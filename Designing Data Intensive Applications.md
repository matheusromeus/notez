
We call an application data intensive if data is its primary challenge, the quantity of data, the complexity of data or the speed at which it is changing as opposed to compute. Intensive where CPU cycles are the bottleneck

Reliability, Scalability, Maintainability

Remember the result of an expensive operation, to speed up reads (caches)
Allow users to search data by keyword or filter it in various ways (search indexes)
Send a message to another process, to be handled asynchronously (stream processing)
Periodically crunch a large amount of accumulated data (batch processing)


by deliberately inducing faults, you ensure that the fault-tolerance machinery is continually exercised and tested (eg: Netflix Chaos Monkey)

