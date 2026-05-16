# PostgreSQL Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: relational modeling, SQL, indexes, transactions, query optimization, migrations, security, and production database architecture.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is PostgreSQL?

**Answer:** PostgreSQL is an open-source relational database system known for reliability, SQL support, transactions, indexing, and extensibility. It fits your backend work with fleet, ecommerce, AI voice, and SaaS platforms.

### 2. What is a relational database?

**Answer:** A relational database stores data in tables with rows and columns, and relationships are defined through keys. This model is strong for structured business data such as users, orders, drivers, vehicles, and payments.

### 3. What is a table?

**Answer:** A table stores records of one entity type, such as users, products, vehicles, or logs. Each row is one record and each column stores one attribute.

### 4. What is a row in PostgreSQL?

**Answer:** A row is a single record in a table. For example, one driver, one order, or one payment can be represented as a row.

### 5. What is a column?

**Answer:** A column defines one field of a table, such as email, status, created_at, or vehicle_id. Each column has a data type and may have constraints.

### 6. What is a primary key?

**Answer:** A primary key uniquely identifies each row in a table. It should be stable and not null, often using UUIDs or generated numeric IDs.

### 7. What is a foreign key?

**Answer:** A foreign key links one table to another by referencing a primary key. It protects relationships such as orders to users, vehicles to carriers, or logs to drivers.

### 8. What are constraints?

**Answer:** Constraints enforce rules at the database level, such as NOT NULL, UNIQUE, CHECK, primary keys, and foreign keys. They protect data even when application code has bugs.

### 9. What is SQL?

**Answer:** SQL is the language used to query and manage relational databases. In PostgreSQL, SQL is used for reading, writing, joining, aggregating, and maintaining data.

### 10. What does SELECT do?

**Answer:** SELECT reads data from one or more tables. It can include filters, sorting, joins, grouping, and calculated columns.

### 11. What does WHERE do?

**Answer:** WHERE filters rows based on conditions. It is used to return only relevant data, such as active drivers, paid orders, or logs within a date range.

### 12. What does ORDER BY do?

**Answer:** ORDER BY sorts query results by one or more columns. It is commonly used for newest records, alphabetical lists, and dashboard ordering.

### 13. What does GROUP BY do?

**Answer:** GROUP BY combines rows into groups so aggregate functions can calculate totals, counts, averages, or summaries. It is useful for analytics dashboards and reports.

### 14. What are aggregate functions?

**Answer:** Aggregate functions like COUNT, SUM, AVG, MIN, and MAX compute values across multiple rows. They are used for totals, summaries, and reporting.

### 15. What is a JOIN?

**Answer:** A JOIN combines rows from multiple tables based on related columns. Joins are essential for reading normalized data such as users with orders or drivers with vehicles.

### 16. What does INSERT do?

**Answer:** INSERT adds new rows to a table. Applications use it to create users, products, logs, payments, and other records.

### 17. What does UPDATE do?

**Answer:** UPDATE modifies existing rows. It should use safe WHERE conditions to avoid changing more records than intended.

### 18. What does DELETE do?

**Answer:** DELETE removes rows from a table. Many production systems use soft deletes for business records to preserve history and auditability.

### 19. What are PostgreSQL data types?

**Answer:** Data types define what kind of values a column can store, such as integer, text, boolean, timestamp, uuid, numeric, jsonb, and arrays. Correct types improve validation and performance.

### 20. What is NULL?

**Answer:** NULL means the value is unknown or absent. It is different from empty string or zero, so queries and constraints must handle it intentionally.

### 21. What is an index?

**Answer:** An index helps PostgreSQL find rows faster without scanning the whole table. Indexes improve reads but add overhead to writes, so they should match real query patterns.

### 22. What is a transaction?

**Answer:** A transaction groups multiple operations so they succeed or fail together. It is important for payments, order creation, appointment booking, and compliance records.

### 23. What does ACID mean?

**Answer:** ACID means Atomicity, Consistency, Isolation, and Durability. These properties make relational databases reliable for critical business operations.

### 24. What is a schema in PostgreSQL?

**Answer:** A schema is a namespace that organizes database objects such as tables, views, and functions. It can help separate modules or tenants in some designs.

### 25. What is a view?

**Answer:** A view is a saved query that can be selected like a table. Views simplify repeated joins or report queries without duplicating data.

### 26. What is a sequence or identity column?

**Answer:** A sequence generates numeric values, often for IDs. Modern PostgreSQL can use identity columns to generate values automatically.

### 27. What is psql?

**Answer:** psql is the PostgreSQL command-line client. It helps developers run queries, inspect schemas, and debug database behavior.

