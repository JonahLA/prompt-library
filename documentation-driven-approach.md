# A Documentation-Driven Approach to AI-Assisted Development

_Link to documentation: [A Documentation-Driven Approach to AI-Assisted Development](https://docs.google.com/document/d/1mdeYFfLPCy2eI1Sn9hvlhegZwCqOF2lzmh0XYZQEonE/edit?tab=t.swegtyrmvltx)_

## Stage 1: Feature Requirements document

```md
I have uploaded my Design Doc that contains a full description of the feature I need to build. Ask me questions if there is anything that is unclear and then once you fully understand what we need to build, give me a concise description of the requirements in markdown format and save it to /docs/feature-requirements.md.

These are the features you will include:
- Specific user workflows and expected behaviors
- Clear success criteria and acceptance tests
- Explicit decisions about edge cases and error handling
- Dependencies on other systems or features
```

## Stage 2: Technical Architecture document

```md
Look at /docs/feature-requirements.md to understand the requirements of the feature we will be building and then examine the architecture of [point to a similar existing implementation in the codebase]. Consider the architectural decisions that need to be made to fully build this feature and then ask me questions when there is a choice to be made. Once we have a full understanding of the architectural needs for this feature, create a document /docs/feature-architecture.md that contains our decisions.
```

## Stage 3: Implementation Plan document

```md
Look at /docs/feature-requirements.md and /docs/feature-architecture.md and create a detailed step-by-step implementation plan we can use to fully build this feature. Each step should have a status field we can use to track our progress. Save this file as /docs/feature-implementation.md
```

## Implementation workflow

```md
1. Look at the given implementation file
2. Mark the given phase and step as "in progress"
3. Start implementing the given step
4. Once complete, mark the step as complete
5. Stop and ask for direction
```

**Example usage:** `/implement @feature-implementation.md Phase 1, step 1`

## Commit/push workflow

```md
1. Check the git status
2. Add files related to the work that has been done
3. Commit with a meaningful commit message
4. Push to remote
```

**Example usage:** `/push`
