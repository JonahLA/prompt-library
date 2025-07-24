---
description: Conducts a code review on correct design given a diff
---

INTERFACE:
 - IN
   - diff (file diff between base branch and head of PR)
 - OUT
   - review (report containing findings from code review; as copyable Markdown)

1. Analyze code and dependencies
 - Use the `view_file` tool to read the specified code.
 - Trace any function or method calls within the code to their definitions, whether in the same file or other files. Use `grep_search` and `view_code_item` to understand the contracts (pre-conditions, post-conditions) and implementation details of these dependencies.

2. Clarify business purpose
 - Based on the initial analysis, identify any ambiguities regarding the code's business logic or intended behavior.
 - Ask the user targeted questions to resolve these ambiguities. For example: "I see the `processOrder` function handles payment verification and inventory updates. Is it also intended to send a confirmation email, or is that handled by a different service?"

3. Perform in-depth code analysis
 - With the full context, analyze the code against common software design principles. Document any deviations as findings.
 - Examples of principles to compare against:
   - SOLID Principles:
     - Single Responsibility
     - Open/Closed
     - Liskov Substitution
     - Interface Segregation
     - Dependency Inversion
     - DRY (Don't Repeat Yourself)
     - KISS (Keep It Simple, Stupid)
     - Readability & Maintainability
     - Testability

4. Synthesize and deliver the review
 - If there are findings, present them in a structured list. For each finding, provide:
   - Observation: A clear and concise description of the design issue.
   - Impact: An explanation of the potential negative consequences (e.g., "This tight coupling makes the class difficult to test in isolation.").
   - Suggestion: A concrete, actionable recommendation for improvement, with code examples where appropriate.
 - If no significant design issues are found, confirm that the code appears to be well-structured and adheres to the principles checked.
 - OUT -> {review}