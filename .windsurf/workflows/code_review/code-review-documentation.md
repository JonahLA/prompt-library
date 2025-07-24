---
description: Analyzes code documentation for clarity, completeness, and quality, and suggests improvements.
---

## Documentation Code Review

### 1. Identify Target Documentation and Code

1.  **Define Scope:**
    *   Confirm the documentation to be reviewed. This could be docstrings within specific files, a class's public API documentation, or a README file.
    *   If not provided, ask the user: "What specific documentation would you like me to review?"

2.  **Analyze the Corresponding Code:**
    *   Use `view_file` and `view_code_item` to read the code associated with the documentation. A thorough understanding of the code's actual behavior is necessary to assess the documentation's accuracy and completeness.

### 2. Clarify Code's Purpose (If Necessary)

1.  **Formulate Questions:**
    *   If the code's purpose or behavior is not clear after reading it, you cannot effectively review its documentation.
    *   Ask clarifying questions before proceeding. For example: "I see the `sync_records` function takes a `force` parameter. What is the specific behavior change when `force` is true?"

### 3. Perform In-Depth Documentation Analysis

With a clear understanding of the code, analyze its documentation against key quality criteria. Document any deficiencies as findings.

*   **Completeness:**
    *   **Purpose:** Does the documentation clearly and concisely explain the *what* and *why* of the code? Does it describe the problem it solves?
    *   **Parameters/Arguments:** Are all parameters documented? For each, is the type, purpose, and expected format clear? Are optional vs. required parameters identified?
    *   **Return Values:** Is the return value described? Is its type and structure clear? What is returned in edge cases (e.g., on failure, or when nothing is found)?
    *   **Exceptions/Errors:** Does the documentation list the exceptions or errors that can be thrown and the conditions that cause them?

*   **Clarity and Readability:**
    *   **Audience:** Is the language appropriate for the intended audience (e.g., new developers, expert users)?
    *   **Ambiguity:** Is the language precise and unambiguous? Are there vague terms that could be misinterpreted?
    *   **Examples:** For complex functions or APIs, are there clear, correct, and easy-to-understand code examples?
    *   **Formatting:** Is the documentation well-formatted and easy to read?

*   **Correctness and Accuracy:**
    *   **Synchronization:** Does the documentation accurately reflect the code's current implementation? Check for outdated information, such as incorrect parameter names or descriptions of old behavior.
    *   **Typos and Grammar:** Is the documentation free of spelling and grammatical errors?

*   **Consistency:**
    *   **Style and Format:** Does the documentation adhere to the project's established style guide (e.g., PHPDoc, JSDoc, Google Style Guide)? Is the tone and formatting consistent with other documentation in the codebase?

### 4. Report Findings

1.  **Synthesize and Deliver the Review:**
    *   If issues are found, present them in a structured list. For each finding, provide:
        *   **Observation:** A clear description of the documentation issue (e.g., "The `@return` tag for the `getUser` function is missing.").
        *   **Impact:** An explanation of why it's a problem (e.g., "This leaves developers unsure of what data structure to expect in response.").
        *   **Suggestion:** Provide a corrected version of the documentation block.
    *   If the documentation is clear, complete, and accurate, confirm that it meets quality standards.