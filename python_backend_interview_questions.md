# Python Backend Interview Questions & Answers

**Total questions:** 200

---

## Table of Contents

1. [Python Fundamentals (1–40)](#1-python-fundamentals-140)
2. [Data Structures & Algorithms (41–60)](#2-data-structures--algorithms-4160)
3. [OOP & Design Patterns (61–80)](#3-oop--design-patterns-6180)
4. [Web Frameworks — Django / Flask / FastAPI (81–110)](#4-web-frameworks--django--flask--fastapi-81110)
5. [REST APIs & HTTP (111–130)](#5-rest-apis--http-111130)
6. [Databases & ORM (131–155)](#6-databases--orm-131155)
7. [Async, Concurrency & Performance (156–170)](#7-async-concurrency--performance-156170)
8. [Testing, Debugging & Code Quality (171–180)](#8-testing-debugging--code-quality-171180)
9. [DevOps, Security & System Design Basics (181–200)](#9-devops-security--system-design-basics-181200)

---

## 1. Python Fundamentals (1–40)

### 1. What is the difference between a list and a tuple?

**Answer:** Lists are mutable (`[]`); tuples are immutable (`()`). Lists support append/remove; tuples do not. Tuples are hashable (if contents are hashable) and can be used as dict keys. Tuples are slightly faster and use less memory for fixed collections.

### 2. What is the difference between `==` and `is`?

**Answer:** `==` compares values (equality). `is` compares object identity (same memory address). Example: `a = [1]; b = [1]` → `a == b` is True, `a is b` is False.

### 3. Explain mutable vs immutable types.

**Answer:** Mutable objects can change in place: `list`, `dict`, `set`, `bytearray`. Immutable objects cannot: `int`, `float`, `str`, `tuple`, `frozenset`, `bytes`. Reassignment creates a new object for immutables.

### 4. What are `*args` and `**kwargs`?

**Answer:** `*args` collects extra positional arguments into a tuple. `**kwargs` collects extra keyword arguments into a dict. Useful for flexible APIs and wrappers.

### 5. What is a generator? How does it differ from a list?

**Answer:** A generator yields values lazily with `yield` (or a generator expression). It does not store all values in memory. Lists are eager and hold everything. Generators are one-pass iterators.

### 6. What is the GIL?

**Answer:** The Global Interpreter Lock (GIL) allows only one thread to execute Python bytecode at a time in CPython. It simplifies memory management but limits CPU-bound multithreading. I/O-bound work and multiprocessing still benefit.

### 7. Difference between `@staticmethod`, `@classmethod`, and instance methods?

**Answer:** Instance methods take `self`. Class methods take `cls` and can access/modify class state. Static methods take neither; they are namespaced functions on the class with no implicit first argument.

### 8. What are Python decorators?

**Answer:** Decorators are callable wrappers that modify or extend another function/class without changing its source. Syntax: `@decorator` above a `def`. Common uses: logging, auth, caching, timing.

### 9. Explain list comprehension vs generator expression.

**Answer:** `[x for x in range(10)]` builds a full list. `(x for x in range(10))` returns a generator. Prefer generators for large sequences to save memory.

### 10. What is `__init__` vs `__new__`?

**Answer:** `__new__` creates and returns a new instance (rarely overridden). `__init__` initializes the instance after creation. `__new__` is called before `__init__`.

### 11. What are dunder (magic) methods?

**Answer:** Special methods with double underscores (`__str__`, `__repr__`, `__len__`, `__eq__`, `__enter__`, etc.) that define object behavior with built-in operations and protocols.

### 12. How does Python handle memory management?

**Answer:** Reference counting plus a cyclic garbage collector. When refcount hits zero, memory is freed. GC handles reference cycles. Objects live on a private heap managed by Python.

### 13. What is the difference between `deepcopy` and `shallow copy`?

**Answer:** Shallow copy (`copy.copy`) copies the container but shares nested objects. Deep copy (`copy.deepcopy`) recursively copies nested objects. Mutating nested data in a shallow copy affects the original.

### 14. Explain `*`, `/`, and `*` as parameter separators.

**Answer:** `*` alone forces following parameters to be keyword-only. `/` forces preceding parameters to be positional-only (Python 3.8+). Useful for clearer APIs and preventing breaking changes.

### 15. What is EAFP vs LBYL?

**Answer:** EAFP (“Easier to Ask Forgiveness than Permission”) uses try/except. LBYL (“Look Before You Leap”) checks conditions first. Python style prefers EAFP when races or type checks are messy.

### 16. What does `if __name__ == "__main__":` do?

**Answer:** Code under that block runs only when the file is executed as a script, not when imported as a module. Keeps import side effects out of reusable code.

### 17. Difference between `range` and `xrange`?

**Answer:** In Python 2, `range` returned a list and `xrange` was lazy. In Python 3, `range` is lazy (like `xrange`); `xrange` was removed.

### 18. What are context managers? How do you write one?

**Answer:** Objects used with `with` that manage setup/teardown (files, locks, DB sessions). Implement `__enter__`/`__exit__`, or use `@contextlib.contextmanager` with `yield`.

### 19. Explain `pass`, `continue`, and `break`.

**Answer:** `pass` is a no-op placeholder. `continue` skips to the next loop iteration. `break` exits the nearest loop.

### 20. What is the difference between `append` and `extend`?

**Answer:** `append(x)` adds `x` as a single element. `extend(iterable)` adds each item from the iterable. `a.append([1,2])` → nested list; `a.extend([1,2])` → flat.

### 21. How do you swap two variables in Python?

**Answer:** `a, b = b, a` — tuple unpacking; no temporary variable needed.

### 22. What is a lambda function? Limitations?

**Answer:** An anonymous single-expression function: `lambda x: x * 2`. Cannot contain statements, multiple expressions, or annotations easily. Prefer named `def` for complex logic.

### 23. Explain Python’s LEGB rule.

**Answer:** Name resolution order: Local → Enclosing → Global → Built-in. Closures see enclosing scopes; `nonlocal`/`global` alter binding.

### 24. What is `zip()`? What about unpacking?

**Answer:** `zip(a, b)` pairs elements until the shortest iterable ends. `zip(*pairs)` unpacks pairs back into separate sequences.

### 25. Difference between `remove`, `pop`, and `del` for lists?

**Answer:** `remove(value)` deletes the first matching value. `pop(i)` removes by index and returns it (default last). `del list[i]` removes by index without returning.

### 26. What are f-strings? Pros?

**Answer:** Formatted string literals (`f"Hello {name}"`) evaluated at runtime. Faster and more readable than `%` or `.format()` for most cases. Support expressions and format specs.

### 27. How does exception handling work? `else` and `finally`?

**Answer:** `try` runs code; `except` handles errors; `else` runs if no exception; `finally` always runs (cleanup). Prefer specific exceptions over bare `except`.

### 28. What is `None`? Is it a singleton?

**Answer:** `None` is the null object. There is only one `None` instance; compare with `is None`, not `== None`.

### 29. Explain duck typing.

**Answer:** “If it walks like a duck and quacks like a duck…” — type is determined by behavior (methods/attributes), not inheritance. Python favors interfaces via protocols over strict types.

### 30. What is the difference between modules and packages?

**Answer:** A module is a `.py` file. A package is a directory with `__init__.py` (or namespace package) that groups modules. Import paths reflect the package hierarchy.

### 31. How do virtual environments work?

**Answer:** Tools like `venv`/`virtualenv`/`poetry` isolate project dependencies. Each env has its own `site-packages` so projects don’t conflict. Activate before installing packages.

### 32. What is `pip` vs `poetry` vs `pipenv`?

**Answer:** `pip` installs packages; often with `requirements.txt`. Poetry and Pipenv manage dependencies + lockfiles + virtualenvs more rigorously. Poetry is widely used for apps/libraries today.

### 33. Explain `collections.defaultdict` and `Counter`.

**Answer:** `defaultdict(factory)` auto-creates missing keys via `factory`. `Counter` counts hashable objects; supports most common / least common helpers.

### 34. What is `enumerate`?

**Answer:** `enumerate(iterable, start=0)` yields `(index, value)` pairs — cleaner than manual counters.

### 35. Difference between `str` and `repr`?

**Answer:** `str()` is user-friendly display. `repr()` aims for unambiguous, often developer-facing representation (ideally `eval`-able). `__str__` vs `__repr__`.

### 36. How do you read a large file efficiently?

**Answer:** Iterate line by line (`for line in f`) instead of `f.read()`. Use buffered reading, generators, or chunked reads. Avoid loading entire file into memory.

### 37. What are type hints? Are they enforced?

**Answer:** Annotations like `def f(x: int) -> str:` document expected types. Runtime does not enforce them (unless you use tools). Used by mypy, pyright, IDEs.

### 38. What is `dataclasses`?

**Answer:** `@dataclass` auto-generates `__init__`, `__repr__`, `__eq__`, etc. Reduces boilerplate for data-holding classes. Supports defaults, frozen, slots (3.10+).

### 39. Explain walrus operator `:=`.

**Answer:** Assignment expression (Python 3.8+): assigns and returns a value in one expression, e.g. `while (line := f.readline()):`.

### 40. What is the difference between `async def` and normal `def`?

**Answer:** `async def` defines a coroutine that must be awaited or scheduled on an event loop. Normal `def` runs synchronously. Mixing blocking I/O in async code can stall the loop.

---

## 2. Data Structures & Algorithms (41–60)

### 41. Time complexity of common list operations?

**Answer:** Indexing/append amortized O(1). Insert/delete at start O(n). Membership O(n). Sorting O(n log n).

### 42. Time complexity of dict/set operations?

**Answer:** Average O(1) for get/set/delete/membership (hash table). Worst case O(n) with pathological collisions. Keys must be hashable.

### 43. When would you use a deque?

**Answer:** `collections.deque` for O(1) append/pop from both ends — queues, sliding windows, BFS. Lists are O(n) at the left end.

### 44. How do you reverse a string/list?

**Answer:** Slicing: `s[::-1]` or `list.reverse()` / `reversed()`. For interviews, also know two-pointer in-place reverse for lists.

### 45. Explain Big-O briefly.

**Answer:** Asymptotic upper bound on growth of time/space as input size grows. Focus on dominant term: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ).

### 46. How would you find duplicates in a list?

**Answer:** Use a `set` while iterating; if seen again, it’s a duplicate. Or `Counter` for frequencies. Sorting + adjacent compare is O(n log n) without extra hash memory tradeoffs.

### 47. What is a hash collision? How does Python handle it?

**Answer:** Two keys map to the same hash bucket. CPython dicts use open addressing with probing. Collisions degrade performance but are handled correctly for correctness.

### 48. Difference between array (list) and linked list conceptually?

**Answer:** Arrays: contiguous, O(1) index, costly mid insert. Linked lists: O(1) insert/delete given node, O(n) access. Python `list` is dynamic array; linked lists via custom nodes or `deque` internals.

### 49. Explain stack vs queue.

**Answer:** Stack: LIFO (push/pop same end). Queue: FIFO (enqueue one end, dequeue other). Use list/`deque` accordingly.

### 50. How do you implement a FIFO queue in Python?

**Answer:** Prefer `collections.deque` with `append`/`popleft`. `queue.Queue` for thread-safe use. Avoid `list.pop(0)` for performance.

### 51. What is binary search? Requirements?

**Answer:** Search sorted data by repeatedly halving the range — O(log n). Data must be sorted (or searchable via monotonic predicate). `bisect` module helps.

### 52. Explain recursion vs iteration.

**Answer:** Recursion: function calls itself; elegant for trees/divide-conquer; risk of stack overflow. Iteration: loops; usually more memory-efficient. Tail recursion isn’t optimized in CPython.

### 53. What is a heap? When use `heapq`?

**Answer:** Binary heap for priority queues. `heapq` provides min-heap. Use for top-k, merge sorted streams, Dijkstra. Max-heap via negated values.

### 54. How do you merge two sorted lists?

**Answer:** Two-pointer merge: compare heads, append smaller, advance — O(n+m). Or `heapq.merge` for multiple iterables lazily.

### 55. What is memoization?

**Answer:** Caching function results for given inputs to avoid recomputation. `@functools.lru_cache` or manual dict. Classic for Fibonacci/DP.

### 56. Explain sliding window pattern.

**Answer:** Maintain a window over a sequence that expands/contracts to satisfy a condition (max sum of size k, longest substring without repeat). Often O(n) vs O(n²) nested loops.

### 57. How do you detect a cycle in a linked list?

**Answer:** Floyd’s tortoise and hare: slow/fast pointers; if they meet, cycle exists. Or track visited node ids in a set.

### 58. Difference between BFS and DFS?

**Answer:** BFS (queue): level-order, shortest path in unweighted graphs. DFS (stack/recursion): explores deep paths first; good for connectivity, topological sort, path existence.

### 59. What is a trie used for?

**Answer:** Prefix tree for strings — autocomplete, dictionary lookup, IP routing prefixes. Fast prefix queries; memory heavier than hash sets.

### 60. How would you find the k-th largest element?

**Answer:** Sort O(n log n), or min-heap of size k O(n log k), or Quickselect average O(n). `heapq.nlargest(k, iterable)[-1]`.

---

## 3. OOP & Design Patterns (61–80)

### 61. What are the four pillars of OOP?

**Answer:** Encapsulation, Abstraction, Inheritance, Polymorphism. Python supports all; encapsulation is convention-based (`_protected`, `__name_mangling`).

### 62. Difference between inheritance and composition?

**Answer:** Inheritance: “is-a” via subclassing. Composition: “has-a” via containing objects. Prefer composition for flexibility and looser coupling.

### 63. What is MRO? How does Python resolve it?

**Answer:** Method Resolution Order — the order Python searches for attributes in multiple inheritance. C3 linearization; inspect with `Class.__mro__` or `help(Class)`.

### 64. What is an abstract base class (ABC)?

**Answer:** `abc.ABC` + `@abstractmethod` define interfaces that subclasses must implement. Instantiating an incomplete ABC raises `TypeError`.

### 65. Explain polymorphism with an example.

**Answer:** Same interface, different behavior: `len()` works on str/list/dict via `__len__`. Or subclasses overriding `draw()` with different shapes.

### 66. What is the Singleton pattern? Concerns?

**Answer:** Ensure one instance. In Python: module-level object, metaclass, or `__new__`. Can hurt testability and hide dependencies; prefer DI when possible.

### 67. What is the Factory pattern?

**Answer:** A function/class that creates objects without exposing construction logic. Useful when concrete type depends on config/runtime input.

### 68. What is Dependency Injection?

**Answer:** Pass dependencies into a class/function rather than creating them inside. Improves testability and decoupling (mock DB/repo in tests).

### 69. Explain Repository pattern in backends.

**Answer:** Abstracts data access behind an interface (`UserRepository.get_by_id`). Services depend on the repo, not ORM details — cleaner layers and easier mocking.

### 70. What is the Strategy pattern?

**Answer:** Encapsulate interchangeable algorithms behind a common interface (e.g., payment processors, sort strategies). Swap at runtime without if/else sprawl.

### 71. What is SOLID? Name each letter.

**Answer:** Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion. Guides maintainable OOP design.

### 72. What is tight vs loose coupling?

**Answer:** Tight: components hardwired together; hard to change/test. Loose: interact via interfaces/events; easier to swap implementations.

### 73. Difference between composition and aggregation?

**Answer:** Both are “has-a”. Composition: owned lifecycle (part dies with whole). Aggregation: shared/independent lifecycle. Conceptual UML distinction.

### 74. What are mixins?

**Answer:** Classes providing reusable methods via multiple inheritance without being standalone base types (e.g., `JsonSerializableMixin`). Keep them focused.

### 75. How does encapsulation work in Python?

**Answer:** No true private members. Convention: `_internal`, `__mangled`. Properties (`@property`) control access. Trust the developer culture.

### 76. What is a property in Python?

**Answer:** `@property` turns a method into attribute-like access with getter/setter/deleter — validation without changing call sites to methods.

### 77. Explain the Observer pattern.

**Answer:** Subject notifies registered observers on state change (events, pub/sub). Django signals and many event buses follow this idea.

### 78. What is DRY, KISS, YAGNI?

**Answer:** Don’t Repeat Yourself; Keep It Simple Stupid; You Aren’t Gonna Need It. Avoid premature abstraction and unused features.

### 79. When is inheritance a bad idea?

**Answer:** Deep hierarchies, fragile base classes, forcing “is-a” that isn’t true, sharing code that isn’t a true subtype. Prefer composition/mixins carefully.

### 80. What is an interface in Python terms?

**Answer:** No formal `interface` keyword. Use ABCs, Protocols (`typing.Protocol` — structural subtyping), or duck typing documentation.

---

## 4. Web Frameworks — Django / Flask / FastAPI (81–110)

### 81. Django vs Flask vs FastAPI — when to use each?

**Answer:** Django: batteries-included monoliths (ORM, admin, auth). Flask: minimal, flexible microservices/APIs. FastAPI: modern async APIs with automatic OpenAPI and type-hint validation; great for high-concurrency I/O services.

### 82. What is WSGI vs ASGI?

**Answer:** WSGI is the sync Python web standard (Django classic, Flask). ASGI supports async and WebSockets (FastAPI, Django ASGI, Starlette). Uvicorn/Hypercorn are ASGI servers; Gunicorn often WSGI (or with Uvicorn workers).

### 83. Explain Django MVT.

**Answer:** Model (data), View (request logic), Template (presentation). Similar to MVC; Django’s “view” is closer to a controller.

### 84. What are Django migrations?

**Answer:** Versioned schema changes generated from model changes (`makemigrations` / `migrate`). Applied in order; keep them in VCS. Avoid editing applied migrations casually.

### 85. Difference between Django `ForeignKey`, `OneToOne`, `ManyToMany`?

**Answer:** FK: many-to-one. OneToOne: unique FK both ways. M2M: through table (implicit or explicit). Choose based on cardinality.

### 86. What is `select_related` vs `prefetch_related`?

**Answer:** `select_related`: SQL JOINs for FK/OneToOne (single query). `prefetch_related`: separate query + Python join for M2M/reverse FK. Prevents N+1 queries.

### 87. What causes the N+1 query problem?

**Answer:** Looping over objects and hitting related fields lazily, one query per row. Fix with `select_related`/`prefetch_related`, eager loading, or batch queries.

### 88. Flask: application factory pattern — why?

**Answer:** `create_app()` builds the app with config/extensions. Enables multiple configs, testing, and avoids circular imports from global app objects.

### 89. What are Flask blueprints?

**Answer:** Modular route groups with their own templates/static. Register on the app — scales larger Flask projects.

### 90. FastAPI: what does Pydantic do?

**Answer:** Validates and serializes request/response data from type hints. Gives clear 422 errors and OpenAPI schemas automatically.

### 91. FastAPI dependency injection — purpose?

**Answer:** `Depends()` injects shared logic (DB sessions, auth, pagination). Reusable, testable, composable request plumbing.

### 92. How do you handle CORS?

**Answer:** Configure allowed origins/methods/headers via middleware (`CORSMiddleware` in FastAPI/Starlette, `django-cors-headers`, Flask-CORS). Never use `*` with credentials in production.

### 93. What is middleware?

**Answer:** Components that process requests/responses globally (auth, logging, CORS, GZip). In Django: middleware stack; in FastAPI/Starlette: ASGI middleware.

### 94. Explain Django signals briefly.

**Answer:** Decoupled notifications (`pre_save`, `post_save`, etc.). Useful for side effects; overuse hides control flow — prefer explicit service calls when clarity matters.

### 95. What is Django REST Framework (DRF)?

**Answer:** Toolkit for building REST APIs on Django: serializers, viewsets, routers, permissions, authentication, browsable API.

### 96. Serializer vs ModelSerializer in DRF?

**Answer:** Serializer: manual field definitions. ModelSerializer: auto fields from a model + create/update helpers. Customize validation as needed.

### 97. What are Django class-based views vs function-based?

**Answer:** FBVs: simple and explicit. CBVs: reuse via inheritance/mixins (ListView, APIView). Prefer clarity; CBVs help for standard CRUD patterns.

### 98. How does FastAPI background tasks work?

**Answer:** `BackgroundTasks` runs functions after the response is sent — fine for light work (email send). For heavy/reliable jobs use Celery/RQ/arq.

### 99. What is Uvicorn?

**Answer:** Lightning-fast ASGI server built on uvloop/httptools. Common production choice behind nginx for FastAPI/Starlette apps.

### 100. How do you structure a mid-size FastAPI project?

**Answer:** Separate routers, schemas (Pydantic), models, services/use-cases, repositories, dependencies, and config. Keep routers thin; business logic in services.

### 101. Django `settings.py` — environment-specific config?

**Answer:** Use env vars (`django-environ`, `pydantic-settings`), split settings modules, or 12-factor config. Never commit secrets.

### 102. What is Flask’s `g` object?

**Answer:** Request-scoped temporary storage for data during a request (e.g., current user, DB connection). Cleared after the request.

### 103. Explain CSRF protection.

**Answer:** Cross-Site Request Forgery: browser sends cookies on malicious sites’ requests. Django forms/middleware use CSRF tokens. APIs often use tokens/headers instead of cookie sessions alone.

### 104. How do sessions work in Django?

**Answer:** Server stores session data (DB/cache/file); client gets a session cookie id. Configurable backends. Prefer cache/DB for multi-instance deploys.

### 105. What is Jinja2?

**Answer:** Popular templating engine (Flask default, Django-inspired syntax). Used for HTML/email templates with inheritance and filters.

### 106. FastAPI `response_model` — why use it?

**Answer:** Filters/validates outgoing data, documents schema, and prevents leaking sensitive fields accidentally.

### 107. How do you version APIs in these frameworks?

**Answer:** URL prefix (`/api/v1`), headers, or Accept versioning. Mount versioned routers. Keep backward compatibility until clients migrate.

### 108. What is Django Admin good for?

**Answer:** Rapid internal CRUD UI for models. Customize list displays, filters, actions. Not a public-facing product UI.

### 109. Explain request lifecycle briefly (Django).

**Answer:** Request → middleware → URL resolve → view → (ORM/service) → response → middleware → client. Exceptions handled by handlers/middleware.

### 110. How do you serve static files in production?

**Answer:** Collect static (`collectstatic`), serve via CDN/nginx/S3 — not the app server. Whitenoise can serve from the app for simpler setups.

---

## 5. REST APIs & HTTP (111–130)

### 111. What is REST?

**Answer:** Architectural style: resources identified by URIs, manipulated via HTTP methods, stateless requests, representations (JSON/XML). Not a strict protocol — conventions vary.

### 112. Common HTTP methods and idempotency?

**Answer:** GET (read, idempotent, safe), POST (create/action, not idempotent), PUT (replace, idempotent), PATCH (partial update), DELETE (idempotent ideally). Idempotent: same effect if repeated.

### 113. What are common HTTP status codes you use?

**Answer:** 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable, 429 Too Many Requests, 500 Internal Server Error.

### 114. 401 vs 403?

**Answer:** 401: not authenticated (missing/invalid credentials). 403: authenticated but not allowed. Some APIs blur them; be consistent.

### 115. What is idempotency key used for?

**Answer:** Client sends a unique key with POST so retries don’t create duplicates (payments, orders). Server stores key → result mapping.

### 116. REST vs GraphQL vs gRPC?

**Answer:** REST: resource URLs, simple caching/HTTP. GraphQL: client-shaped queries, one endpoint, over/under-fetching control. gRPC: binary Protobuf, strong contracts, great for service-to-service; less browser-native.

### 117. What is HATEOAS?

**Answer:** Hypermedia as the Engine of Application State — responses include links to related actions. Rarely fully adopted; “REST maturity” concept.

### 118. How do you design pagination?

**Answer:** Offset/limit (simple, can skip inconsistently) or cursor-based (stable for infinite scroll). Return `next`/`prev` links and totals when useful.

### 119. What is content negotiation?

**Answer:** Client and server agree on representation via `Accept` / `Content-Type` headers (JSON vs XML, etc.).

### 120. Explain JWT structure and risks.

**Answer:** Header.Payload.Signature (Base64URL). Stateless auth claims. Risks: long-lived tokens, secret leak, no easy revoke — use short TTL + refresh tokens + denylist if needed. Don’t put secrets in payload (it’s readable).

### 121. Cookie-based vs token-based auth?

**Answer:** Cookies: browser auto-sends; CSRF concerns; good for first-party web. Bearer tokens: explicit Authorization header; common for SPAs/mobile/APIs; store carefully (prefer httpOnly cookies for web XSS mitigation).

### 122. What is OAuth2 vs OpenID Connect?

**Answer:** OAuth2: authorization (delegated access). OIDC: identity layer on OAuth2 (who the user is — ID token). “Login with Google” is typically OIDC.

### 123. How do you version and deprecate APIs?

**Answer:** Version in path/header; announce deprecation; monitor usage; keep overlap period; document migration; eventually remove with notice.

### 124. What makes a good error response body?

**Answer:** Consistent shape: `code`, `message`, optional `details`/`fields`. Don’t leak stack traces in production. Map domain errors to HTTP statuses.

### 125. What is rate limiting? Where enforce it?

**Answer:** Cap requests per client/IP/API key. Enforce at gateway/nginx/API middleware/Redis counters. Return 429 + `Retry-After`.

### 126. PUT vs PATCH?

**Answer:** PUT replaces the whole resource (client sends complete state). PATCH applies partial updates. Prefer PATCH for sparse updates.

### 127. What is CORS and when do you need it?

**Answer:** Browser security: cross-origin XHR/fetch restricted unless server allows via CORS headers. Needed for SPAs on different origins calling your API.

### 128. Safe vs unsafe HTTP methods?

**Answer:** Safe methods (GET, HEAD, OPTIONS) shouldn’t change server state. Unsafe (POST, PUT, PATCH, DELETE) may. Caching proxies rely on this.

### 129. How do you secure an API? Checklist.

**Answer:** HTTPS, authn/authz, input validation, rate limits, least privilege DB users, secrets in vault/env, logging without PII, dependency updates, CORS lockdown, security headers.

### 130. What is OpenAPI/Swagger?

**Answer:** Spec for describing HTTP APIs. FastAPI generates it from code. Used for docs, client generation, contract testing.

---

## 6. Databases & ORM (131–155)

### 131. SQL vs NoSQL — when each?

**Answer:** SQL: structured data, strong consistency, complex joins, transactions. NoSQL (document/key-value): flexible schemas, horizontal scale, simple access patterns. Choose by query patterns and consistency needs.

### 132. What is ACID?

**Answer:** Atomicity, Consistency, Isolation, Durability — properties of reliable transactions in relational DBs.

### 133. Explain database indexes. Tradeoffs?

**Answer:** Structures (usually B-trees) that speed lookups/filters/sorts. Tradeoffs: slower writes, extra storage. Index columns used in WHERE/JOIN/ORDER BY carefully; avoid over-indexing.

### 134. What is a primary key vs unique vs foreign key?

**Answer:** PK uniquely identifies a row (often surrogate id). UNIQUE constrains uniqueness. FK enforces referential integrity to another table’s key.

### 135. INNER JOIN vs LEFT JOIN?

**Answer:** INNER: only matching rows both sides. LEFT: all left rows + matches from right (NULLs if none). RIGHT/FULL less common in app SQL.

### 136. What is normalization? Denormalization?

**Answer:** Normalization reduces redundancy (1NF–3NF typical). Denormalization adds redundancy for read performance. Balance consistency vs speed.

### 137. What is a transaction isolation level?

**Answer:** Controls visibility of concurrent transactions: Read Uncommitted, Read Committed, Repeatable Read, Serializable. Higher = fewer anomalies, more locking/contention.

### 138. Explain optimistic vs pessimistic locking.

**Answer:** Optimistic: assume rare conflicts; version column; fail on stale update. Pessimistic: lock rows (`SELECT FOR UPDATE`) during transaction. Choose based on contention.

### 139. What is connection pooling? Why needed?

**Answer:** Reuse DB connections instead of opening per request. Creating connections is expensive. Tools: SQLAlchemy pool, PgBouncer, Django CONN_MAX_AGE.

### 140. How do you prevent SQL injection?

**Answer:** Always parameterized queries / ORM bindings. Never concatenate user input into SQL. Validate/sanitize inputs as defense in depth.

### 141. ORM vs raw SQL — when raw?

**Answer:** ORM for CRUD and maintainability. Raw/SQLAlchemy Core for complex reports, window functions, performance-critical queries, DB-specific features. Measure with EXPLAIN.

### 142. What is Alembic / Django migrations role?

**Answer:** Schema migration tools that version DB changes with application code. Essential for team deploys and rollbacks strategy.

### 143. Explain eventual consistency.

**Answer:** System may temporarily show stale data but converges. Common in distributed/NoSQL/replicas. OK for feeds/caches; careful for balances/inventory.

### 144. What is Redis used for in backends?

**Answer:** Cache, session store, rate limiting, pub/sub, leaderboards, job queues (with RQ/Celery broker). In-memory, very fast; persistence optional.

### 145. Cache strategies: cache-aside vs write-through?

**Answer:** Cache-aside: app reads cache → miss → DB → populate cache. Write-through: write DB and cache together. Also write-behind, TTL eviction, stampede protection.

### 146. What is the thundering herd / cache stampede?

**Answer:** Many requests miss same hot key simultaneously and slam the DB. Mitigate with locking, soft TTL, probabilistic early refresh, or singleflight.

### 147. Explain database migrations zero-downtime tips.

**Answer:** Expand-contract: add columns nullable → deploy code → backfill → enforce constraints → remove old. Avoid destructive renames in one step. Feature flags help.

### 148. What is EXPLAIN / EXPLAIN ANALYZE?

**Answer:** Shows query plan (and actual timings with ANALYZE). Use to find sequential scans, bad joins, missing indexes.

### 149. Difference between MongoDB and PostgreSQL?

**Answer:** Postgres: relational, SQL, strong transactions, rich types/JSON too. Mongo: document store, flexible schema, horizontal sharding focus. Postgres often enough with JSONB.

### 150. What is JSONB in PostgreSQL?

**Answer:** Binary JSON storage with indexing (GIN) and querying. Good for semi-structured attributes without a separate document DB.

### 151. How do you handle soft deletes?

**Answer:** `deleted_at` timestamp instead of DELETE. Filter in queries/default managers. Tradeoffs: unique constraints, storage, accidental inclusion — document carefully.

### 152. What is a database migration rollback strategy?

**Answer:** Prefer forward-fix migrations. Keep backups. Test down migrations in staging. For production, restore from backup or reverse expand-contract if needed.

### 153. SQLAlchemy Session vs Engine?

**Answer:** Engine: connection pool + dialect. Session: unit of work / identity map for ORM objects. Commit/rollback at session boundaries.

### 154. What is `CASCADE` on foreign keys?

**Answer:** Deleting/updating parent auto-deletes/updates children. Convenient but dangerous — accidental mass deletes. Prefer explicit application deletes when unsure.

### 155. How do you choose between UUID and auto-increment IDs?

**Answer:** Auto-increment: simple, compact, sequential. UUID: safer for distributed generation, harder to guess, larger indexes. UUIDv7 improves sortability.

---

## 7. Async, Concurrency & Performance (156–170)

### 156. Threading vs multiprocessing vs asyncio?

**Answer:** Threading: good for I/O; limited by GIL for CPU. Multiprocessing: true parallelism for CPU-bound. Asyncio: single-thread cooperative concurrency for many I/O connections with less overhead.

### 157. What is an event loop?

**Answer:** Core of asyncio: schedules and runs coroutines, callbacks, and I/O ready events. Only one coroutine runs at a time until it awaits.

### 158. `asyncio.gather` vs `create_task`?

**Answer:** `gather` runs awaitables concurrently and waits for all. `create_task` schedules a coroutine on the loop immediately; you can await later. Fire-and-forget tasks need careful exception handling.

### 159. When should you not use async?

**Answer:** CPU-heavy work, libraries that are blocking-only without thread offload, simple CRUD with low concurrency. Async shines with many waiting connections.

### 160. How do you run blocking code in async apps?

**Answer:** `asyncio.to_thread()` or run in an executor. Don’t call blocking DB/HTTP drivers on the event loop.

### 161. What is Celery? Typical use cases?

**Answer:** Distributed task queue: background jobs, emails, image processing, scheduled tasks. Broker (Redis/RabbitMQ) + workers + optional result backend.

### 162. At-least-once vs exactly-once delivery?

**Answer:** Most queues are at-least-once → design idempotent consumers. Exactly-once is hard; often exactly-once processing via idempotency keys + dedupe store.

### 163. How do you profile a slow Python API?

**Answer:** Measure: APM (Datadog/New Relic), `cProfile`, Django Debug Toolbar, `py-spy`, slow query logs, EXPLAIN. Fix N+1, add indexes, cache, reduce payloads.

### 164. What is horizontal vs vertical scaling?

**Answer:** Vertical: bigger machine. Horizontal: more instances behind a load balancer. Horizontal needs stateless apps + shared store (DB/Redis).

### 165. How does Gunicorn worker model work?

**Answer:** Prefork workers handle requests. Sync workers: one request per worker. Use gevent/uvicorn workers for concurrency. Tune workers ≈ 2–4 × CPU for sync CPU-light apps (rule of thumb).

### 166. What is backpressure?

**Answer:** Slowing producers when consumers can’t keep up (queue limits, 429s, buffering). Prevents unbounded memory growth and cascading failure.

### 167. Explain circuit breaker pattern.

**Answer:** Stop calling a failing dependency temporarily; fail fast; retry after cooldown. Protects your service from cascading outages.

### 168. What is `async with` used for?

**Answer:** Asynchronous context managers (`__aenter__`/`__aexit__`) — e.g., async DB sessions, HTTP clients (`httpx.AsyncClient`).

### 169. Difference between CPU-bound and I/O-bound?

**Answer:** CPU-bound: computation (use multiprocessing/C extensions). I/O-bound: waiting on network/disk (threads/async help). Know which before optimizing.

### 170. How do you prevent memory leaks in long-running workers?

**Answer:** Avoid global caches without bounds, close connections, watch reference cycles, recycle workers (Gunicorn `max_requests`), profile with tracemalloc/`objgraph`.

---

## 8. Testing, Debugging & Code Quality (171–180)

### 171. Unit vs integration vs e2e tests?

**Answer:** Unit: isolated functions/classes (mocks). Integration: real DB/cache/HTTP boundaries. E2E: full user flows. Pyramid: many unit, fewer e2e.

### 172. What is pytest and why prefer it?

**Answer:** Popular test runner: fixtures, parametrize, plugins, clear assert introspection. De facto standard over unittest for many teams.

### 173. What are pytest fixtures?

**Answer:** Reusable setup/teardown injected into tests by name. Scopes: function/class/module/session. Compose fixtures for DB sessions, clients, users.

### 174. How do you test FastAPI/Django APIs?

**Answer:** FastAPI: `TestClient`/`httpx.ASGITransport`. Django: `APIClient`/`Client`. Prefer DB transactions rolled back per test; factory_boy/faker for data.

### 175. What is mocking? When is it wrong?

**Answer:** Replace dependencies with fakes (`unittest.mock`, `respx`). Over-mocking tests implementation details and misses integration bugs — mock at boundaries.

### 176. What is TDD?

**Answer:** Red-Green-Refactor: write failing test → implement → clean up. Improves design and regression safety when practiced pragmatically.

### 177. How do you debug production issues?

**Answer:** Structured logs + correlation IDs, metrics/traces, reproduce with same inputs, feature flags, careful hotfixes, postmortems. Don’t debug only via SSH print statements.

### 178. What is linting/formatting stack?

**Answer:** `ruff`/`flake8`, `black`/`ruff format`, `isort`, `mypy`/`pyright`. Enforce in CI/pre-commit for consistent quality.

### 179. What is coverage? Is 100% the goal?

**Answer:** Measures which lines ran in tests. High coverage helps but doesn’t guarantee correctness. Prefer meaningful assertions over chasing 100%.

### 180. How do you write a good bug report / ticket?

**Answer:** Expected vs actual, steps to reproduce, environment, logs/IDs, impact/severity, screenshots. Clear titles help triage.

---

## 9. DevOps, Security & System Design Basics (181–200)

### 181. What is CI/CD?

**Answer:** Continuous Integration: auto build/test on every push. Continuous Delivery/Deployment: auto promote to staging/prod. Catch bugs early; ship smaller changes.

### 182. What is Docker? Why use it for Python apps?

**Answer:** Containers package app + runtime + deps. Same behavior across machines. Dockerfile defines image; Compose for local multi-service (app/db/redis).

### 183. Difference between image and container?

**Answer:** Image: immutable template. Container: running instance of an image. Like class vs object.

### 184. What is Kubernetes at a high level?

**Answer:** Orchestrates containers: scheduling, scaling, health checks, rolling updates, service discovery. Useful at scale; overkill for tiny apps.

### 185. 12-factor app principles (name a few)?

**Answer:** Codebase in VCS, explicit deps, config in env, backing services as attached resources, build/release/run stages, stateless processes, port binding, logs as event streams.

### 186. How do you manage secrets?

**Answer:** Env vars for simple cases; Vault/AWS Secrets Manager/GCP Secret Manager for production. Never commit secrets; rotate regularly; least privilege IAM.

### 187. What is HTTPS/TLS doing?

**Answer:** Encrypts traffic and authenticates the server (via certificates). Prevents eavesdropping/tampering. Terminate TLS at load balancer or app.

### 188. OWASP Top risks relevant to APIs?

**Answer:** Broken auth, injection, SSRF, security misconfig, vulnerable components, excessive data exposure, lack of rate limiting, improper asset management. Validate inputs; patch deps.

### 189. How would you design a URL shortener (high level)?

**Answer:** API to create/redirect; store `code → long_url`; generate unique codes (hash/base62 id); cache hot redirects in Redis; analytics async; DB for durability.

### 190. How would you design a notification system?

**Answer:** API enqueues events → workers fan out to email/SMS/push providers; templates; user preferences; retries with backoff; idempotency; dead-letter queue for failures.

### 191. Explain load balancer basics.

**Answer:** Distributes traffic across instances (round-robin, least connections). Health checks remove bad nodes. Often terminates TLS and handles sticky sessions if needed.

### 192. What is a reverse proxy (nginx)?

**Answer:** Sits in front of app servers: TLS, static files, rate limit, buffering, routing. Clients talk to nginx; nginx talks to Gunicorn/Uvicorn.

### 193. CAP theorem in one sentence?

**Answer:** In a partition, a distributed system must choose Consistency or Availability (Partition tolerance assumed). Practical systems tune this tradeoff.

### 194. How do you make a Python service observable?

**Answer:** Structured JSON logs, metrics (latency/error/QPS), distributed tracing (OpenTelemetry), health/readiness endpoints, alerting on SLOs.

### 195. Blue-green vs rolling vs canary deploys?

**Answer:** Blue-green: switch traffic between two environments. Rolling: gradually replace instances. Canary: small % traffic to new version first. Canary reduces blast radius.

### 196. What is idempotent consumer design for queues?

**Answer:** Store processed message IDs; use unique business keys; upsert instead of insert; safe retries. Prevents duplicate side effects under at-least-once delivery.

### 197. How do you handle file uploads safely?

**Answer:** Limit size/type, scan/validate content, store outside web root/S3 with random keys, virus scan if needed, never trust filenames, serve via signed URLs.

### 198. Difference between authentication and authorization?

**Answer:** Authentication: who you are. Authorization: what you’re allowed to do. Implement both (JWT/session + roles/permissions/policies).

### 199. How would you approach designing a rate-limited public API?

**Answer:** API keys, Redis sliding window/token bucket per key, gateway enforcement, clear 429s, tiers/quotas, monitoring abuse, WAF for volumetric attacks.

### 200. Walk through debugging a 500 error in production.

**Answer:** Check error tracker (Sentry) for stack + request id → correlate logs/traces → identify recent deploys → reproduce in staging → fix with test → deploy hotfix → verify metrics/error rate drops → write postmortem if needed.

---

## Quick Study Tips (2 YOE)

- Be ready to **write code** on lists/dicts, SQL joins, and a small FastAPI/Django endpoint.
- Explain **tradeoffs** (sync vs async, SQL vs cache, ORM vs raw) more than buzzwords.
- Know **your stack deeply**: one framework, one DB, Redis, and how you deploy.
- Prepare **2–3 project stories**: bottleneck you fixed, bug you hunted, design choice you owned.

---

*Good luck with your interviews.*
