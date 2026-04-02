# Overload Control During Migrations

**Summary:** Migrations and cutovers alter demand shape and failure risk, so overload controls must be tightened and rehearsed before traffic moves.

## What it is
A migration-specific overload strategy for schema changes, infrastructure cutovers, region shifts, and control-plane transitions.

## Why it matters
Migrations often produce temporary dual-writes, cache cold starts, replay traffic, and operational retries—all of which increase load while tolerance for mistakes is low.

## What problem it solves
It prevents rollout-induced saturation and protects rollback pathways when dependency latency or error rates increase.

## How it works
1. Define migration load envelope and safe rollback capacity.
2. Apply stricter admission thresholds during cutover windows.
3. Reduce retry budgets and enforce idempotency keys.
4. Pre-warm caches and throttle backfills by priority lane.
5. Bound replay queues with hard age cutoffs.
6. Enable proactive degradation for non-critical features.
7. Use stage gates with automated halt criteria (latency, queue age, reject ratio).

## What it is not
It is not a one-time deploy checklist or blind canary rollout without overload signals.

## Tradeoffs and failure modes
- Conservative limits can slow migration velocity.
- Aggressive ramps can overload dependencies before dashboards reflect risk.
- Missing rollback capacity planning converts minor faults into prolonged incidents.

## Where it fits in the overload-control stack
Migration safety overlays every overload mechanism, especially admission, retries, queue bounds, and degradation toggles.

## Production scenario
During database cutover, dual-write traffic doubles write path demand. Admission caps background reindex jobs, load shedding disables analytics fanout, and graceful degradation serves cached secondary fields while write path remains healthy.

## What to instrument
- Dual-write latency/error split by old/new path
- Cutover queue depth and max age
- Retry fanout multiplier during migration windows
- Admission rejections by workload class
- Rollback readiness indicators (capacity reserve, lag, success rate)

## Related concepts
- [Rollout-Induced Overload Scenario](../scenarios/rollout-induced-overload.md)
- [Designing Safe Fallbacks](../design-guides/designing-safe-fallbacks.md)
- [Migration Cutover Example](../case-examples/migration-cutover-example.md)

## Closing summary
Migration reliability depends on overload discipline: bound demand, protect rollback, and prioritize critical state transitions.
