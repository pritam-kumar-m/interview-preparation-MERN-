# Redis Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: caching, data structures, TTLs, pub/sub, streams, queues, rate limiting, sessions, high availability, and production Redis design.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is Redis?

**Answer:** Redis is an in-memory data structure store used for caching, sessions, queues, pub/sub, rate limiting, and fast lookups. In your profile, it fits realtime fleet updates and scalable backend services.

### 2. Why is Redis fast?

**Answer:** Redis keeps data primarily in memory and uses efficient data structures. Network, serialization, and command choice still affect real application performance.

### 3. Is Redis only a key-value store?

**Answer:** Redis is often called a key-value store, but values can be rich data structures such as strings, hashes, lists, sets, sorted sets, and streams.

### 4. What is a Redis key?

**Answer:** A key is the unique name used to access a value. Good key names include purpose and scope, such as user:123:session or tenant:7:orders:summary.

### 5. What are Redis strings?

**Answer:** Strings are the simplest Redis data type and can store text, numbers, JSON strings, or binary data. They are commonly used for simple cache values and counters.

### 6. What are Redis hashes?

**Answer:** Hashes store field-value pairs under one key. They are useful for small objects such as user session details, profile snippets, or cached entity summaries.

### 7. What are Redis lists?

**Answer:** Lists are ordered collections that support pushing and popping from both ends. They can be used for simple queues, though streams or dedicated queue libraries are often better for advanced jobs.

### 8. What are Redis sets?

**Answer:** Sets store unique unordered values. They are useful for membership checks, unique IDs, tags, permissions, or online users.

### 9. What are sorted sets?

**Answer:** Sorted sets store unique members with scores. They are useful for leaderboards, ranking, scheduling, priority queues, and time-ordered indexes.

### 10. What are Redis streams?

**Answer:** Streams are append-only log-like data structures. They are useful for event processing, consumer groups, and reliable async workflows.

### 11. What is TTL in Redis?

**Answer:** TTL is the remaining time before a key expires. TTLs are important for caches, sessions, temporary tokens, rate limits, and cleanup.

### 12. What does EXPIRE do?

**Answer:** EXPIRE sets a timeout on a key so Redis automatically removes it later. It helps prevent stale cache data and uncontrolled memory growth.

### 13. What are SET and GET used for?

**Answer:** SET stores a string value and GET retrieves it. These are common commands for simple cache entries, tokens, and flags.

### 14. What does DEL do?

**Answer:** DEL removes one or more keys. It is used for cache invalidation, logout cleanup, or removing temporary records.

### 15. What does INCR do?

**Answer:** INCR atomically increments a numeric string value. It is useful for counters, rate limits, and sequence-like tracking.

### 16. What is Redis caching?

**Answer:** Caching stores frequently requested data in Redis so the application can avoid repeated database or API calls. Cache design must include expiration and invalidation rules.

### 17. What is cache-aside?

**Answer:** Cache-aside means the application checks Redis first, loads from the database on a miss, then stores the result in cache. It is simple and common in Node.js APIs.

### 18. What is cache invalidation?

**Answer:** Cache invalidation removes or updates stale cached data after the source data changes. It is one of the most important and difficult parts of caching.

### 19. What is Redis Pub/Sub?

**Answer:** Pub/Sub lets publishers send messages to channels and subscribers receive them. It is useful for lightweight realtime notifications, but messages are not stored for later replay.

### 20. What is Redis persistence?

**Answer:** Redis can persist data to disk using snapshots or append-only files. Persistence improves recovery, but Redis is still often used as a fast supporting store rather than the only database.

### 21. What is RDB persistence?

**Answer:** RDB persistence saves point-in-time snapshots of Redis data. It is compact and good for backups, but recent writes can be lost if Redis crashes between snapshots.

### 22. What is AOF persistence?

**Answer:** AOF logs write operations so Redis can replay them after restart. It can provide better durability than snapshots but may use more disk and rewrite work.

### 23. What is redis-cli?

**Answer:** redis-cli is the command-line tool for interacting with Redis. It is useful for debugging keys, checking TTLs, testing commands, and inspecting server info.

### 24. What is a Redis database number?

**Answer:** Redis supports logical databases selected by number in standalone mode. In production, clear key names and separate instances are often preferred for strong separation.

### 25. How does Node.js connect to Redis?

**Answer:** Node.js uses clients such as node-redis or ioredis. Applications should manage connection lifecycle, errors, retries, and command timeouts.

### 26. How can Redis store sessions?

**Answer:** Redis can store session data with TTL so multiple backend instances share login state. This is common when Express or Node.js APIs scale horizontally.

### 27. How can Redis support rate limiting?

**Answer:** Redis atomic counters and expirations can track requests per user, IP, or route. Distributed rate limits work across multiple app instances.

