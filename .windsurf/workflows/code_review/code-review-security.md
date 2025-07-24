---
description: Performs a code review with a focus on identifying and mitigating common security vulnerabilities.
---

## Security Code Review

### 1. Identify Code and Understand Data Flow

1.  **Define Scope:**
    *   Confirm the specific file(s), class(es), or functions to be reviewed.
    *   If not provided, ask the user: "What specific code would you like me to review for security vulnerabilities?"

2.  **Trace Data and Trust Boundaries:**
    *   Use `view_file`, `grep_search`, and `view_code_item` to analyze the code.
    *   Identify all sources of external input (e.g., HTTP request parameters, database results, API responses).
    *   Trace how this data is used, paying close attention to when it crosses a trust boundary (e.g., from user input to a database query).

### 2. Clarify Security Context and Assumptions

1.  **Formulate Questions:**
    *   Based on the initial analysis, ask clarifying questions about the security context.
    *   Examples:
        *   "What authorization level (e.g., anonymous user, authenticated user, admin) is required to execute this function?"
        *   "Is the data from `get_user_profile()` considered safe for direct display, or does it require output encoding?"
        *   "Are there any rate-limiting or throttling mechanisms in place for this endpoint?"

### 3. Perform In-Depth Security Analysis

With the full context, analyze the code for common security vulnerabilities. Document any weaknesses as findings.

*   **A1: Injection Flaws:**
    *   **SQL/NoSQL Injection:** Is user-supplied input used to construct database queries directly? (Look for string concatenation instead of parameterized queries/prepared statements).
    *   **Cross-Site Scripting (XSS):** Is untrusted data rendered in the UI without proper output encoding?
    *   **Command Injection:** Is user input passed directly to system shell commands?

*   **A2: Broken Authentication & Authorization:**
    *   **Missing Checks:** Are there missing or incorrect authorization checks to verify the user has the required permissions for an action?
    *   **Insecure Direct Object References (IDOR):** Can a user access or modify another user's data by simply changing an ID in a URL or parameter?
    *   **Hardcoded Credentials:** Are secrets like API keys, passwords, or tokens stored directly in the source code?

*   **A3: Sensitive Data Exposure:**
    *   **Data in Transit:** Is sensitive data transmitted over non-secure channels (e.g., HTTP instead of HTTPS)?
    *   **Data at Rest:** Is sensitive data (passwords, PII) stored without proper hashing or encryption?
    *   **Verbose Logging:** Are sensitive details like passwords, session tokens, or PII being written to logs?

*   **A4: Insecure Error Handling:**
    *   Do error messages reveal sensitive system information (e.g., stack traces, database errors, internal file paths) to the end-user?

*   **A5: Vulnerable & Outdated Components:**
    *   Are third-party libraries or dependencies being used that have known security vulnerabilities? (Check against `composer.lock`, `package-lock.json`, etc.).

### 4. Report Findings

1.  **Synthesize and Deliver the Review:**
    *   If vulnerabilities are found, present them in a structured list. For each finding, provide:
        *   **Observation:** A clear description of the vulnerability.
        *   **Impact/Risk:** An explanation of the potential security risk (e.g., "An attacker could exploit this to gain unauthorized access to user data.").
        *   **Suggestion:** A concrete, actionable recommendation for mitigation (e.g., "Replace the string-based query with a parameterized query to prevent SQL injection.").
    *   If no security issues are found, confirm that the code appears to follow security best practices for the areas analyzed.