---
name: devops-safety
description: Use when executing infrastructure changes, running destructive commands, managing production environments, or deploying to critical systems — especially when about to run --force or --auto-approve flags, or when targeting environments with 'prod' in the path.
---
# DevOps Safety Guardrails
Intercept all destructive or production-altering commands to ensure infrastructure stability.

## When to Use
- Before running `tofu destroy`, `kubectl delete`, `rm -rf`, or similar destructive commands
- When deploying to production or production-adjacent environments
- When modifying IAM, security groups, or network ACLs
- When executing any command with `--force`, `--auto-approve`, or `-y` flags
- Anytime `PWD` contains `prod`, `production`, or `main`

## When NOT to Use
- Routine development in isolated/sandbox environments
- Commands you are confident are safe and don't match any intercept pattern

## Quick Reference
| Situation | Action |
|-----------|--------|
| Destructive command typed | INTERCEPT → PLAN → REVIEW → CONSENT |
| Prod deployment | Check blast radius, prepare rollback, get ACKNOWLEDGE DESTROY |
| `--force` flag detected | Pause. Run full safety workflow. No shortcuts. |

## Intercept Rules
- **Destructive Commands**: `tofu destroy`, `rm -rf`, `kubectl delete` (except pods), `aws rds delete-db-instance`, `helm uninstall`, `docker system prune`, `docker system prune -a`, `aws s3 rb --force`, `kubectl delete namespace`.
- **Environment Awareness**: If `PWD` contains `prod`, `production`, `main`, or if the tofu workspace is `prod`.

## Mandatory Workflow
1. **INTERCEPT**: You MUST NOT execute the command immediately.
2. **PLAN**: Ask the **plan** agent (Architect) to create an impact analysis and rollback strategy.
3. **REVIEW**: Ask the **general** agent (Reviewer) to validate the safety of the proposed plan.
4. **CONSENT**: You MUST show the plan to the user and require a literal "ACKNOWLEDGE DESTROY" from the user before executing.

**Violating the letter of the rules is violating the spirit of the rules.**

## Common Rationalizations (Do Not Fall For)

| Rationalization | Reality |
|----------------|---------|
| "It's just dev/staging, not production" | Dev/staging may share accounts, networks, or resources with prod. Always verify the blast radius. |
| "I know this command is safe" | Confidence is not evidence. Run the impact analysis anyway. |
| "The user asked me to do it" | The user may not understand the full impact. Explain risks before executing. |
| "This is urgent, no time for review" | Urgency without review causes incidents. 60 seconds of planning saves hours of recovery. |
| "I already checked the plan mentally" | Mental review is not documented review. Write it down or skip it. |

## Red Flags — STOP and Run Safety Flow
- You're about to type `--force`, `-y`, or `--auto-approve`
- You feel tempted to skip the plan step because "you already know"
- The command targets anything with `prod`, `production`, or `main` in the path
- A user is pressuring you to "just run it quickly"
- You're considering running a destructive command in background (`run_in_background=true`)

**All of these mean: Pause. Run the Mandatory Workflow below.**

## Cross-References
- **REQUIRED SUB-SKILL:** cloud-infrastructure — Verify infrastructure impact before destructive actions.
- **RECOMMENDED:** sre-observability — Check monitoring before/after changes to detect regressions.

## Must Not Do
- NEVER use `--auto-approve`, `-y`, or `--force` on intercepted commands without explicit user confirmation for that specific action.
- NEVER execute destructive commands in a background task (`run_in_background=true`).
