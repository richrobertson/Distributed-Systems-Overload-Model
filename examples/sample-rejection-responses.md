# Sample Rejection Responses

**Summary:** Example rejection payloads that help clients react safely.

```json
{
  "error": "overload_rejected",
  "reason": "admission_safety_boundary",
  "retry_after_ms": 500,
  "request_class": "standard"
}
```

```json
{
  "error": "rate_limited",
  "reason": "tenant_token_exhausted",
  "retry_after_ms": 1000,
  "tenant": "acme-co"
}
```
