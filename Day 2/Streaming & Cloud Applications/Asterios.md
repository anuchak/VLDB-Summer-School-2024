# Day 2 Talk - Streaming Processing in the Cloud

- stateful stream processing
- streaming is doing dataflow programming
- expressing logic with operators and data flows through it
- good because once expressed, you can do data parallelism, pipeline parallelism
- persistence important for stream processing
- exactly once processing
- runs 2 phase commit in the background, similar to providing ACID transactions
- more lose guarantees: at least once, at most once (looser txn guarantees)

