# OpsWatch — Deep Product & Market Research

**Owner / Content Creator:** Sandeep Barupal  
**Copyright:** © 2026 Sandeep Barupal. All rights reserved, except linked resources under their own terms.  
**Research status:** Deep-research baseline v1.0 — desk research, pending SRE/operator validation.

## 1. Product thesis
OpsWatch should help teams detect service degradation, understand impact, coordinate response and learn from incidents. Observability means correlating metrics, logs and traces with service ownership and deployment context—not simply displaying graphs.

## 2. Market landscape
The ecosystem spans telemetry standards, storage/query backends, dashboards, alerting, on-call and incident management. OpenTelemetry provides vendor-neutral instrumentation and telemetry conventions; Prometheus is widely used for metrics; Grafana IRM combines alert routing, on-call and incident response. Google SRE guidance emphasizes reliability objectives and operational learning. Sources: [OpenTelemetry docs](https://opentelemetry.io/docs/), [Prometheus overview](https://prometheus.io/docs/introduction/overview/), [Grafana IRM docs](https://grafana.com/docs/grafana-cloud/observe-and-act/respond-to-incidents/introduction/), [Google SRE Book](https://sre.google/sre-book/table-of-contents/).

## 3. Competitor categories
| Category | Examples | What to compare |
|---|---|---|
| Full-stack observability | Datadog, New Relic | Integrated telemetry, query model, pricing/ingestion controls |
| Open telemetry stack | Prometheus, Grafana, OpenTelemetry | Flexibility, operational burden, interoperability |
| Incident response | Grafana IRM, PagerDuty and similar | Escalation, on-call schedules, deduplication, integrations |
| Cloud-native monitoring | AWS/Azure/GCP tools | Native integration and cross-cloud visibility |

Avoid direct price comparisons without equivalent data volume, retention, seats and feature scope.

## 4. User jobs
On-call engineer: quickly determine severity and likely cause. SRE: track SLOs and error budgets. Service owner: understand dependencies and recent changes. Operations lead: manage incidents and follow-up actions. Executive: understand customer impact and reliability trends.

## 5. Feature specification
### P0
- Service catalog, ownership, environment and dependency links.
- Metrics dashboard and external telemetry links; show data freshness.
- Alert rules with threshold, query, severity, owner, routing and silence expiry.
- Incident lifecycle: declare, assign commander, timeline, impact, updates, resolve and postmortem.
- On-call schedule, escalation policy and notification delivery status.
- Audit log and integration health.
### P1
- OpenTelemetry ingestion/links; log/trace correlation; deployment annotations.
- SLO/SLI and error-budget tracking with burn-rate alerts.
- Alert grouping/deduplication, maintenance windows, runbook links and incident templates.
- Status page, postmortem action tracking and recurring-incident analysis.
### P2
- Change-risk correlation, anomaly detection and AI incident summaries with source-linked evidence and human verification.

## 6. Page map
Operations Overview; Service Catalog; Service Detail; Dashboards; Alerts; Alert Rule Editor; On-call; Escalations; Incident Command; Incident Timeline; SLOs; Error Budgets; Deployments; Runbooks; Postmortems; Integrations; Audit; Settings.

## 7. Architecture
Use telemetry adapters and standards-based integrations, time-series/log/trace stores or vendor links, alert evaluation, event deduplication, incident state machine and notification workers. Keep alert evaluation separate from UI requests. Use event IDs and idempotency to prevent duplicate incidents. Track pipeline health so missing telemetry cannot look like a healthy service.

## 8. Reliability and security
Protect observability credentials; restrict log access due to possible PII/secrets; redact sensitive fields; enforce tenant/service-level access; rate-limit notifications; test escalation fallback; retain incident audit trail; monitor the monitoring system itself. Do not automatically execute risky remediation without explicit policy and rollback.

## 9. Metrics
MTTD, time to acknowledge, time to mitigate, alert precision, pages per on-call shift, SLO attainment, error-budget burn, repeat incident rate, telemetry freshness and postmortem action completion. Pair speed metrics with customer impact and quality to avoid incentives to close incidents prematurely.

## 10. Risks and validation
Risks: alert noise, cardinality explosion, high telemetry cost, missing data, false anomaly detection, PII in logs and confusing incident ownership. Run tabletop exercises and test one scenario from signal to alert to incident to postmortem. Validate alert fatigue with on-call users before adding AI features.

## 11. References
- [OpenTelemetry](https://opentelemetry.io/docs/)
- [Prometheus](https://prometheus.io/docs/introduction/overview/)
- [Google SRE Book](https://sre.google/sre-book/table-of-contents/)
- [Grafana IRM](https://grafana.com/docs/grafana-cloud/observe-and-act/respond-to-incidents/introduction/)
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/)

## 12. Next work
Build a dated capability matrix, decide whether OpsWatch stores telemetry or integrates with existing backends, specify incident states and alert deduplication, then run an on-call usability test.