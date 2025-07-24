---
description: Performs a code review on one or more files with a focus on software design principles and best practices
---

## Code Review for Correct Design

### 1. Identify Code and Gather Initial Context

1.  **Define Scope:**
    *   Confirm the specific file(s), class(es), or functions to be reviewed.
    *   If not provided, ask the user: "What specific code would you like me to review for correct design?"

2.  **Analyze Code and Dependencies:**
    *   Use the `view_file` tool to read the specified code.
    *   Trace any function or method calls within the code to their definitions, whether in the same file or other files. Use `grep_search` and `view_code_item` to understand the contracts (pre-conditions, post-conditions) and implementation details of these dependencies.

### 2. Clarify Business Purpose

1.  **Formulate Questions:**
    *   Based on the initial analysis, identify any ambiguities regarding the code's business logic or intended behavior.
    *   Ask the user targeted questions to resolve these ambiguities. For example: "I see the `processOrder` function handles payment verification and inventory updates. Is it also intended to send a confirmation email, or is that handled by a different service?"

### 3. Perform In-Depth Design Analysis

With the full context, analyze the code against common software design principles. Document any deviations as findings.

*   **SOLID Principles:**
    *   **Single Responsibility:** Does each class or method have one, and only one, reason to change?
    *   **Open/Closed:** Is the code open to extension but closed for modification?
    *   **Liskov Substitution:** Can subclasses be substituted for their base classes without altering the program's correctness?
    *   **Interface Segregation:** Are interfaces lean and specific to the client's needs?
    *   **Dependency Inversion:** Does the code depend on abstractions (e.g., interfaces) rather than concrete implementations?
*   **DRY (Don't Repeat Yourself):**
    *   Is there redundant or duplicated code that could be refactored into a single, reusable component?
*   **KISS (Keep It Simple, Stupid):**
    *   Is the solution overly complex? Could a simpler approach achieve the same goal effectively?
*   **Readability & Maintainability:**
    *   Are names for variables, functions, and classes clear and unambiguous?
    *   Is the control flow easy to follow?
*   **Testability:**
    *   Is the code structured in a way that makes it easy to unit test? Are dependencies managed in a way (e.g., via dependency injection) that allows for mocking?

### 4. Report Findings

1.  **Synthesize and Deliver the Review:**
    *   If there are findings, present them in a structured list. For each finding, provide:
        *   **Observation:** A clear and concise description of the design issue.
        *   **Impact:** An explanation of the potential negative consequences (e.g., "This tight coupling makes the class difficult to test in isolation.").
        *   **Suggestion:** A concrete, actionable recommendation for improvement, with code examples where appropriate.
    *   If no significant design issues are found, confirm that the code appears to be well-structured and adheres to the principles checked.