---
description: Document functions based on the Design by Contract (DbC) principle
agent: coder
---

Call the coder agent to rewrite documentation strings for the current file.
Avoid stating "what" the code does; instead, document the "obligations" and "guarantees".
• Pre-conditions: What must be true before calling (e.g., "id must be > 0")
• Post-conditions: What is guaranteed to be true after (e.g., "returns a non-null object")
• Invariants: What remains unchanged during execution
• Exceptions: Document exactly which errors are thrown and why
• Use the standard documentation format for the detected language (JSDoc, Go Doc, Doxygen, etc.)
