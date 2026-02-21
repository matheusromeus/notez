
A **connection pool** is a reusable set of live database connections.

Why it exists:
- Creating a DB connection is expensive (TCP + auth + handshake).
- Databases have a maximum connection limit.

Without pooling:
- Every request → new connection → close → heavy overhead.

With pooling:
- Request borrows connection
- Uses it
- Returns it to pool


`pool_size=20` - Number of **persistent connections** kept open.
`max_overflow=30` - Extra temporary connections beyond `pool_size`. Only created if all 20 are busy.
`pool_timeout` - 51st request → waits until a connection is free. If wait exceeds `pool_timeout`, error is raised.

so total connections possible = 50 per process/worker/CPU

Connection pool is **per process**, not global.

### you are supposed to be using async db
- 4 workers
- Each worker handles 1 blocking request
- You still process 4 requests in parallel

If this is your case,
- You need hundreds/thousands of concurrent connections
- Many requests spend most of their time waiting on I/O
then use async.

Sync Is Simpler
Async adds complexity:

- `async def` everywhere
- `await` everywhere
- Can’t call sync functions directly
- Must ensure libraries are async-compatible
- Harder debugging and stack traces
- Subtle deadlocks or context issues

With sync:
- Normal functions
- Linear control flow
- Easier mental model
- Easier integration with existing libraries


If your bottleneck is:
- CPU-heavy work
- Complex queries
- Data processing

Async gives zero benefit.

There are two concurrency models:

### Model A: Sync + Multiple Workers

- Each worker blocks
- OS schedules them across CPU cores
- Simple
- Predictable
- Uses more memory

### Model B: Async + Few Workers

- One worker handles many concurrent requests
- Less memory
- Better for high concurrency I/O workloads
- More complex

Both are valid.



Async should be used anywhere your application **waits on external I/O**.
Not for CPU work. 

1. Database calls
2. External HTTP API calls
3. WebSockets
4. File I/O
5. Message Brokers / Queues
6. Background tasks that wait on I/O

For CPU heavy work, async does not help. Use
- thread pool
- process pool
- task queue


## NoSQL vs SQL

the problems that i had encountered, like empty data and no relationship constraints enforced was an application level problem. not an inherent problem of nosql vs sql. we have to implement the data integrity part and schemas in the application.

even what values should not be added, guardrails, having a single source of truth etc.