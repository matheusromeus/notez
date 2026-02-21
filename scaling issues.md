
1000 concurrent users are != 1000 concurrent DB connections


	first aim is to reach 100 concurrent requests. 

Postgres max connections = 100


what is app worker?
what does it mean by non-app use?


## 3. Enforce session scope discipline (mandatory)

Rules:

- One DB session = one contiguous DB interaction block
    
- No session across:
    
    - external APIs
        
    - sleeps
        
    - awaits
        
    - long computations
        

Pattern to enforce:

`[ acquire session ] → do DB work → close session → do non-DB work → (optional) reacquire session`

If violated, you will not reach 100.



## 6. Load test correctly

Test **concurrent requests**, not RPS.

Test points:

- 25
    
- 50
    
- **100**
    
- 120 (failure mode)
    

Success at 100 means:

- zero pool timeouts
    
- p95 stable
    
- failures beyond 100 are fast and clean



10 Request per second - a simple ec2 server 2,3 core

100 Request per second - beefier ec2 server, look into the database CPU and Memory

1000 Requests per second - a secondary ec2 server with basic load balancer, then use a pooler to connect to the database. use redis for caching and rate limiting, use your db for transactional data and another database for the analytical workloads (clickhouse etc), telemetry has to be added (datadog or any other apm tool)

(this is literally busier than stripe)
10k requests per second - a managed Load Balancer, horizontal scaling of servers, multiple PgBouncers, one db for write and replicas for read, too many writes will cause issues to the postgres primary (so bigger instance is needed), then al the async stuff should be moved away from the main servers (like queue and other things)

100k requests per second - cache is max priority, queries cannot be computationally expensive, fully event driven architecture, make multi region, no hot paths to the db, splitting databases for each services, vitess, planetscale, infra for health checks, internal tooling, database sharding, 

1 Mil rps - edge computing, 


# we mightve been using sync database connections