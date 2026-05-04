---
name: cloud-infrastructure
description: Use when provisioning cloud resources, designing network topology, writing Terraform/OpenTofu modules, or planning multi-cloud architecture — especially when encountering state lock conflicts, drift detection failures, or cost overruns from untagged resources.
---
# Cloud Infrastructure Expert Skill

Specialist in Infrastructure as Code (IaC), cloud architecture, and platform engineering.

## When to Use
- Provisioning cloud resources (AWS, GCP, Azure) with IaC
- Designing VPC, subnet, and network topology
- Writing or reviewing Terraform/OpenTofu modules
- Planning multi-cloud or hybrid cloud strategy

## When NOT to Use
- Application-level architecture without infrastructure concerns (use backend-architect)
- CI/CD pipeline configuration (use cicd-automation)

## Quick Reference
| Situation | Action |
|-----------|--------|
| Provisioning new resources | Write module, `tofu plan`, review diff, `tofu apply` |
| State lock conflict | Identify holder, verify safety, force unlock (rare) |
| Cost spike detected | Check untagged resources, orphaned volumes, oversized instances |

## Core Technologies
- **Terraform / OpenTofu:** Modular IaC design, state management, and provider configuration.
- **Cloud Providers:** Deep understanding of AWS, GCP, and Azure services (Compute, Storage, Networking, IAM).
- **Kubernetes:** Orchestration, Helm charts, and cluster configuration.

## Key Principles
- **Immutable Infrastructure:** Treat infrastructure as code and deploy versioned changes.
- **Least Privilege:** Implement fine-grained IAM roles and security groups.
- **Network Security:** Secure VPC design, private subnets, and load balancing.
- **Cost Optimization:** Monitor resource usage and suggest efficient instance types.

## Workflow
- Always perform `tofu plan` before applying changes.
- Ensure sensitive variables are never committed to version control.
- Prioritize modular and reusable IaC components.

## Must Do
- ALWAYS use state locking for Terraform backends (S3 + DynamoDB, GCS, Azure Blob).
- ALWAYS version-control IaC modules and pin provider versions.
- ALWAYS set up drift detection on critical infrastructure.
- ALWAYS implement resource tagging for cost allocation and governance.

## Common Mistakes
- **State mismanagement**: Losing or corrupting Terraform state files. Always use remote state with locking.
- **Tagging neglect**: Skipping resource tags makes cost allocation and governance impossible.
- **Hardcoded environments**: Duplicating modules instead of using variables and workspaces.

## Cross-References
- **REQUIRED SUB-SKILL:** devops-safety — Safety intercepts for destructive infrastructure commands.
- **REQUIRED SUB-SKILL:** security-auditor — IAM policy review and network security validation.
- **RECOMMENDED:** sre-observability — Monitoring and alerting for provisioned infrastructure.

## Must Not Do
- NEVER hardcode cloud provider credentials or access keys in code.
- NEVER use `tofu apply` without reviewing a `tofu plan` first.
- NEVER expose database ports or internal services to the public internet without network controls.
