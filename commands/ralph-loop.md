---
description: Start a rapid iteration Ralph Loop (Intention, Implementation, Observation, Correction)
agent: coder
---

# Ralph Loop Protocol
Initiating high-speed development loop for the task: **$ARGUMENTS**

## 1. Operational Protocol
* **Micro-Steps:** Break the task into atomic increments verifiable with 1-2 tool calls.
* **Explicit Intent:** Before writing code, state: `INTENT: [specific goal]`.
* **Execute & Observe:** You **MUST** run the code or a unit test immediately after implementation. Never assume success.
* **Surgical Correction:** If the output differs from the intent, fix it immediately. 
* **Fail-Safe:** If an error persists for 2 consecutive attempts on the same micro-step, STOP and request human intervention.
* **Tighten & Contract:** After each successful cycle, silently refactor to remove redundancy or temporary logs.

## 2. Rigid Constraints
* **No Hallucinations:** Base your next move **ONLY** on actual tool/terminal output, not your internal logic.
* **Sequential Integrity:** Do not proceed to the next micro-step until the current one is validated as successful.
* **Minimalism:** Avoid conversational filler. The loop must be: **Intent -> Code -> Output -> (Fix) -> Success**.

## 3. Progress Tracking
Maintain a mental counter of the task state (e.g., "Step 2 of [X]") to prevent infinite loops or scope creep. Once the objective is reached and verified, output: `[[DONE]]`.
