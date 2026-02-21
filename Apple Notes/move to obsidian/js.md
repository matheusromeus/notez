string comparisons in js are very slow
strings are passed by reference
nums are passed by value

so to compare references, it goes to the memory, which makes it slow.

the difference in runtime is significant when using large datasets.


- monomorphic objects give more performance than polymorphic and megamorphic.
- refers to shape of objects

functional programming in js is very slow
like map, reduce, filter. it's a tradeoff between readability and performance.

deeper objects means slower code