### 28. What is a database connection string?

**Answer:** A connection string contains host, port, database, user, password, and options. Node.js services and ORMs use it to connect to PostgreSQL.

### 29. What is normalization?

**Answer:** Normalization organizes data to reduce duplication and maintain consistency. It is useful for structured domains like users, products, vehicles, orders, and logs.

### 30. What is a unique constraint?

**Answer:** A unique constraint ensures no two rows have the same value for one or more columns. Common examples include email, external provider ID, or payment event ID.

## Intermediate

### 31. What is the difference between INNER JOIN and LEFT JOIN?

**Answer:** INNER JOIN returns only matching rows from both tables, while LEFT JOIN returns all rows from the left table and matching rows from the right. Use LEFT JOIN when related data may be missing.

### 32. What is a many-to-many relationship?

**Answer:** A many-to-many relationship uses a join table between two entities. Examples include users and roles, products and collections, or drivers and assigned groups.

### 33. What is a CTE?

**Answer:** A Common Table Expression uses WITH to name a temporary result inside a query. CTEs can make complex reporting and multi-step queries easier to read.

### 34. What is a subquery?

**Answer:** A subquery is a query inside another query. It can filter, calculate, or provide derived data, but joins or CTEs may be clearer for complex cases.

### 35. What are window functions?

**Answer:** Window functions calculate values across related rows without collapsing rows like GROUP BY. They are useful for ranking, running totals, and per-group analytics.

### 36. What is a B-tree index?

**Answer:** B-tree is the default PostgreSQL index type and works well for equality, range queries, sorting, and many common filters. Most application indexes start here.

### 37. What is a composite index?

**Answer:** A composite index includes multiple columns. It is useful when queries often filter or sort by the same column combination, such as tenant_id plus created_at.

### 38. What is a partial index?

**Answer:** A partial index includes only rows matching a condition. It is useful for common filtered queries, such as active records or unpaid orders.

### 39. What is an expression index?

**Answer:** An expression index indexes a computed value, such as lower(email). It helps queries that repeatedly filter on the same expression.

### 40. What is EXPLAIN used for?

**Answer:** EXPLAIN shows how PostgreSQL plans to execute a query. EXPLAIN ANALYZE actually runs the query and reports real timing, which helps find bottlenecks.

### 41. What is a sequential scan?

**Answer:** A sequential scan reads rows from a table directly. It is not always bad, but for large tables and selective filters, a good index may be needed.

### 42. What is MVCC?

**Answer:** MVCC, or Multi-Version Concurrency Control, lets PostgreSQL provide consistent reads while writes happen concurrently. It is central to PostgreSQL transaction behavior.

### 43. What are transaction isolation levels?

**Answer:** Isolation levels define how transactions see changes from other transactions. PostgreSQL commonly uses Read Committed by default, with stronger options like Repeatable Read and Serializable.

### 44. What is a lock in PostgreSQL?

**Answer:** A lock controls concurrent access to data or database objects. Locks protect consistency, but long-running transactions can block other work.

### 45. What is a deadlock?

**Answer:** A deadlock happens when transactions wait on each other in a cycle. PostgreSQL detects deadlocks and aborts one transaction, so applications should retry safe operations.

### 46. Why is connection pooling important?

**Answer:** Opening database connections is expensive, and PostgreSQL has connection limits. Pooling reuses connections and keeps backend services stable under load.

### 47. How do migrations work?

**Answer:** Migrations apply schema changes over time, such as creating tables, adding columns, or changing indexes. Good migrations are versioned, reviewed, and safe to run in production.

### 48. How does Prisma work with PostgreSQL?

**Answer:** Prisma maps application models to database tables and generates a typed client. It improves productivity, but developers must still understand indexes, joins, and query plans.

### 49. What are cascading foreign keys?

**Answer:** Cascading actions automatically update or delete related rows when a referenced row changes. Use them carefully because accidental cascades can remove important data.

### 50. What is JSONB?

**Answer:** JSONB stores JSON data in a binary format that can be queried and indexed. It is useful for flexible metadata, but core relational data should usually stay in typed columns.

### 51. When would you use arrays in PostgreSQL?

**Answer:** Arrays can store lists of values in one column, but they should not replace proper relational modeling when values need filtering, joining, or independent relationships.

### 52. What is full-text search?

**Answer:** Full-text search indexes and queries natural language text. It can support product search, content search, and SEO tools when basic LIKE queries are not enough.

### 53. How does offset pagination work?

**Answer:** Offset pagination uses LIMIT and OFFSET to skip rows. It is simple, but can become slow or inconsistent for large changing datasets.

