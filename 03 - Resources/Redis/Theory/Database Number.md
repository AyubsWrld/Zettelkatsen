Redis supports **multiple numbered databases** per server instance, identified by integers starting from `0`.

#### Benefits
___
- **Separation**: each database is separate. Keys which exist in one database are separate from keys which exist in another database. 
- **Lightweight**: Switching databases doesn't create new memory allocations.
- **Non-namespaced**: There’s no naming prefix; databases are logically distinct.

#### Use Cases
___
- Temporary separation in development/testing (e.g., DB 1 for tests, DB 0 for local app).
- Simple multi-tenant environments (not recommended for strong isolation).
- Ephemeral task queues or counters with minimal overlap.

#### Some considerations
___
- All databases share the same memory space and are affected by commands like `FLUSHALL` ( vs. `FLUSHDB` which only effects one DB ).
___
Tags: #redis 