### 28. What is a Redis lock?

**Answer:** A Redis lock is a key used to coordinate exclusive access to a task or resource. Locks need expiration and careful design to avoid stale ownership.

### 29. How can Redis support queues?

**Answer:** Redis lists, sorted sets, or streams can represent queued work. Production Node.js apps often use libraries like BullMQ on top of Redis.

### 30. When should you not use Redis?

**Answer:** Do not use Redis as a replacement for relational truth when strong persistence, complex queries, or long-term records are required. It is best as a fast supporting system.

## Intermediate

### 31. How do you choose the right Redis data type?

**Answer:** Match the data type to access patterns: strings for simple values, hashes for objects, sets for membership, sorted sets for ranking, and streams for events.

### 32. When would you use a hash instead of a JSON string?

**Answer:** Use a hash when you need to update or read individual fields. Use JSON string when the whole object is fetched together and structure is simple.

### 33. How do sorted sets support scheduling?

**Answer:** Use timestamps or priorities as scores, then query due items by score range. This can support delayed jobs, reminders, or retry scheduling.

### 34. How do Redis streams support consumer groups?

**Answer:** Consumer groups let multiple consumers process stream messages cooperatively while tracking pending entries. They are useful for reliable background processing.

### 35. What delivery semantics does Pub/Sub provide?

**Answer:** Redis Pub/Sub is lightweight and does not persist messages for disconnected subscribers. If consumers must catch up later, streams are usually a better choice.

### 36. What are MULTI and EXEC?

**Answer:** MULTI starts a transaction and EXEC runs queued commands atomically. Redis transactions serialize command execution but do not provide rollback like SQL databases.

### 37. What are Lua scripts used for in Redis?

**Answer:** Lua scripts execute multiple Redis operations atomically on the server. They are useful for complex rate limits, locks, counters, and conditional updates.

### 38. What is the difference between pipelining and transactions?

**Answer:** Pipelining sends multiple commands without waiting for each response, improving network efficiency. Transactions guarantee queued commands execute together atomically.

### 39. How should Redis connections be managed in Node.js?

**Answer:** Create shared clients, handle reconnects and errors, avoid creating a new connection per request, and close connections during graceful shutdown.

### 40. What is TTL jitter?

**Answer:** TTL jitter adds randomness to expirations so many keys do not expire at the same time. It helps prevent cache stampedes.

### 41. What is a cache stampede?

**Answer:** A cache stampede happens when many requests miss the cache together and overload the database. Use locks, stale data, request coalescing, or TTL jitter to reduce it.

### 42. What is stale-while-revalidate?

**Answer:** Serve slightly stale cached data quickly while refreshing it in the background. It improves latency when perfect freshness is not required.

### 43. How do distributed locks work in Redis?

**Answer:** A process sets a lock key with a unique value and expiration, then releases it only if it still owns the value. Correctness depends on timeouts and failure handling.

### 44. What are Redlock trade-offs?

**Answer:** Redlock is a distributed locking algorithm for Redis deployments, but it requires careful assumptions about clocks, network, and Redis topology. Critical correctness may need database locks instead.

### 45. How would you implement a fixed-window rate limit?

**Answer:** Increment a counter key and set an expiration for the window. It is simple but can allow bursts at window boundaries.

### 46. How would you implement a sliding-window rate limit?

**Answer:** Track request timestamps with sorted sets or approximate counters. It is smoother than fixed windows but costs more Redis operations.

### 47. How can Redis store token deny-lists?

**Answer:** Store revoked token IDs with TTL equal to remaining token lifetime. This allows logout or forced revocation while avoiding permanent memory growth.

### 48. How does Redis help idempotency?

**Answer:** Store idempotency keys with operation status and expiration. This helps prevent duplicate payments, orders, or webhook processing.

### 49. How do Redis geospatial commands help applications?

**Answer:** Geospatial indexes can store coordinates and query nearby members. Fleet, delivery, or location-based features can use this pattern.

### 50. What are bitmaps in Redis?

**Answer:** Bitmaps use string bits to store compact boolean information. They can track daily activity, feature flags, or large yes/no datasets efficiently.

### 51. What is HyperLogLog?

**Answer:** HyperLogLog estimates unique counts with low memory. It is useful for analytics like approximate unique visitors where exact counts are not required.

### 52. What is a big key?

**Answer:** A big key stores too much data under one key, causing slow operations, memory pressure, and blocking. Large hashes, lists, sets, or strings should be monitored.

### 53. What is a hot key?

**Answer:** A hot key receives a disproportionate amount of traffic. It can overload one Redis node or shard and needs caching, sharding, replication, or key redesign.

### 54. What are eviction policies?

