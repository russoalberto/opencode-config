---
name: sre-observability
description: Use when setting up monitoring and alerting, defining SLOs/SLIs, investigating production incidents, or designing observability strategy — especially when encountering alert fatigue, missing correlation IDs in logs, or outages without documented runbooks.
---
# SRE & Observability Expert Skill

Focuses on system reliability, monitoring, and operational excellence.

## When to Use
- Setting up or improving monitoring (Prometheus, Grafana, CloudWatch)
- Defining SLOs, SLIs, and error budgets for services
- Instrumenting code with OpenTelemetry for distributed tracing
- Investigating production incidents or performance regressions
- Building incident response runbooks and escalation paths

## When NOT to Use
- Infrastructure provisioning (use cloud-infrastructure)
- Application feature development without observability concerns

## Quick Reference
| Situation | Action |
|-----------|--------|
| New service going live | Add metrics, structured logging, and distributed tracing |
| Incident in progress | Check runbook, correlate traces, assess SLO burn rate |
| Alert fatigue mounting | Review severity tiers, consolidate noisy alerts, add escalation paths |

## Core Pillars
- **Metrics:** Prometheus, Grafana, and SLI/SLO definition.
- **Logging:** Structured JSON logging, ELK/EFK stack, and log aggregation.
- **Tracing:** OpenTelemetry (OTel) instrumentation and distributed tracing.

## Key Principles
- **Reliability:** Design for high availability and fault tolerance.
- **SLIs/SLOs:** Define clear Service Level Indicators and Objectives to measure system health.
- **Incident Response:** Develop clear runbooks and automated alerting.
- **Automation:** Automate toil and routine operational tasks.

## Workflow
- Instrument code with OpenTelemetry for better visibility.
- Monitor error rates, latency, and resource utilization.
- Implement health checks and automated recovery where possible.

## Must Do
- ALWAYS define and publish SLIs/SLOs for critical services.
- ALWAYS implement structured logging with correlation IDs for traceability.
- ALWAYS set up alerting with actionable runbooks and escalation paths.
- ALWAYS test failover mechanisms and disaster recovery procedures.

## Common Mistakes
- **Alert fatigue**: Too many low-severity alerts cause genuine incidents to be ignored. Define alert severity tiers.
- **Dashboards without runbooks**: Charts without documented remediation steps don't help during incidents.
- **SLOs set once, never revisited**: SLOs must evolve with system usage patterns. Review quarterly.

## Cross-References
- **RECOMMENDED:** devops-safety — Incident response safety when running recovery commands.
- **RECOMMENDED:** cloud-infrastructure — Monitor infrastructure health and resource utilization.
- **RECOMMENDED:** backend-architect — Application-level metrics and tracing integration.

## Must Not Do
- NEVER alert on symptoms without linking to a documented runbook.
- NEVER use log-based metrics for SLOs without sampling correctness guarantees.
- NEVER silence alerts without a tracked remediation plan.