### 54. How does cursor pagination work?

**Answer:** Cursor pagination uses a stable position, such as created_at and id, to fetch the next page. It performs better for large logs, events, and feeds.

### 55. What is UPSERT in PostgreSQL?

**Answer:** UPSERT uses INSERT ... ON CONFLICT to insert a row or update an existing one. It is useful for syncing external IDs, webhook events, and idempotent writes.

### 56. Why enforce rules with database constraints?

**Answer:** Database constraints protect data regardless of which service or script writes to the database. Application validation improves UX, but constraints provide final safety.

### 57. What is a materialized view?

**Answer:** A materialized view stores the result of a query physically and can be refreshed. It helps expensive reports but requires a refresh strategy.

### 58. What are triggers?

**Answer:** Triggers run database functions automatically on events like insert, update, or delete. They can enforce audit logic, but overuse can hide business behavior.

### 59. What is table partitioning?

**Answer:** Partitioning splits a large table into smaller physical pieces, often by date or tenant. It can improve management and performance for large log or event tables.

### 60. What are VACUUM and ANALYZE?

**Answer:** VACUUM cleans up old row versions, and ANALYZE updates planner statistics. They help PostgreSQL maintain performance over time.

### 61. How should Node.js use PostgreSQL transactions?

**Answer:** Start a transaction for related operations, pass the transaction client through service logic, commit on success, and rollback on failure. Keep transactions short.

### 62. What is the N+1 query problem?

**Answer:** N+1 happens when code runs one query for a list and then one more query per row. Use joins, batching, or eager loading to reduce database round trips.

### 63. How do you index dashboard queries?

**Answer:** Look at filters, sort fields, joins, and date ranges used by dashboards. Index for real query patterns such as tenant_id, status, created_at, or foreign keys.

### 64. How should timestamps be stored?

**Answer:** Store canonical timestamps consistently, often in UTC, and keep timezone meaning explicit. ELD/HOS and reporting systems need careful time handling.

### 65. When would you use enum types?

**Answer:** Enums are useful for stable small sets like status values, but they are harder to change than lookup tables. Choose based on how often values evolve.

### 66. What is backup and restore?

**Answer:** Backups copy database data so it can be restored after failure or human error. A backup is only useful if restore is tested.

### 67. How do PostgreSQL roles work?

**Answer:** Roles define login and permissions. Least-privilege roles help separate app access, migrations, reporting, and administrative operations.

### 68. What is row-level security?

**Answer:** Row-level security can restrict which rows a role can access based on policies. It is powerful for multi-tenant systems but must be tested carefully.

### 69. How do prepared statements help?

**Answer:** Prepared statements separate SQL structure from values and can improve safety and performance. They are important for preventing SQL injection when used correctly.

### 70. How do you prevent SQL injection?

**Answer:** Use parameterized queries or trusted ORM query builders, validate inputs, and never concatenate raw user input into SQL strings. This is a core backend security requirement.

## Advanced

### 71. How would you design PostgreSQL tables for an ELD fleet system?

**Answer:** Model carriers, drivers, vehicles, assignments, HOS logs, violations, locations, and audit records with clear relationships. Use constraints and indexes around tenant, driver, vehicle, and timestamp fields.

### 72. How would you optimize a slow PostgreSQL query?

**Answer:** Use EXPLAIN ANALYZE, check indexes, row estimates, joins, filters, sorts, and returned columns. Then adjust indexes, query shape, statistics, or schema based on evidence.

### 73. How would you create an index strategy?

**Answer:** Start from production query patterns, not guesses. Index common filters, joins, uniqueness rules, and sorting needs while watching write overhead and index bloat.

### 74. How would you design multi-tenant data in PostgreSQL?

**Answer:** Use tenant_id on tenant-owned tables, enforce it in queries, index tenant-specific access patterns, and consider RLS for stronger isolation. Cache keys must include tenant context too.

### 75. How would you handle high-write log tables?

**Answer:** Use append-friendly schema, partition by time when needed, avoid excessive indexes, batch inserts carefully, and archive old data. HOS logs and audit trails can grow quickly.

### 76. When would you use time-based partitioning?

**Answer:** Use it when large tables are naturally queried or retained by time, such as logs, events, reports, or telemetry. It can make retention and query pruning easier.

### 77. How do isolation levels affect application design?

**Answer:** Stronger isolation reduces anomalies but can increase retries or overhead. Senior developers choose the level based on business correctness, not just default settings.

### 78. How would you debug deadlocks?

**Answer:** Inspect transaction order, lock waits, queries, and indexes. Fix by accessing rows in a consistent order, keeping transactions short, and retrying safely when necessary.