**Answer:** Eviction policies decide what Redis removes when max memory is reached, such as least recently used keys or keys with TTL. Choose based on whether Redis stores cache or important state.

### 55. How do you serialize data for Redis?

**Answer:** Common choices include JSON strings, msgpack, or simple primitives. Keep serialization consistent and avoid storing sensitive data without protection.

### 56. What is key namespacing?

**Answer:** Namespacing uses prefixes such as app:env:tenant:resource:id to organize keys. It prevents collisions and makes debugging easier.

### 57. How do you invalidate cache after database writes?

**Answer:** Delete or update affected keys after successful writes. For complex dependencies, publish invalidation events or use predictable key design.

### 58. How do Redis replicas work?

**Answer:** Replicas copy data from a primary Redis instance and can support read scaling or failover. Applications must understand replication lag.

### 59. What is Redis Sentinel?

**Answer:** Sentinel monitors Redis instances and coordinates failover for high availability in non-cluster deployments. Clients must support Sentinel discovery.

### 60. What is Redis Cluster?

**Answer:** Redis Cluster shards data across nodes using hash slots. It supports horizontal scaling but requires cluster-aware clients and careful multi-key command design.

### 61. What are hash tags in Redis Cluster keys?

**Answer:** Hash tags force part of a key to determine the cluster slot. They allow related keys to live in the same slot for multi-key operations.

### 62. How do you monitor Redis?

**Answer:** Use INFO, SLOWLOG, latency tools, memory stats, keyspace metrics, and external monitoring. Track memory, evictions, command latency, and connected clients.

### 63. How do ACLs improve Redis security?

**Answer:** ACLs define users and command/key permissions. They support least privilege instead of one all-powerful password for every service.

### 64. Why use TLS with Redis?

**Answer:** TLS encrypts traffic between clients and Redis. It is important when Redis traffic crosses networks where interception is possible.

### 65. What is BullMQ?

**Answer:** BullMQ is a Node.js queue library backed by Redis. It supports delayed jobs, retries, priorities, repeatable jobs, and worker processing.

### 66. How do Redis streams differ from queues?

**Answer:** Streams store append-only entries and support replay and consumer groups. Simple queues remove items as they are consumed, while streams retain history until trimmed.

### 67. How do you trim Redis streams?

**Answer:** Use trimming options to limit stream length or approximate size. Trimming prevents unbounded memory growth in event-heavy systems.

### 68. What is backpressure in Redis-backed systems?

**Answer:** Backpressure means producers create work faster than consumers process it. Monitor queue length or stream pending entries and slow producers when needed.

### 69. How can Redis support WebSocket scaling?

**Answer:** Use Redis Pub/Sub or streams so multiple app instances can broadcast messages consistently. This prevents one instance from knowing only its own socket connections.

### 70. How do you decide Redis TTL values?

**Answer:** Base TTL on data freshness, database load, user expectations, and risk of stale data. Inventory, payment, and compliance data need shorter or more explicit invalidation.

## Advanced

### 71. How would you design a Redis caching layer for Node.js APIs?

**Answer:** Identify expensive read paths, define cache keys, set TTLs, handle misses, invalidate after writes, and monitor hit rate. Cache only data where staleness rules are acceptable.

### 72. How would you design Redis high availability?

**Answer:** Use managed Redis, Sentinel, or Cluster depending on scale; configure client reconnects, persistence, monitoring, and failover tests. High availability is not just turning on replicas.

### 73. How would you use Redis Cluster safely?

**Answer:** Design keys for hash slot behavior, avoid unsupported multi-key operations across slots, use cluster-aware clients, and test failover. Cluster changes application assumptions.

### 74. How would you prevent thundering herd problems?

**Answer:** Use TTL jitter, request coalescing, locks around cache regeneration, stale-while-revalidate, and background refresh. This protects the database during cache expiry.

### 75. How would you build distributed rate limiting with Redis?

**Answer:** Use atomic counters, sorted sets, or Lua scripts; key by user/IP/tenant/route; set expirations; and return clear retry information to clients.

### 76. How would you design Redis locks for scheduled jobs?

**Answer:** Use unique lock values, expirations, safe release scripts, and job idempotency. Locks reduce duplicates but should not be the only correctness mechanism for critical data.

### 77. How would you design a reliable Redis-backed job queue?

**Answer:** Use a queue library or streams, retries, dead-letter handling, idempotent workers, concurrency limits, and monitoring for stuck jobs. Background work needs operational visibility.

### 78. How would you use Redis Streams for event processing?

**Answer:** Append events, process with consumer groups, track pending entries, retry failed messages, trim old data, and make consumers idempotent. Streams are stronger than Pub/Sub for durable workflows.

### 79. How would Redis support realtime fleet dashboards?

**Answer:** Use Redis Pub/Sub or streams to fan out updates from backend services to WebSocket servers. Persist important log events in PostgreSQL before broadcasting them.

