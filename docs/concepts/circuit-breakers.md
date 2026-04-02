# Circuit Breakers

**Summary:** Circuit breakers stop repeated calls to unhealthy dependencies to protect local resources and reduce futile load.

## What it is
A state machine (closed/open/half-open) around dependency calls.

## Why it matters
Repeated timeouts burn threads, sockets, and retries while producing little value.

## What problem it solves
It contains partial dependency failures before they become global application failures.

## How it works
Breaker opens when failure thresholds are exceeded, blocks calls for a cooldown, then probes cautiously in half-open state.

## What it is not
It is not a retry mechanism and not a substitute for timeout budgets.

## Tradeoffs and failure modes
Overly sensitive breakers can trip on transient noise; overly slow breakers permit resource exhaustion.

## Where it fits in the overload-control stack
Dependency protection layer alongside isolation pools and deadlines.

## Production scenario
Notification provider latency spikes. Breaker opens and traffic shifts to deferred delivery mode.

## What to instrument
Open rate, half-open probe success, blocked call count, and recovered latency distribution.

## Related concepts
- [Dependency Isolation](dependency-isolation.md)
- [Circuit Breakers vs Retries](../comparisons/circuit-breakers-vs-retries.md)

## Related reading on myrobertson.com
- [Distributed Systems Writing Hub](https://www.myrobertson.com/blog/)
- [Backpressure in Distributed Systems: Stability, Correctness, and Graceful Degradation](https://www.myrobertson.com/blog/backpressure-stability-correctness-distributed-systems)
- [API Backpressure Explained Simply](https://www.myrobertson.com/blog/api-backpressure-explained-simply)
- [What Is a Control Plane?](https://www.myrobertson.com/blog/what-is-a-control-plane)
- [Architecting a Multitenant Control Plane for a Next-Generation Data Tier](https://www.myrobertson.com/blog/architecting-a-multitenant-control-plane-for-a-next-generation-data-tier)
- [Distributed Systems Case Studies](https://www.myrobertson.com/case-studies/)

## Closing summary
Circuit breakers preserve service by refusing to spend resources on likely-failing dependency calls.
