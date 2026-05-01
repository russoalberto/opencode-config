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

### 4. Token-Optimized Commands (RTK)
The RTK plugin rewrites all Bash commands to token-efficient equivalents, compressing output without changing behavior.

- **Transparent Rewriting:** Every Bash command is automatically rewritten — e.g., `git status` -> `rtk git status` — producing compact output.
- **Risk-Based Permissions:** Read-only and lint/check subcommands are pre-approved. Destructive proxies (`rtk docker`, `rtk git`, `rtk aws`, `rtk run`, etc.) require manual approval, mirroring the security model for native commands.
- **Savings Tracking:** `rtk gain` shows cumulative token savings; `rtk session` shows session-level adoption.

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

> **Note:** `systematic-debugging`, `test-driven-development`, and `verification-before-completion` are now served by the superpowers plugin (see `opencode.jsonc` plugins) and no longer need separate skill installs.

### Skills from [skills.sh](https://skills.sh/)
Additional battle-tested skills installed from the open agent skills ecosystem:

| Skill | Source | Description |
| :--- | :--- | :--- |
| 🗂️ **find-skills** | skills.sh | Discover and install agent skills from the open ecosystem. |
| 📐 **terraform-style-guide** | hashicorp/agent-skills (2.9K installs) | Official HashiCorp Terraform HCL style conventions and code generation patterns. |
| ☸️ **k8s-manifest-generator** | wshobson/agents (30.6K installs) | Production-ready Kubernetes manifests (Deployments, Services, ConfigMaps, Secrets). |
| 🔗 **api-design-principles** | wshobson/agents (15.3K installs) | REST and GraphQL API design patterns, versioning, error handling, and DataLoaders. |

### Caveman Skills
Token-optimized communication skills for ultra-compressed agent interaction, installed from `skill://caveman`:

| Skill | Description |
| :--- | :--- |
| 🦴 **caveman** | Ultra-compressed communication mode (~75% token reduction). Supports `lite`, `full`, `ultra`, and `wenyan` intensities. |
| 📝 **caveman-commit** | Ultra-compressed Conventional Commits (subject ≤50 chars). Auto-triggers on staging changes. |
| ℹ️ **caveman-help** | Quick-reference card for all caveman modes, skills, and commands. |
| 📊 **caveman-stats** | Real token usage and estimated savings for the current session. Reads from Claude Code session log. |

**Install commands:**
```bash
npx -y skills add JuliusBrussee/caveman -a opencode
npx -y skills add vercel-labs/skills@find-skills -g -y
npx skills add hashicorp/agent-skills@terraform-style-guide -g -y
npx skills add wshobson/agents@k8s-manifest-generator -g -y
npx skills add wshobson/agents@api-design-principles -g -y
```

## 🔌 External Integrations (MCP)
- **Exa:** Secure web search for current information and news.
- **Context7:** Real-time documentation and code examples for libraries and frameworks.
- **GitHub:** Direct integration for managing issues, pull requests, and repository data.

## 🧹 Context Management (DCP)
This configuration includes **Dynamic Context Pruning (DCP)** to maintain optimal context window usage:
- Automatically compresses older conversation turns
- Protects MCP tool outputs and recent (5-turn) history
- Model-specific context limits for optimal performance
- Configured in `dcp.jsonc`

## 🔌 Plugin System

Plugins extend opencode's core functionality. Configured under `plugin` in `opencode.jsonc`:

| Plugin | Source | Purpose |
| :--- | :--- | :--- |
| 🧠 **DCP** | `@tarquinen/opencode-dcp` | Dynamic Context Pruning — auto-compresses stale conversation turns to maintain context window budget. Configured in `dcp.jsonc`. |
| ⚡ **Superpowers** | `obra/superpowers` | Skill-based workflow system providing structured processes for brainstorming, TDD, systematic debugging, code review, plan writing, and more. See `@skills/` and `AGENTS.md`. |
| 🗜️ **RTK** | opencode-bundled | Reduced Token Kernel — rewrites bash commands for token-efficient output. Transparent `rtk` proxy with automatic compression of shell output. |

## ✅ Validation
```bash
# Check opencode configuration
opencode config validate

# Verify skills installations
npx skills check
```

## 🐛 Troubleshooting
- **Skills not loading:** Run `npx skills check` to verify installations, then `npx skills update` to refresh.
- **MCP errors:** Ensure `EXA_API_KEY`, `CONTEXT7_API_KEY`, and `GITHUB_TOKEN` are set in your environment.
- **Context issues:** DCP automatically manages context; check `dcp.jsonc` for tuning.
- **Permission errors:** Check `opencode.jsonc` bash section for `allow`/`ask` patterns.

## 💡 Usage Guidelines
To get the best results, you can prompt the agent either implicitly or explicitly:
- **Implicit:** *"Add a new Angular component for the dashboard."* (Agent loads `frontend-expert` automatically).
- **Explicit:** *"Act as my `cloud-infrastructure` expert and review this Terraform module."* (Forces specific mindset).

---
*This configuration is model-agnostic and designed to provide a consistent, secure, and high-velocity experience across any supported AI model.*