### 80. How would you design Redis session storage at scale?

**Answer:** Store compact session data with TTL, secure cookie identifiers, shared Redis access, and logout cleanup. Monitor memory and avoid storing unnecessary sensitive data.

### 81. How do you design tenant-safe Redis keys?

**Answer:** Include tenant ID and environment in key names, enforce consistent builders, and avoid broad key scans in production. Tenant-aware keys prevent accidental data mixing.

### 82. How would you keep Redis cache consistent with PostgreSQL?

**Answer:** Write to PostgreSQL as the source of truth, then invalidate or update Redis after commit. For complex flows, publish events or use an outbox pattern.

### 83. When is stale cache acceptable?

**Answer:** Stale cache is acceptable for read-heavy, low-risk data like product descriptions or summary widgets. It is risky for payments, inventory, compliance, and permissions.

### 84. How would you choose Redis persistence settings?

**Answer:** Use RDB for compact snapshots, AOF for better write durability, or both depending on recovery needs. Cache-only Redis may need less durability than queue/session Redis.

### 85. How would you investigate Redis memory growth?

**Answer:** Check key count, big keys, TTL coverage, data type sizes, fragmentation, and eviction metrics. Growth often comes from missing expirations or unbounded streams/lists.

### 86. How would you handle memory fragmentation?

**Answer:** Monitor fragmentation ratio, allocator behavior, big keys, and workload patterns. Managed Redis or controlled restarts may help, but root-cause key design still matters.

### 87. How would you mitigate big keys?

**Answer:** Split data into smaller keys, paginate structures, trim streams, limit list/set sizes, and avoid commands that return huge payloads. Big keys can block Redis operations.

### 88. How would you mitigate hot keys?

**Answer:** Replicate reads, shard data, cache at another layer, split counters, or redesign access patterns. Hot keys can become the bottleneck in otherwise scaled systems.

### 89. When would you use Lua instead of multiple commands?

**Answer:** Use Lua when multiple operations must be atomic and conditional, such as compare-and-delete locks or complex rate limits. Keep scripts short and predictable.

### 90. How do Redis transactions differ from PostgreSQL transactions?

**Answer:** Redis transactions execute commands atomically but do not support rollback like PostgreSQL. PostgreSQL is better for relational consistency; Redis is better for fast coordination and state.

### 91. How would you use Redis geospatial data in fleet software?

**Answer:** Store active vehicle or driver coordinates with geospatial indexes, query nearby assets, and expire stale positions. Persist long-term trip history in a durable database.

### 92. How would you observe Redis in production?

**Answer:** Track latency, memory, evictions, keyspace hits/misses, slow commands, connected clients, blocked clients, replication lag, and queue depth. Alerts should match business risk.

### 93. How would failover affect Redis-backed applications?

**Answer:** Clients may see brief errors or reconnects, replicas may lag, and in-flight pub/sub messages can be lost. Applications should handle retries and idempotency.

### 94. How would you back up Redis data?

**Answer:** Use RDB/AOF files or managed backups depending on durability needs. For cache-only data, backup may be less important than rebuild speed.

### 95. How would you secure Redis in production?

**Answer:** Use private networking, authentication, ACLs, TLS where needed, least-privilege users, command restrictions, and secret rotation. Never expose Redis publicly.

### 96. How would you choose between Redis Pub/Sub and Streams?

**Answer:** Use Pub/Sub for transient live notifications where missed messages are acceptable. Use Streams when consumers need replay, acknowledgement, and pending-message recovery.

### 97. How would you design Redis for idempotent webhooks?

**Answer:** Store event IDs with status and TTL or permanent retention as needed, use atomic set-if-not-exists, and let duplicate events return safely. This protects payment and ecommerce workflows.

### 98. How would Redis fit with PostgreSQL in your resume projects?

**Answer:** PostgreSQL remains the durable source of truth, while Redis supports cache, rate limiting, sessions, realtime fan-out, and background queues for ELD, ecommerce, and AI voice systems.

### 99. How would you review Redis usage as a senior developer?

**Answer:** Check key naming, TTLs, memory growth, data type choice, atomicity, failure behavior, invalidation, monitoring, and security. Redis mistakes often show up under scale.

### 100. How would you explain Redis experience from this resume?

**Answer:** Discuss Redis as part of the ELD stack for realtime support, caching, rate limits, queues, or WebSocket coordination, and explain how it improves performance without replacing durable databases.


## Reference Docs

- [Redis Data Types](https://redis.io/docs/latest/develop/data-types/)
- [Redis Pub/Sub](https://redis.io/docs/latest/develop/pubsub/)
- [Redis Streams](https://redis.io/docs/latest/develop/data-types/streams/)
