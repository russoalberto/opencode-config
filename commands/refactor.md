---
description: Orchestrate a safe refactoring loop (Coder -> Reviewer)
agent: wintermute
---

# Refactoring Protocol
Initiating safe refactoring for: **$ARGUMENTS**

## 1. Implementation Phase
* Delegate to the `coder` to perform the requested refactoring.
* The `coder` must ensure no runtime behavior is changed and all tests pass.

## 2. Review Phase
* Delegate to the `reviewer` to audit the refactored code for regressions, performance bottlenecks, and style consistency.
* If issues are found, loop back to the `coder`.
* Conclude only when the `reviewer` approves.

## 3. Context Management
* Use the `distill` tool to summarize the changes made and keep the context clean.
