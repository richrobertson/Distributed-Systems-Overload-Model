# Sample API Contracts

**Summary:** Example contract elements for overload-aware APIs.

- 429 with `Retry-After` and reason code for rate limits
- 503 with reason code for admission safety reject
- Idempotency key required for retriable write endpoints
- Response headers exposing applied limit policy and remaining budget
