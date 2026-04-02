# Overload Observability

**Summary:** Overload observability tracks saturation, queueing, and rejection signals needed to detect and control instability before outage.

## What it is
Metrics, logs, traces, and derived indicators centered on capacity boundaries and control actions.

## Why it matters
Latency-only dashboards hide impending collapse until too late.

## What problem it solves
Provides actionable detection for pre-failure saturation and ineffective controls.

## How it works
Instrument admission outcomes, queue age/depth, concurrency saturation, breaker states, retry amplification, and degradation modes.

## What it is not
Not generic service telemetry disconnected from overload semantics.

## Tradeoffs and failure modes
Higher cardinality and metric cost if dimensions are unmanaged.

## Where it fits in the overload-control stack
Cross-cutting across all overload controls and incident response workflows.

## Production scenario
Alert fires on rising queue age + reject ratio + retry amplification before user-visible hard outage.

## What to instrument
Saturation index, rejection reason rates, queue age p95/p99, retry fanout factor, and mode-transition churn.

## Related concepts
- [Instrumentation and Alerting](../design-guides/instrumentation-and-alerting.md)
- [Sample Alerts](../../examples/sample-alerts.md)

## Closing summary
You cannot operate overload controls you do not measure explicitly.
