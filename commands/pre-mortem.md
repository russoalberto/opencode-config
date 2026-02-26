---
description: Identify architectural failure points before they happen (Prospective Hindsight)
agent: architect
---

Call the architect agent to challenge the current design or proposed feature.
Assume the project has failed 6 months from now; identify the technical reasons.
• Analyze scalability bottlenecks (e.g., O(n²) operations, database locks)
• Identify security risks (e.g., injection points, broken access control)
• Evaluate "Bus Factor" and maintainability (e.g., code that is too clever/complex)
• Check for dependency lock-in or outdated library risks
• Output a list of [MITIGATION] steps for each identified failure modefore including it in the report.
