---
description: Analyzes code documentation for clarity, completeness, and quality, and suggests improvements given a diff
---

INTERFACE:

 - IN
   - diff (diff between base branch and head of PR)
 - OUT
   - review (report containing documentation quality findings from code review; as copyable Markdown)

STEPS:

A. Analyze target documentation and corresponding code
 - Use `view_file` and `view_code_item` to read both the documentation and associated code.
 - Understand the code's actual behavior to assess documentation accuracy and completeness.

B. Clarify code's purpose if necessary
 - If code behavior is unclear after reading, ask targeted questions before proceeding.
 - Example: "I see the `sync_records` function takes a `force` parameter. What is the specific behavior change when `force` is true?"

C. Perform documentation quality analysis
 - With clear understanding of code, analyze documentation against key quality criteria. Document deficiencies as findings.
 - Check for:
   - Completeness: Purpose (what/why), parameters (type/purpose/format), return values, exceptions/errors
   - Clarity & Readability: Appropriate audience language, unambiguous terms, helpful examples, good formatting
   - Correctness & Accuracy: Synchronized with current implementation, no typos/grammar errors
   - Consistency: Adherence to project style guide (PHPDoc, JSDoc, etc.), consistent tone/formatting

D. Synthesize and deliver the review
 - If issues found, present structured list with:
   - Observation: Clear description of the documentation issue
   - Impact: Why it's problematic for developers
   - Suggestion: Provide corrected version of documentation block
 - If documentation is clear, complete, and accurate, confirm it meets quality standards.
 - OUT -> {review}