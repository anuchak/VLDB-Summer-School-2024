# Day 2 Talk - Cloud Data Warehouses & Workload-Driven Indexing

- Different from "data-driven" indexing, more workload driven (?)
- Work related to stuff done in AWS
- dataset released: aws redset (github)
- sorting vs indexing
- lot more updates on workload (unexpected for warehouse, OLAP like systems)
- query repetitiveness: for 50% clusters, 75% of queries are repeated (in 1 month duration)
- query repetitiveness: for 75% clusters, workload is 50% select + update select
- updates make it difficult to implement caches that store result
- Multi-dimensional data layout (hilbert curve, z-order)
- create a new mddl column and append on the table 
- the value for this will be evaluated based on how many conditions it satisfied, then based on subsequent 
  query with matching filter predicates, check which mdl rows match
- after that go into the rows and check manually (there can be false positives, when going into the physical data)
- performs better than z-order because space filling curves don't handle well filter predicates on string columns

Predicate caching
-----------------

- have a cache for filter predicates the row ranges that match
- transform scan into scan of specific rows that need to be looked up based on predicates of queries
- not as well as sorting, but still works well due to redshift workloads

In conclusion, workloads for the cloud warehouse are highly repetitive and doing simple caching with filter predicates
is working well for their workloads. There is not much complicated theory involved, just that it is specifically 
aimed at improving their execution.
