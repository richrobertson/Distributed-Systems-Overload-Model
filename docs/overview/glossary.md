# Glossary

**Summary:** Canonical definitions used across this repository.

## Terms
- **Admission control:** Front-door decision to accept or reject work based on current safe capacity.
- **Backpressure:** Upstream signaling that downstream capacity is constrained.
- **Load shedding:** Intentional rejection of lower-value work during saturation.
- **Graceful degradation:** Planned reduction of non-critical behavior to preserve critical service.
- **Retry storm:** Traffic amplification caused by many clients retrying during partial failure.
- **Bounded queue:** Queue with explicit size/time limits and rejection policy.
- **Concurrency limit:** Maximum simultaneous work units a component can run safely.
