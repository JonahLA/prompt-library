---
description: README for code review workflows
---

## Purpose

These workflows are for having Windsurf perform a targeted code review on your code. They cover a few types of reviews:
 - on _code design patterns/principles_
 - on _documentation_
 - on _optimization_
 - on _security_

They are formatted using an experimental "pipeline" format which defines IN and OUT variables. These workflows are named with the prefix `pipeline_*` so that the `workflow-pipeline-standards.md` rule is applied when the workflow is ran. That rule gives Windsurf context on how to use pipeline workflows.

## Usage

These workflows are designed to be used in a pipeline where the output of one workflow/process is the input to another one. In this case, the `pipeline_get-diff-for-pr.md` workflow instructs Windsurf on how to calculate a file diff for a PR given the PR's branch name. That workflow's output can be used as an input to any of the other code review workflows which each expect a file diff as input.

The workflows can be used like:

```bash
/pipeline_get-diff-for-pr /pipeline_code-review-design-from-diff branchName: {name/of/branch}
```

Or more simply:


```bash
/pipeline_get-diff-for-pr /pipeline_code-review-design-from-diff
```

If no branch name is provided, then the `workflow-pipeline-standards.md` rule _should_ make Windsurf ask you for the branch name before proceeding.