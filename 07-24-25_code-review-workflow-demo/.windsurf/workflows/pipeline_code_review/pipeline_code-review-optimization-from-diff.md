---
description: Analyzes code to identify performance bottlenecks and suggests optimizations for improved resource utilization given a diff
---

INTERFACE:
 - IN
   - diff (diff between base branch and head of PR)
 - OUT
   - review (report containing performance optimization findings from code review; as copyable Markdown)

1. Analyze code and identify high-cost operations
 - Use `view_file` tool to read the specified code, focusing on resource-intensive sections.
 - Identify loops, I/O operations (database queries, network requests, file access), and memory allocation patterns using `grep_search` and `view_code_item`.

2. Clarify performance goals and context
 - Based on initial analysis, ask targeted questions about performance requirements and operational context.
 - Examples: "What are the performance goals - low latency or high throughput?", "What scale will this operate at?", "Is this in a memory-constrained environment?"

3. Perform performance bottleneck analysis
 - With full context, analyze code against common performance anti-patterns. Document any bottlenecks as findings.
 - Check for:
   - I/O Bottlenecks: N+1 query problems, inefficient data fetching, blocking operations
   - Algorithmic Inefficiencies: High complexity loops (O(n²)), redundant computation
   - Memory Issues: Large datasets in memory, inefficient data structures, object churn
   - Concurrency/Caching: Missed parallelism opportunities, cacheable expensive operations

4. Synthesize and deliver the review
 - If bottlenecks found, present structured list with:
   - Observation: Clear description of the performance issue
   - Impact: How it affects resource utilization or speed
   - Suggestion: Concrete optimization recommendation with code examples
   - Trade-offs: Brief mention of any trade-offs (e.g., memory vs latency)
 - If no issues found, confirm code appears reasonably optimized for its purpose.
 - OUT -> {review}