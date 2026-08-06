# Python Backend Scenario-Based Interview Questions & Answers

**Total questions:** 100

---

## Table of Contents

1. [Python & Debugging Scenarios (1-20)](#1-python--debugging-scenarios-1-20)
2. [API & Web Backend Scenarios (21-45)](#2-api--web-backend-scenarios-21-45)
3. [Database & ORM Scenarios (46-65)](#3-database--orm-scenarios-46-65)
4. [Async, Queues & Performance Scenarios (66-80)](#4-async-queues--performance-scenarios-66-80)
5. [Testing, Security & Deployment Scenarios (81-100)](#5-testing-security--deployment-scenarios-81-100)

---

## 1. Python & Debugging Scenarios (1-20)

### 1. A production bug happens because a function uses a mutable default argument like `def add_item(x, items=[])`. What is the issue and how would you fix it?

**Answer:** The default list is created once at function definition time and reused across calls, so state leaks between requests. I would change it to `items=None` and create a new list inside the function with `items = [] if items is None else items`.

### 2. A teammate says `is` and `==` are interchangeable for strings and integers because they often “work the same.” How would you explain the risk?

**Answer:** `==` compares values, while `is` compares object identity. Small strings or integers may appear identical because of interning, but relying on that is a bug. I would use `is` only for singletons like `None`, `True`, and `False`.

### 3. A script is consuming too much memory when processing a 5 GB log file. What changes would you make?

**Answer:** I would avoid reading the whole file into memory and process it line by line or in chunks. If multiple transformations are involved, I would use generators so each stage stays lazy.

### 4. You inherit code with a giant `try/except Exception:` block around the entire request handler. What problems can that cause?

**Answer:** It hides the real error source, makes debugging difficult, and can swallow programmer mistakes that should fail loudly. I would catch specific exceptions, log the context, and let unexpected errors propagate to monitoring.

### 5. An API endpoint sometimes returns stale data because a module-level variable is reused between requests. How would you approach this?

**Answer:** Module-level mutable state can be shared across requests and workers, which is risky. I would move request-specific state into function scope, request context, cache, or database depending on the need.

### 6. A colleague uses recursion for processing a very deep tree and it crashes in production. What likely happened?

**Answer:** Python has a recursion depth limit, so deeply nested recursion can raise `RecursionError`. I would rewrite it iteratively using an explicit stack unless the depth is guaranteed to stay small.

### 7. You need to compare two large lists and find common items efficiently. What would you do?

**Answer:** If order is not important, I would convert one or both lists to sets and use intersection because lookup is average O(1). If duplicates matter, I would use `Counter`.

### 8. A service crashes only in one environment because of timezone-related datetime bugs. What is your fix strategy?

**Answer:** I would standardize on timezone-aware datetimes, ideally in UTC internally. Then I would audit parsing, DB storage, serialization, and comparisons to ensure naive and aware datetimes are not mixed.

### 9. A helper function is difficult to test because it directly reads environment variables and creates network clients. How would you improve it?

**Answer:** I would inject configuration and dependencies rather than creating them inside the function. That makes the code easier to mock, easier to test, and less tightly coupled.

### 10. You see `TypeError: 'NoneType' object is not subscriptable` in production logs. How would you debug it?

**Answer:** It means code expected a dict/list-like object but got `None`. I would trace where the value is produced, add logging around the failing path, validate assumptions early, and either guard against `None` or fail with a clearer domain-specific error.

### 11. A background script gets slower over time and memory usage keeps increasing. What would you suspect first?

**Answer:** I would suspect unbounded in-memory collections, cached objects that never expire, unclosed resources, or a message consumer retaining references. I would inspect memory growth with tracemalloc or worker recycling and look for global state.

### 12. Two developers disagree on using a list versus tuple for returning query parameters from a helper. What would you choose?

**Answer:** If the result is fixed-size and should not be modified, I would use a tuple because it communicates immutability. If callers are expected to append or change values, a list is fine.

### 13. You need to parse user input that may be invalid, but the current code crashes frequently. What Python style would you prefer?

**Answer:** I would prefer explicit validation with targeted exception handling. In many cases EAFP works well: attempt the conversion, catch the expected exception, and return a clean validation error.

### 14. A function returns different types depending on conditions, and this causes bugs later. How would you refactor it?

**Answer:** I would make the return type consistent, such as always returning a dict, dataclass, or raising a specific exception. Predictable interfaces reduce downstream branching and runtime surprises.

### 15. You are reviewing code where a generator is iterated twice and the second pass is empty. What happened?

**Answer:** Generators are one-time iterators; once consumed they are exhausted. If the data needs to be reused, I would materialize it into a list or recreate the generator.

### 16. A bug appears after using `copy.copy()` on nested request payloads. Why?

**Answer:** `copy.copy()` is a shallow copy, so nested mutable objects are still shared. Changes inside nested dicts or lists can affect both copies. I would use `deepcopy` only if truly needed, or create a more targeted clone.

### 17. A utility function is slowing down a hot path because it recomputes the same expensive result repeatedly. What are reasonable fixes?

**Answer:** I would consider memoization with `functools.lru_cache` if inputs are hashable and the result is reusable. If the result depends on external state, I would use a bounded cache with invalidation rules.

### 18. A package import works on one machine but fails in CI with `ModuleNotFoundError`. What would you check?

**Answer:** I would check virtual environment activation, package installation, Python path assumptions, relative versus absolute imports, and whether the module is included in the project/package configuration.

### 19. A teammate added lots of metaprogramming and custom decorators, making the code hard to follow. What feedback would you give?

**Answer:** I would suggest simplifying unless the abstraction is solving a repeated problem clearly. In backend code, readability and debuggability usually matter more than cleverness.

### 20. An endpoint fails only for a specific Unicode username. How would you investigate?

**Answer:** I would check encoding assumptions across request parsing, database collation, validation, logging, and response serialization. I would also reproduce with the exact payload and verify the app consistently uses UTF-8.

---

## 2. API & Web Backend Scenarios (21-45)

### 21. Your login API is returning `403` when credentials are wrong. Would you keep that?

**Answer:** Usually no. Invalid or missing credentials should typically return `401 Unauthorized`. `403 Forbidden` is more appropriate when the user is authenticated but not allowed to access the resource.

### 22. A frontend team says your API sometimes takes 8 seconds but database time is low. Where would you look next?

**Answer:** I would inspect external service calls, serialization cost, network latency, middleware, large response payloads, and thread/worker starvation. Tracing is ideal because it shows where the request time is really spent.

### 23. You need to add a new field to an API response, but some old clients may break if they parse strictly. What would you do?

**Answer:** If clients are known to be fragile, I would version the API or coordinate rollout carefully. In general, additive response fields should be backward compatible, but real clients sometimes violate that expectation.

### 24. A product manager wants DELETE requests to be reversible. How might you implement that?

**Answer:** I would use soft deletes with a `deleted_at` field and exclude those rows from normal queries. Then I could add a restore endpoint or admin workflow if the business case supports it.

### 25. An endpoint creates duplicate orders when the client retries due to a timeout. How would you prevent that?

**Answer:** I would support idempotency keys for order creation and store the result by key. That way a retry returns the same logical result instead of creating another order.

### 26. A service is returning 500 for user validation errors. What is wrong with that design?

**Answer:** Validation failures are client errors, so they should return a 4xx response such as 400 or 422. Returning 500 makes monitoring noisy and hides whether the issue is in the client or server.

### 27. Your API needs to support both mobile apps and internal admin tools. How would you structure authentication?

**Answer:** I would separate concerns: for example JWT or OAuth-based auth for mobile/API consumers, and session or SSO-based auth for internal admin tools. The permission model should still come from a shared authorization layer.

### 28. A GET endpoint triggers an email as a side effect. Why is that a bad idea?

**Answer:** GET should be safe and not mutate state. Side effects on GET can break caching assumptions, create duplicate actions, and surprise clients or crawlers.

### 29. A FastAPI endpoint is marked `async`, but it still blocks badly under load. What likely happened?

**Answer:** The endpoint probably calls blocking I/O or CPU-heavy code directly. Declaring `async` alone does not make blocking work non-blocking; I would switch to async libraries or offload blocking code.

### 30. A Django app works locally but static files are missing in production. What common issue would you check?

**Answer:** I would verify `collectstatic` was run, static storage settings are correct, and nginx/CDN or Whitenoise is configured to serve the collected files.

### 31. An API returns huge nested JSON and mobile clients complain about slowness. What improvements would you suggest?

**Answer:** I would reduce unnecessary nesting, return only required fields, paginate related data, compress responses, and consider splitting the endpoint if it is doing too much.

### 32. A new API is expected to be called from browsers on another domain, but calls are blocked. What do you need to configure?

**Answer:** I would configure CORS correctly with allowed origins, methods, and headers. I would avoid an overly permissive policy in production.

### 33. Users report they get logged out randomly after deployment. What deployment-level issue could cause this?

**Answer:** Session secrets may be changing between instances or deployments, or sessions may be stored locally on one instance in a multi-instance setup. I would move session storage to a shared backend and keep secrets stable.

### 34. You need to deprecate an endpoint used by several clients. How would you handle it?

**Answer:** I would introduce a replacement, document the migration path, notify consumers early, monitor usage, and remove the old endpoint only after the deprecation window ends.

### 35. A route receives partial updates, but the team implemented it with PUT. Would you change it?

**Answer:** Yes, if the semantics are partial update then PATCH is clearer. PUT should usually represent full replacement of the resource.

### 36. A Flask codebase has business logic directly inside route functions. Why is that a problem?

**Answer:** It makes routes hard to test, reuse, and maintain. I would move business rules into services or use-case functions so routes stay thin and focused on HTTP concerns.

### 37. A response includes password hashes by mistake because of automatic model serialization. How do you prevent this class of bug?

**Answer:** I would use explicit response schemas or serializers and whitelist fields rather than returning ORM models directly. In FastAPI, `response_model` helps; in DRF, serializers help.

### 38. A frontend team wants offset pagination, but records are inserted frequently and users see duplicates while scrolling. What would you propose?

**Answer:** I would recommend cursor-based pagination using a stable sort key such as `created_at` plus id. It handles changing datasets better than offset-based pagination.

### 39. Your API gateway shows many `429` responses. What might be happening, and what would you check?

**Answer:** Clients may be exceeding rate limits, or the limit may be too strict for legitimate traffic. I would inspect the affected keys or IPs, burst patterns, retry behavior, and whether rate limiting logic is correctly scoped.

### 40. A FastAPI dependency opens a DB session but does not close it reliably. What is the risk?

**Answer:** Connections can leak and exhaust the pool under load. I would manage sessions with `yield` dependencies or context managers so cleanup happens consistently.

### 41. You’re asked to add request logging for debugging, but the app handles sensitive data. What would you log and avoid?

**Answer:** I would log request IDs, route, latency, status code, and selected metadata. I would avoid passwords, tokens, full PII payloads, and secrets.

### 42. A DRF endpoint is slow because each serializer field triggers another database hit. What is likely the issue?

**Answer:** It is probably an N+1 query problem caused by lazy relationship loading or per-item computed queries. I would optimize queryset fetching and move repeated work out of serializer loops.

### 43. Your app needs an internal admin endpoint that should never be public. How would you protect it?

**Answer:** I would require strong authentication and authorization, and ideally restrict network access as well, such as VPN, private ingress, or IP allowlists.

### 44. An API returns inconsistent error formats across endpoints. Why is that worth fixing?

**Answer:** Clients become harder to implement and debug. I would standardize error response structure so consumers can handle failures predictably.

### 45. A user reports double form submission creates duplicate records even from the web UI. What backend guard would you add besides frontend fixes?

**Answer:** I would enforce server-side protection such as idempotency tokens, unique constraints for the business key, or a deduplication check in the transaction.

---

## 3. Database & ORM Scenarios (46-65)

### 46. A page lists 100 orders and shows customer names, but it now issues 101 SQL queries. What is happening?

**Answer:** That is a classic N+1 query problem. The orders were likely loaded first, and each access to `order.customer` triggered another query. I would use eager loading like `select_related` or equivalent.

### 47. A query became slow after the table grew from 10k to 10 million rows. What is your first database check?

**Answer:** I would inspect the query plan with `EXPLAIN` or `EXPLAIN ANALYZE` and verify proper indexing, filter selectivity, and whether a sequential scan is now happening.

### 48. A teammate wants to add indexes to every column “just in case.” What would you say?

**Answer:** Indexes speed reads but slow writes and use storage. I would add indexes based on actual query patterns, joins, and sorting needs rather than indexing everything blindly.

### 49. An insert fails due to a unique constraint in production under concurrent requests. How should the backend handle it?

**Answer:** I would treat the database as the final source of truth and catch the integrity error cleanly. Depending on the endpoint, I might return 409 Conflict or convert the operation into an upsert/idempotent flow.

### 50. A migration adds a non-nullable column to a large table and causes downtime. What safer rollout would you use?

**Answer:** I would use an expand-contract approach: add the column nullable or with a safe default, deploy code that writes it, backfill existing rows, then enforce the non-null constraint later.

### 51. A report query is too complex in the ORM and becoming unreadable. Would you keep forcing ORM usage?

**Answer:** Not necessarily. For advanced reporting queries, raw SQL or SQLAlchemy Core can be clearer and faster as long as it stays parameterized and well tested.

### 52. A cache sometimes returns old profile data after a user update. What is the likely issue?

**Answer:** Cache invalidation is incomplete or delayed. I would define a clear cache-aside strategy and ensure writes invalidate or refresh the relevant keys.

### 53. You need to support searching users by email quickly. What would you add?

**Answer:** I would add an index on the email column, and if lookups should be case-insensitive, I would align the index and query strategy with the chosen collation or functional index.

### 54. A PostgreSQL read replica serves stale data right after a write, confusing users. How would you explain it?

**Answer:** Replica lag means reads may not immediately reflect writes. For read-after-write consistency, I would route those requests to the primary or add consistency-aware routing.

### 55. An endpoint updates account balance in two separate queries and occasionally loses money updates. What went wrong?

**Answer:** There is likely a race condition due to non-atomic read-modify-write logic. I would use a transaction with row locking, an atomic SQL update, or optimistic locking depending on the use case.

### 56. A long-running transaction blocks other writes and causes latency spikes. What changes would you make?

**Answer:** I would shorten transaction scope, move non-DB work outside it, commit earlier, and inspect whether lock contention or unnecessary row locks are being held.

### 57. A teammate wants to store everything in Redis because it is “fast.” What tradeoff would you raise?

**Answer:** Redis is excellent for cache and ephemeral data, but it is not automatically the right primary datastore. I would discuss durability, query flexibility, memory cost, persistence requirements, and operational complexity.

### 58. You need to delete a parent row, but child records must stay for audit. Would you use cascade delete?

**Answer:** No, not if the children must remain. I would model the relationship differently, archive the parent, or use a nullable foreign key depending on the domain rules.

### 59. A query on a JSONB column is now a hotspot. How would you optimize it?

**Answer:** I would inspect the exact query pattern and consider a suitable GIN or expression index, or move frequently filtered fields into normal columns if the access pattern is stable.

### 60. A soft delete implementation causes uniqueness issues when re-creating a user with the same email. What options do you have?

**Answer:** I could use a partial unique index only for active rows, restore the old record instead of creating a new one, or redesign the business rule depending on expected behavior.

### 61. A migration passes locally but fails in production because existing rows violate a new constraint. How would you avoid that in future?

**Answer:** I would validate production-like data before enforcing the constraint, add a backfill/cleanup step first, and stage schema changes across multiple deploys.

### 62. A query that joins several tables is correct but still slow. What additional things would you inspect besides indexes?

**Answer:** I would inspect row counts, join order, selected columns, sort operations, filter selectivity, stale statistics, and whether the app is fetching much more data than needed.

### 63. Your ORM session keeps stale object values after another transaction updates the same row. Why can that happen?

**Answer:** ORM sessions often cache object identity and state. I would refresh or expire the object, or scope sessions narrowly so stale state is less likely.

### 64. A developer uses string interpolation in SQL for a search filter. What is your review comment?

**Answer:** It risks SQL injection and should be replaced with parameterized queries immediately. Even internal tools should not build SQL from raw user input.

### 65. An audit table grows very fast and slows down analytics queries. What design ideas would you consider?

**Answer:** I would consider partitioning, retention rules, archival storage, summary tables, or moving analytics workloads to a separate reporting path if needed.

---

## 4. Async, Queues & Performance Scenarios (66-80)

### 66. A FastAPI service handles many outbound HTTP calls per request and starts timing out. What architectural improvement would you try first?

**Answer:** I would use a shared async HTTP client with connection pooling and make the calls concurrently where safe. I would also add timeouts and retries with limits.

### 67. A CPU-heavy CSV parsing step was moved into an `async def`, but throughput did not improve. Why not?

**Answer:** Async helps with waiting, not heavy computation. CPU-bound work should be moved to a worker process, multiprocessing pool, or a separate task queue.

### 68. Celery tasks occasionally run twice after worker restarts. How do you design around that?

**Answer:** I assume at-least-once delivery and make tasks idempotent. For example, I use unique business keys, dedupe checks, or upserts so retries do not create duplicate side effects.

### 69. A job queue keeps growing and response latency rises. What metrics would you check first?

**Answer:** I would check enqueue rate, processing rate, worker concurrency, job runtime distribution, retry counts, and failure reasons. That tells me whether the problem is insufficient capacity or broken jobs.

### 70. A service slows down every time an external payment provider is flaky. What resilience pattern would help?

**Answer:** I would use timeouts, retries with backoff, and a circuit breaker so failing dependencies do not drag down the entire service.

### 71. A team wants to spawn a new thread for every incoming request to improve speed. Would you recommend it?

**Answer:** No, not blindly. Unbounded threads can exhaust resources and hurt performance. I would use the framework/server concurrency model, pools, or async rather than ad hoc per-request threads.

### 72. A file-processing API sometimes exhausts memory when several uploads arrive together. How would you reduce risk?

**Answer:** I would stream uploads, process them in chunks, enforce size limits, and move heavy work to background jobs if synchronous processing is not required.

### 73. A Redis-backed rate limiter becomes a single point of failure. What would you consider?

**Answer:** I would decide whether the system should fail open or fail closed during Redis outages, add high availability if necessary, and consider gateway-level protection as another layer.

### 74. Your asyncio app creates many tasks but never awaits some of them. What can go wrong?

**Answer:** Exceptions may be lost, resources may leak, and shutdown becomes unreliable. I would track tasks explicitly or use structured concurrency patterns.

### 75. A team wants to cache every endpoint response forever because the data “rarely changes.” What caution would you raise?

**Answer:** Without expiration or invalidation, rare changes become hard bugs. I would define TTLs, invalidation rules, and cache only where the consistency tradeoff is acceptable.

### 76. Under load, Gunicorn workers keep restarting due to memory limits. What are plausible causes?

**Answer:** Large responses, memory leaks, oversized caches, per-request accumulation, or libraries holding buffers too long. I would measure worker RSS growth and profile allocation hotspots.

### 77. A batch job needs to call a third-party API for 100k users. How would you avoid getting rate limited?

**Answer:** I would process in controlled batches, respect provider quotas, add backoff and jitter, and persist progress so retries can resume safely.

### 78. A queue consumer updates the database and then crashes before acknowledging the message. What behavior do you expect?

**Answer:** The message may be redelivered, which is why the consumer must be idempotent. The DB write and ack are not automatically one atomic step.

### 79. A service spends most of its time serializing very large Python objects to JSON. How would you optimize?

**Answer:** I would reduce payload size first, then consider faster serializers, streaming responses where appropriate, and avoiding unnecessary intermediate object construction.

### 80. A scheduled job overlaps with itself and corrupts output files. What would you do?

**Answer:** I would add a lock or lease so only one instance runs at a time, make writes atomic, and ensure retries or reruns can detect incomplete work safely.

---

## 5. Testing, Security & Deployment Scenarios (81-100)

### 81. A bug reaches production because unit tests passed but the endpoint failed against the real database. What test gap does this suggest?

**Answer:** It suggests missing integration coverage. Unit tests alone may not catch ORM mappings, migrations, transaction behavior, or SQL differences.

### 82. A flaky test sometimes passes and sometimes fails in CI. What are common causes?

**Answer:** Shared mutable state, ordering dependencies, time-based assumptions, random data without fixed seeds, external network calls, and test pollution from previous cases.

### 83. A team mocks the database in almost every test, and regressions keep slipping through. What would you adjust?

**Answer:** I would keep mocking at true external boundaries when needed, but add integration tests with a real test database for repository and endpoint behavior.

### 84. A production issue cannot be traced because logs lack a common identifier. What would you add?

**Answer:** I would add request or correlation IDs and propagate them through logs, async jobs, and downstream service calls so a single flow can be followed end to end.

### 85. A user is able to access another user’s invoice by changing the URL id. What category of bug is this?

**Answer:** It is a broken authorization or IDOR-style issue. The backend must verify ownership or permission for every object access, not just authenticate the user.

### 86. An engineer wants to store JWTs in localStorage for convenience. What risk would you mention?

**Answer:** localStorage is vulnerable to token theft if the app has XSS. I would prefer safer patterns such as httpOnly cookies for browser apps when appropriate, plus CSRF protection strategy.

### 87. A deployment works in staging but fails in production because an env var is missing. How do you reduce that class of problem?

**Answer:** I would validate required configuration at startup and fail fast with a clear error. Infrastructure and deployment templates should define required settings explicitly.

### 88. A Docker image for a Python API is huge and slow to build. What improvements would you try?

**Answer:** I would use a slimmer base image, multi-stage builds if needed, copy dependency files before app code for better layer caching, and avoid unnecessary build tools in the final image.

### 89. A service exposes full stack traces in production error responses. Why is that risky?

**Answer:** It can leak implementation details, file paths, library versions, and internal behavior. I would keep detailed traces in logs and return sanitized error messages to clients.

### 90. A dependency scanner flags a vulnerable package, but the feature using it is barely used. Would you still act?

**Answer:** Yes, I would assess severity and exploitability, but low usage does not eliminate risk. I would patch or mitigate it according to exposure and urgency.

### 91. Your health check endpoint returns 200 even when the database is unreachable. Is that okay?

**Answer:** It depends on the check type. Liveness may stay 200 if the app process is alive, but readiness should fail if the app cannot serve real traffic due to a critical dependency outage.

### 92. A test suite takes 40 minutes and slows delivery. How would you improve it?

**Answer:** I would profile where time is spent, parallelize independent tests, reduce unnecessary integration setup, isolate slow end-to-end tests, and remove redundant coverage.

### 93. A developer commits secrets into the repo by mistake. What immediate steps would you take?

**Answer:** I would rotate the exposed secrets, remove them from the codebase, review access logs if relevant, and treat the secret as compromised even if the repo is private.

### 94. A rollout causes a spike in 500s, but only for one region. What would you investigate?

**Answer:** I would compare configuration, traffic patterns, dependency health, region-specific infrastructure, and whether only that region received a different build or environment setting.

### 95. A migration is safe in code review but still scares the team because it touches a huge table. What deployment steps help reduce risk?

**Answer:** I would test on production-like data, deploy during a low-traffic window if needed, monitor closely, add rollback or forward-fix plans, and prefer phased expand-contract changes.

### 96. An API key used by one customer starts making abusive traffic patterns. What controls would you apply?

**Answer:** I would rate limit or temporarily block that key, inspect usage patterns, alert the customer if appropriate, and ensure quotas and abuse detection are in place.

### 97. A webhook endpoint from a third party is being spoofed. How do you secure it?

**Answer:** I would verify signatures or shared-secret HMAC headers, validate timestamps to reduce replay risk, and reject unsigned or malformed requests.

### 98. After a blue-green deployment, users report inconsistent behavior between requests. What could explain that?

**Answer:** Traffic may be split between old and new versions that are not fully backward compatible, especially around sessions, schema changes, or cached payload formats.

### 99. A team wants 100% test coverage before every release. What would your balanced answer be?

**Answer:** Coverage is useful, but 100% is not the real goal. I would focus on meaningful coverage of critical paths, regressions, and business rules rather than inflating metrics with low-value tests.

### 100. You are asked in an interview: “Tell me about a backend incident you handled.” How would you structure the answer?

**Answer:** I would use a concise story: the symptom, impact, how I investigated, the technical root cause, the fix, and what preventive improvement I added afterward. Interviewers usually care about ownership, reasoning, and learning.

---

## How To Use This File

- Practice explaining each answer in your own words instead of memorizing line by line.
- For strong interview prep, pair these with examples from your own projects.
- If an interviewer asks follow-ups, talk about tradeoffs, failure modes, and how you would verify the fix.

---

*End of scenario-based interview guide.*
