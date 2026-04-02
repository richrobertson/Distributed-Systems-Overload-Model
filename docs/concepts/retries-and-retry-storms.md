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

## Closing summary
Retries must be budgeted load, not unconditional optimism.
