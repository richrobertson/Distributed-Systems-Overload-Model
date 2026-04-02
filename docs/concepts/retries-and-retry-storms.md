# Retries and Retry Storms

**Summary:** Retries can improve transient resilience but become overload multipliers when budgets, jitter, and deadlines are absent.

## What it is
Client or service attempts to reissue failed requests.

## Why it matters
Without governance, retries increase demand exactly when capacity is already constrained.

## What problem it solves
Controls positive-feedback loops that transform partial failures into systemic incidents.

## How it works
Use capped retries, exponential backoff with jitter, retry budgets, and idempotency protections.

## What it is not
Not a replacement for dependency recovery or capacity planning.

## Tradeoffs and failure modes
Too few retries reduce success for transient faults; too many amplify load and tail latency.

## Where it fits in the overload-control stack
Client SDKs, service-to-service calls, queue workers.

## Production scenario
Downstream timeout causes 3x retry fanout, doubling effective QPS and saturating shared gateway.

## What to instrument
Retry rate, attempts per request, success-after-retry ratio, and budget exhaustion.

## Related concepts
- [Circuit Breakers](circuit-breakers.md)
- [Retry Storm Scenario](../scenarios/retry-storm-scenario.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Retries must be budgeted load, not unconditional optimism.
