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

## Closing summary
Rate limits provide durable fairness; admission adds real-time safety.
