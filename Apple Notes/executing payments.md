so we have a payment service.

payment system has to be idempotent

the call that goes to the payment service from the client, we add a header called idempotency key. and the payment system should be idempotent for that uuid. 

if the client sends it again, send with the same id, it should send back 429. too many requests. 



1. client talks to server just to generate an idempotent key (can this be a uuid from the client?)
2. client passes the key to server along with the payload as a req header or query param
3. server checks the id and validates whether the operation was done before