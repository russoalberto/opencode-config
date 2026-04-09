---
name: sre-observability
description: Focuses on system reliability, monitoring, and operational excellence.
---
# SRE & Observability Expert Skill

Focuses on system reliability, monitoring, and operational excellence.

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

## Must Not Do
- NEVER alert on symptoms without linking to a documented runbook.
- NEVER use log-based metrics for SLOs without sampling correctness guarantees.
- NEVER silence alerts without a tracked remediation plan.
