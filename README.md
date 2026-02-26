# OpenCode Configuration

This repository contains the personal OpenCode configuration. It defines a highly customized, multi-agent orchestration system designed for autonomous software development, code review, and system architecture.

## Project Overview

The core of this configuration revolves around a "Master Orchestrator" agent named **Wintermute**. Instead of executing tasks directly, Wintermute interprets user intent, plans workflows, and delegates tasks to specialized subagents (like `coder`, `architect`, and `reviewer`) using the `Task` tool. This setup enforces strict feedback loops (e.g., Coder -> Reviewer) and dynamic context management to ensure high-quality, production-ready code.

## Getting Started

To set up the environment and install necessary dependencies, run:

```bash
npm install
```

## Directory Structure

The configuration is modular and organized into several key directories:

### `agents/`
Defines the AI agents that power the system. Each agent is configured via a Markdown file with YAML frontmatter specifying its model, temperature, tools, and system prompt.
- **`wintermute.md`**: The default agent and Master Orchestrator. It classifies intent, discovers skills, and delegates work to subagents.
- **Subagents**: Specialized agents invoked by Wintermute, including:
  - `architect.md`: High-level design and architecture planning.
  - `coder.md`: Precision-focused coding support ("War Machine").
  - `debugger.md`: Investigating crashes and root-cause analysis.
  - `mentor.md`: Theoretical advice and code optimization.
  - `reviewer.md`: Security audits and code quality checks.
  - `researcher.md`: Documentation search and data gathering.

### `commands/`
Defines custom workflows and macros that orchestrate complex, multi-step processes.
- **`ask`**: Technical Consultation. The **Mentor** agent provides high-density technical advice and optimization alternatives.
- **`audit`**: Security & Compliance. The **Reviewer** agent performs a deep scan for vulnerabilities (OWASP Top 10) and credential leaks.
- **`blueprint`**: Architecture Mapping. The **Architect** agent scans the codebase to generate or update `ARCHITECTURE.md`.
- **`contract`**: DbC Documentation. The **Coder** agent rewrites docstrings to focus on "obligations and guarantees".
- **`design`**: System Architecture. The **Architect** agent creates a technical roadmap for new features and schema design.
- **`feature`**: Full Feature Lifecycle. **Wintermute** orchestrates a multi-agent loop: Architect (Design) -> Coder (Implementation) -> Reviewer (Audit).
- **`pre-mortem`**: Risk Identification. The **Architect** agent identifies future failure points and provides mitigation steps.
- **`ralph-loop`**: Rapid Iteration. The **Coder** agent executes a high-speed Intent -> Code -> Observe -> Correct loop.
- **`refactor`**: Safe Refactoring. **Wintermute** manages a Coder-Reviewer loop specifically for refactoring.
- **`tighten`**: Type & Logic Precision. The **Coder** agent performs surgical refactors to replace generic types with strict definitions.
- **`tokenscope`**: Token Usage Analysis. The **Coder** agent executes the `tokenscope` tool to provide a detailed breakdown of session token consumption.

### `skills/`
Contains domain-specific knowledge and workflows that Wintermute can dynamically load based on the task at hand.
- `backend-architect/`
- `cicd-automation/`
- `database-expert/`
- `devops-safety/`
- `security-auditor/`

## Core Configuration Files

### `opencode.jsonc`
The primary configuration file for the OpenCode environment.
- **Theme & Defaults**: Uses the `gruvbox` theme and sets `wintermute` as the default agent.
- **Permissions**: Implements fine-grained bash permissions. Sensitive operations (like reading `.env` or `.ssh`) require explicit user permission (`ask`), while standard development commands (git, docker, kubectl, npm) are allowed automatically. Specifically, `aws` commands (`describe-*`, `get-*`, `list-*`) are allowed, while `external_directory` and `doom_loop` require explicit permission.
- **Plugins**: Integrates `@ramtinj95/opencode-tokenscope` and `@tarquinen/opencode-dcp`.
- **MCP (Model Context Protocol)**: Configures external integrations:
  - `exa`: Remote web search capabilities.
  - `context7`: Remote documentation and code example querying.
  - `github`: Local GitHub integration for repository management.

### `dcp.jsonc`
Configures Dynamic Context Pruning (DCP) to manage the LLM's context window effectively.
- Enables deduplication, superseded writes removal, and error purging.
- Configures `pruneNotification` to "detailed" for better visibility into pruning actions.
- Grants the `distill` tool permission to compress conversation history, which Wintermute uses proactively after subagent tasks.
- Includes `nudge` settings to periodically remind the agent to prune context (every 10 turns).

## Environment Variables

The following environment variables are required for full functionality:

- `EXA_API_KEY`: Required for web search capabilities. Create at [https://dashboard.exa.ai/api-keys](https://dashboard.exa.ai/api-keys).
- `CONTEXT7_API_KEY`: Required for documentation and code example querying. Create at [https://context7.com/dashboard](https://context7.com/dashboard).
- `GITHUB_TOKEN`: Required for GitHub repository management. Create a Personal Access Token at [https://github.com/settings/tokens](https://github.com/settings/tokens).

## Extensibility

This system is designed to be highly extensible:
- **Adding Agents**: Create a new `.md` file in the `agents/` directory with the appropriate YAML frontmatter and system prompt.
- **Creating Workflows**: Add new commands in the `commands/` directory to define custom multi-agent orchestration loops.
- **Expanding Skills**: Add new domain-specific knowledge bases in the `skills/` directory for Wintermute to discover and load dynamically.
- **Integrating Tools**: Add new MCP servers in `opencode.jsonc` to provide agents with new capabilities (e.g., database access, cloud provider integrations).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
