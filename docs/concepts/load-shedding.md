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

## Closing summary
Shedding is controlled sacrifice: lose low-value work to preserve high-value service.
