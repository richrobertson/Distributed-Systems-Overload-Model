# Rate Limiting

**Summary:** Rate limiting enforces traffic contracts over time windows to prevent sustained abuse or burst-induced saturation.

## What it is
A mechanism that caps request rate by principal (tenant, user, API key, route).

## Why it matters
It protects shared capacity and establishes fairness boundaries in multitenant systems.

## What problem it solves
It prevents demand from any one actor from crowding out others.

## How it works
Token bucket/leaky bucket or fixed-window counters enforce per-scope quotas with optional burst budgets.

## What it is not
It is not a complete overload strategy and does not replace admission or backpressure.

## Tradeoffs and failure modes
Hard caps can reject legitimate bursts; overly permissive burst budgets still cause queue spikes.

## Where it fits in the overload-control stack
Ingress and service edges, often combined with priority tiers.

## Production scenario
A single tenant sends large batch writes. Tenant bucket exhausts while other tenants continue within their budgets.

## What to instrument
Throttle rate by tenant, token utilization, burst consumption, and downstream latency at throttle boundaries.

## Related concepts
- [Admission vs Rate Limiting](../comparisons/admission-control-vs-rate-limiting.md)
- [Priority and Fairness](priority-and-fairness.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Rate limits provide durable fairness; admission adds real-time safety.
