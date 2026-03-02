NoSQL often relies on **denormalization**, where you copy data into multiple places to make reads faster.


- your code should handle cascading deletes (application logic)
- garbage collection script