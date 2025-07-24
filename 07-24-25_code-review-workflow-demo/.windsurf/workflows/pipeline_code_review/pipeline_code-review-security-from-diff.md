---
description: Conducts a code review on security given a diff
---

INTERFACE:

 - IN
   - diff (diff between base branch and head of PR)
 - OUT
   - review (report containing security findings from code review; as copyable Markdown)

STEPS:

A. Analyze code and trace data flow
 - Use `view_file` tool to read the specified code.
 - Trace external input sources (HTTP parameters, database results, API responses) and how data crosses trust boundaries using `grep_search` and `view_code_item`.

B. Clarify security context
 - Based on initial analysis, ask targeted questions about security assumptions.
 - Examples: "What authorization level is required for this function?", "Is data from this source considered safe for direct display?", "Are there rate-limiting mechanisms in place?"

C. Perform security vulnerability analysis
 - With full context, analyze code against common security vulnerabilities. Document any weaknesses as findings.
 - Check for:
   - Injection Flaws: SQL/NoSQL injection (string concatenation vs parameterized queries), XSS (unencoded output), command injection
   - Broken Authentication & Authorization: Missing permission checks, IDOR vulnerabilities, hardcoded credentials
   - Sensitive Data Exposure: Insecure transmission/storage, verbose logging of sensitive data
   - Insecure Error Handling: Error messages revealing system information
   - Vulnerable Components: Outdated dependencies with known vulnerabilities

D. Synthesize and deliver the review
 - If vulnerabilities found, present structured list with:
   - Observation: Clear description of the vulnerability
   - Impact/Risk: Explanation of potential security consequences
   - Suggestion: Concrete, actionable mitigation recommendation
 - If no issues found, confirm code follows security best practices for analyzed areas.
 - OUT -> {review}