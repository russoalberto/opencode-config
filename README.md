# Opencode Secure Full-Stack & DevOps Configuration

## 🚀 Overview
This configuration is tailored for **Full-Stack Developers** and **DevOps/SREs** who require a high-speed development loop without compromising on security or code privacy. It balances autonomous code generation with strict manual controls for infrastructure and sensitive data.

## 🛡️ Core Design Principles

### 1. Code Privacy First
Privacy is a non-negotiable mandate. The system is configured to **never** leak proprietary source code, internal IPs, API keys, or sensitive database schemas to external services.
- **Generalized External Searches:** When using tools like Exa (web search) or Context7 (documentation), queries are automatically generalized and stripped of project-specific identifiers.
- **Example:** Instead of searching "How to fix auth in project-x for user-y", the system searches "JWT authentication best practices in Node.js".

### 2. Security & DevOps Guardrails
The agent operates with a security-first mindset, following the principle of least privilege.
- **Destructive Operations:** The agent is instructed to always pause and ask for explicit confirmation before suggesting or executing destructive commands (e.g., `rm -rf`, `terraform destroy`, `kubectl delete`).
- **Infrastructure Awareness:** The agent treats infrastructure state (`.tfstate`, `kubeconfig`, etc.) with extreme caution, ensuring no accidental modifications occur without oversight.

### 3. Automated yet Controlled Workflow
A hybrid permission model is used to maximize developer velocity:
- **Auto-Edits (`allow`):** The agent can autonomously create, modify, and refactor code files, allowing for a seamless development experience.
- **Safe Shell Commands (`allow`):** Read-only and build-related commands are pre-approved (e.g., `npm install`, `ng build`, `tsc`, `git status`, `terraform plan`, `docker ps`).
- **Sensitive Operations (`ask`):** Any command that reads secrets or modifies remote environments (e.g., `cat *.env`, `terraform apply`, `kubectl delete`) requires manual user approval.

## 🛠️ Global Guardrails (`AGENTS.md`)
The `AGENTS.md` file is injected into every session, ensuring consistent behavior across all tasks. It mandates:
- **Verification:** Always running tests, linters, or build commands after code changes.
- **Conventions:** Strict adherence to project-specific coding standards and architectural patterns.

## 🧩 Specialized Skills (`@skills/`)
The agent can dynamically adopt specialized personas to provide expert-level assistance across the stack:

| Skill | Description |
| :--- | :--- |
| 🛡️ **devops-safety** | Intercepts all destructive or production-altering commands. |
| 🔒 **security-auditor** | Specialist in secure coding, OWASP Top 10, and vulnerability assessment. |
| ⚙️ **backend-architect** | Expert in API design, microservices, and scalable backend systems. |
| 🗄️ **database-expert** | Specialist in SQL/NoSQL optimization, schema design, and migrations. |
| 🚀 **cicd-automation** | Expert in Docker, Kubernetes, GitHub Actions, and pipelines. |
| 🎨 **frontend-expert** | Expert in Angular (standalone, RxJS, NgRx), React, Vue, UI/UX, and a11y. |
| ☁️ **cloud-infrastructure** | Specialist in Terraform/OpenTofu, AWS/GCP, and IaC security. |
| 📊 **sre-observability** | Focuses on Prometheus, Grafana, OpenTelemetry, and SLIs/SLOs. |

## 🔌 External Integrations (MCP)
- **Exa:** Secure web search for current information and news.
- **Context7:** Real-time documentation and code examples for libraries and frameworks.
- **GitHub:** Direct integration for managing issues, pull requests, and repository data.

## 💡 Usage Guidelines
To get the best results, you can prompt the agent either implicitly or explicitly:
- **Implicit:** *"Add a new Angular component for the dashboard."* (Agent loads `frontend-expert` automatically).
- **Explicit:** *"Act as my `cloud-infrastructure` expert and review this Terraform module."* (Forces specific mindset).

---
*This configuration is model-agnostic and designed to provide a consistent, secure, and high-velocity experience across any supported AI model.*
