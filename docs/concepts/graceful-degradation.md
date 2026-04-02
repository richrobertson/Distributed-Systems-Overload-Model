# Graceful Degradation

**Summary:** Graceful degradation preserves critical outcomes by intentionally reducing non-essential behavior during overload or dependency failure.

## What it is
A predefined set of reduced-capability modes that maintain core functionality.

## Why it matters
All-or-nothing uptime goals are unrealistic under severe stress; degradation keeps essential paths alive.

## What problem it solves
It avoids broad outages by narrowing what the system attempts.

## How it works
Feature flags, fallback data paths, reduced consistency modes, or deferred side effects activate based on overload signals.

## What it is not
It is not silent data loss and not ad hoc incident improvisation.

## Tradeoffs and failure modes
Reduced feature quality, stale data exposure, and potential business-impact tradeoffs if overused.

## Where it fits in the overload-control stack
Late-stage protection after admission/limiting controls, integrated with circuit breakers and shedding.

## Production scenario
Control plane disables non-critical audit enrichments and real-time notifications while maintaining core resource reconciliation.

## What to instrument
Mode activation frequency/duration, core success rate during degradation, and backlog growth in deferred subsystems.

## Related concepts
- [Designing for Degraded Modes](../design-guides/designing-for-degraded-modes.md)
- [Graceful Degradation vs Failure](../comparisons/graceful-degradation-vs-failure.md)

## Closing summary
Graceful degradation is intentional service contraction that preserves mission-critical behavior.
