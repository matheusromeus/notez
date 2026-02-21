change seat api. is the seat locked?

- all db models should be declared in one single common place
- centralized config, for envs, pydantic settings
- common db actions can be abstracted
- can i write tests?
- db models need indexes
- custom exception hierarchy
- async or sync



# packages/core/exceptions.py
from fastapi import HTTPException, status

class AppException(Exception):
    """Base exception for all application errors"""
    status_code: int = status.HTTP_500_INTERNAL_SERVER_ERROR
    
    def __init__(self, message: str, details: dict = None):
        self.message = message
        self.details = details or {}
        super().__init__(message)
    
    def to_http(self) -> HTTPException:
        return HTTPException(
            status_code=self.status_code,
            detail={"message": self.message, **self.details}
        )

class NotFoundError(AppException):
    status_code = status.HTTP_404_NOT_FOUND
    
    def __init__(self, resource: str, id: any):
        super().__init__(f"{resource} with id {id} not found")

class BusinessError(AppException):
    status_code = status.HTTP_422_UNPROCESSABLE_ENTITY

class ValidationError(AppException):
    status_code = status.HTTP_400_BAD_REQUEST

class AuthenticationError(AppException):
    status_code = status.HTTP_401_UNAUTHORIZED

class AuthorizationError(AppException):
    status_code = status.HTTP_403_FORBIDDEN


# Global exception handler
@app.exception_handler(AppException)
async def app_exception_handler(request: Request, exc: AppException):
    return JSONResponse(
        status_code=exc.status_code,
        content={"error": exc.message, "details": exc.details}
    )


















# packages/clients/service_client.py
import httpx
from tenacity import retry, stop_after_attempt, wait_exponential
from packages.config import get_settings

class ServiceClient:
    def __init__(self, base_url: str, timeout: float = 30.0):
        self.base_url = base_url
        self.timeout = timeout
    
    @retry(stop=stop_after_attempt(3), wait=wait_exponential(multiplier=1, min=1, max=10))
    async def request(
        self, 
        method: str, 
        path: str, 
        data: dict = None,
        headers: dict = None,
        params: dict = None
    ) -> dict:
        async with httpx.AsyncClient(timeout=self.timeout) as client:
            response = await client.request(
                method,
                f"{self.base_url}{path}",
                json=data,
                headers=headers,
                params=params
            )
            response.raise_for_status()
            return response.json()


# Usage
class AuthClient(ServiceClient):
    def __init__(self):
        settings = get_settings()
        super().__init__(settings.services.auth_url)
    
    async def verify_token(self, token: str) -> dict:
        return await self.request(
            "GET",
            "/verify",
            headers={"Authorization": f"Bearer {token}"}
        )
    
    async def get_user(self, user_id: int) -> dict:
        return await self.request("GET", f"/users/{user_id}")