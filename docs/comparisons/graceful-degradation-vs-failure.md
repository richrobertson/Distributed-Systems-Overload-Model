# Graceful Degradation vs Failure

**Summary:** Degradation is intentional capability reduction; failure is uncontrolled loss of service.

## Definitions of both concepts
See linked concept pages for canonical definitions.

## Core distinction
This page distinguishes decision timing, control objective, and failure behavior under saturation.

## Where they overlap
Both are overload-control mechanisms intended to preserve stability and critical paths.

## Where they differ
They act at different layers and use different signals, policies, and tradeoffs.

## When to use both
Use both in production systems with variable demand and shared dependencies to avoid single-point control assumptions.

## Failure modes when confused
Teams either reject too late, retry too aggressively, or assume one mechanism covers all overload behaviors.

## Related concepts
- [Overload Control Model](../overview/overload-control-model.md)
- [Concepts Index](../concepts)
