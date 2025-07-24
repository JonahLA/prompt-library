---
trigger: glob
description: When using any pipeline-based workflow (i.e., a workflow with IN/OUT formatting)
globs: **/.windsurf/workflows/**/pipeline_*.md
---

- Pipeline workflows begin with a definition of the interface (i.e., what the workflow expects as input and what it will output).
- Before starting the first step in each workflow, ensure all of the IN values have been given by the user.
  - IN values may be provided in the prompt or provided as the OUT of a previous workflow.
  - If any IN values are missing or unclear, ask the user to provide those IN values (e.g., "This workflow requires 'branchName'. Can you please provide that for me?").