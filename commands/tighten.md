---
description: Systematically review source files to strengthen type safety and logic precision
agent: coder
---

Call the coder agent to perform a surgical refactor of the selected file or module.
The goal is to move from generic or loose types to strict, expressive definitions.
• Identify and replace "any", "interface{}", "void*", or dynamic types with concrete structures
• Check for null/nil safety and ensure proper error handling patterns
• Improve variable naming to reflect the specific data being held
• Minimize side effects by identifying opportunities for pure functions
• Ensure no runtime behavior is changed, only the quality of definitions
