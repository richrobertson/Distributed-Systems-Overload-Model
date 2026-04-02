# Load Shedding

**Summary:** Load shedding intentionally drops selected work under saturation so critical paths continue to meet service goals.

## What it is
Policy-driven rejection of lower-value requests when capacity is constrained.

## Why it matters
When total demand exceeds safe capacity, some work must be denied to avoid total collapse.

## What problem it solves
It prevents saturation from affecting all request classes equally.

## How it works
Shedding policies use priority tiers, request cost estimates, and current saturation metrics to reject or defer low-priority work.

## What it is not
It is not random failure and not equivalent to static rate limits.

## Tradeoffs and failure modes
Users may see reduced features; incorrect priority rules can discard important workloads.

## Where it fits in the overload-control stack
Near worker pools, dependency boundaries, and ingress under severe pressure.

## Production scenario
During peak traffic, recommendation and analytics requests are shed while checkout and auth remain protected.

## What to instrument
Shed rate by tier, critical-path latency during shedding, and policy-miss incidents.

## Related concepts
- [Admission vs Load Shedding](../comparisons/admission-control-vs-load-shedding.md)
- [Graceful Degradation](graceful-degradation.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Shedding is controlled sacrifice: lose low-value work to preserve high-value service.
