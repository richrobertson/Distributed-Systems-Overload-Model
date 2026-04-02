# Sample Metrics

**Summary:** Example overload metrics taxonomy for APIs, workers, and dependencies.

- admission.accepted_total / admission.rejected_total{reason,tenant}
- queue.depth / queue.age_p95 / queue.age_p99
- concurrency.inflight / concurrency.limit / permit.wait_ms
- retry.attempts_total / retry.fanout_factor
- breaker.state{dependency}
- shed.total{priority}
- degradation.mode_active{mode}
