---
description: Orchestrate a full feature lifecycle (Architect -> Coder -> Reviewer)
agent: wintermute
---

# Feature Lifecycle Protocol
Initiating full feature development for: **$ARGUMENTS**

## 1. Architecture Phase
* Delegate to the `architect` to design the feature, update `ARCHITECTURE.md`, and define the data models.
* Wait for the `architect` to complete the design.

## 2. Implementation Phase
* Delegate to the `coder` to implement the feature based on the `architect`'s design.
* The `coder` must write tests and ensure the code compiles/runs.

## 3. Review Phase
* Delegate to the `reviewer` to audit the `coder`'s implementation.
* If the `reviewer` finds [CRITICAL] or [MAJOR] issues, send the feedback back to the `coder` for fixes.
* Repeat the Coder -> Reviewer loop until the `reviewer` approves with "LGTM - Ready for merge".

## 4. Context Management
* Use the `distill` tool after each phase to compress the context and maintain focus.