### 79. How would you tune connection pooling?

**Answer:** Balance app instances, pool size, database max connections, query latency, and traffic. Too many connections can overload PostgreSQL and make performance worse.

### 80. How do you read EXPLAIN ANALYZE like a senior developer?

**Answer:** Compare estimated vs actual rows, find expensive nodes, check loops, sort methods, join type, index usage, and total timing. Focus on the biggest cost first.

### 81. How would you use materialized views for dashboards?

**Answer:** Precompute expensive summaries, refresh on a schedule or after data changes, and show refresh time if data can be stale. They are useful for analytics, not transactional truth.

### 82. What are JSONB trade-offs?

**Answer:** JSONB gives flexibility and indexing options for semi-structured data, but weakens relational constraints and can hide schema drift. Use it for metadata, not core relational fields.

### 83. How would you run zero-downtime migrations?

**Answer:** Use backward-compatible changes, add nullable columns first, backfill in batches, deploy code that writes both if needed, then enforce constraints later. Avoid long locks on hot tables.

### 84. How would you implement audit history?

**Answer:** Use audit tables, immutable event records, triggers, or application-level writes depending on needs. Compliance systems should record who changed what and when.

### 85. What is the outbox pattern?

**Answer:** The outbox pattern stores events in the same database transaction as business data, then publishes them asynchronously. It prevents losing events after a successful write.

### 86. How does replication help PostgreSQL systems?

**Answer:** Replication copies data to standby servers for read scaling or failover. Applications must understand replication lag when reading from replicas.

### 87. What should a backup strategy include?

**Answer:** Include scheduled backups, point-in-time recovery if needed, retention policies, encryption, restore drills, and monitoring. Untested backups are a business risk.

### 88. How would you use row-level security safely?

**Answer:** Define policies by tenant or ownership, test bypass cases, use least-privilege roles, and monitor query behavior. RLS can improve isolation but adds complexity.

### 89. How would you implement search in PostgreSQL?

**Answer:** For simple search, use indexes and ILIKE carefully; for richer search, use full-text search with ranking. Ecommerce product search may eventually need a dedicated search engine.

### 90. How do locks affect production APIs?

**Answer:** Long transactions, missing indexes, or table-level changes can block requests. Monitor lock waits and keep migrations and transactions designed for concurrency.

### 91. How do you handle serialization failures?

**Answer:** For Serializable transactions, applications must retry when PostgreSQL aborts a transaction due to concurrency. Retry logic should be idempotent and bounded.

### 92. How do database constraints support application reliability?

**Answer:** Constraints catch invalid states even if multiple services, scripts, or jobs write data. They are a final line of defense for money, ownership, and compliance records.

### 93. How would you design idempotency in PostgreSQL?

**Answer:** Store idempotency keys or external event IDs with unique constraints, then return the existing result for duplicates. This protects payments and webhook processing.

### 94. How would PostgreSQL support a queue or job pattern?

**Answer:** Use a dedicated jobs table with status, attempts, scheduled time, and row locking, or use a real queue when throughput grows. Keep workers idempotent.

### 95. How would you store geolocation for fleet features?

**Answer:** Use latitude/longitude columns or geospatial extensions if advanced queries are needed. Indexing and precision depend on use cases like jurisdiction, proximity, or trip history.

### 96. What PostgreSQL metrics matter in production?

**Answer:** Track slow queries, locks, connections, cache hit ratio, replication lag, table/index bloat, transaction age, and disk usage. Metrics reveal issues before outages.

### 97. When would you use PgBouncer?

**Answer:** PgBouncer pools PostgreSQL connections and is helpful when many app instances or serverless functions could exceed connection limits. It requires transaction behavior awareness.

### 98. How would you design data retention?

**Answer:** Define legal/business retention periods, archive old data, partition large tables, and delete safely in batches. Compliance and analytics requirements should guide retention.

### 99. How would you review PostgreSQL changes as a senior developer?

**Answer:** Check schema design, constraints, indexes, query plans, migration locks, rollback strategy, and data backfill safety. Database changes deserve careful production thinking.

### 100. How would you explain PostgreSQL experience from this resume?

**Answer:** Describe building scalable Node.js services backed by PostgreSQL, optimizing REST API queries, using Prisma, designing auth and dashboard data models, and supporting ELD/ecommerce workflows.


## Reference Docs

- [PostgreSQL Current Documentation](https://www.postgresql.org/docs/current/)
- [PostgreSQL Indexes](https://www.postgresql.org/docs/current/indexes.html)
- [PostgreSQL Transaction Isolation](https://www.postgresql.org/docs/current/transaction-iso.html)
