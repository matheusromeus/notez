session is just the server remembering your info for an extended period of time. 
so need to manage state in the backend.

how are they implemented? cookies. it's just a string that contains information. ( i think they are just normal strings that has to be cross checked with db otherwise it's a bad security measure) 

in http, every request has a header and body. cookie is put in header.


client-sessions
bcryptjs
csurf - what does it do

cookie flags - httponly(dont let js code access cookie), secure(only set cookie over https) , ephemeral (destroy when browser is closed)


password based auth uses cookies or JWT.

how cookie auth works: 
- client sends credentials to the server
- server creates a session id and saves in db and returned via set-cookie
- to be safe from xss and csrf, add headers like httpOnly, secure, samesite
- every subsequent request has the session id attached


SSO - SAML (for enterprises), OpenID (social login)

Authorisation- OAuth