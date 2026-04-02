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

## Closing summary
Circuit breakers preserve service by refusing to spend resources on likely-failing dependency calls.
