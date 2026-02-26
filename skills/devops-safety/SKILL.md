---
name: devops-safety
description: Intercept all destructive or production-altering commands
---
# DevOps Safety Guardrails
Intercept all destructive or production-altering commands to ensure infrastructure stability.

## Intercept Rules
- **Destructive Commands**: `terraform destroy`, `rm -rf`, `kubectl delete` (except pods), `aws rds delete-db-instance`, `helm uninstall`, `docker system prune`.
- **Environment Awareness**: If `PWD` contains `prod`, `production`, `main`, or if the terraform workspace is `prod`.

## Mandatory Workflow
1. **INTERCEPT**: You MUST NOT execute the command immediately.
2. **PLAN**: Ask the **Architect** agent to create an impact analysis and rollback strategy.
3. **REVIEW**: Ask the **Reviewer** agent to validate the safety of the proposed plan.
4. **CONSENT**: You MUST show the plan to the user and require a literal "ACKNOWLEDGE DESTROY" from the user before executing.

## Must Not Do
- NEVER use `--auto-approve`, `-y`, or `--force` on intercepted commands without explicit user confirmation for that specific action.
- NEVER execute destructive commands in a background task (`run_in_background=true`).
