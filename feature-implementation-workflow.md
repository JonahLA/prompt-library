# Feature Implementation Workflow for Windsurf

This document outlines the workflow for implementing new features using Windsurf, an AI programming assistant tool.

## Overview

This workflow defines a repeatable process for implementing new features in a codebase. It specifies when Windsurf should act autonomously and when it should wait for developer input.

## Workflow Steps

### 1. Initial Feature Request Analysis

**Action**: Windsurf analyzes the feature request and codebase.

- Windsurf receives a feature request (which may vary in detail level)
- Windsurf analyzes the relevant parts of the codebase to understand the context
  - If the developer/ticket specifies it's a simple feature with sufficient context, Windsurf may perform a more limited analysis
- Windsurf identifies the files and components that will likely need modification

**Wait for Developer Input**: No (unless clarification is needed on ambiguous requirements)

### 2. Implementation Plan Creation

**Action**: Windsurf creates and presents an implementation plan.

- Windsurf creates a detailed implementation plan including:
  - Files to be modified
  - New files to be created
  - Changes to be made in each file
  - Any dependencies or considerations
  - Potential challenges or edge cases
- Windsurf presents this plan to the developer

**Wait for Developer Input**: Yes - Developer must approve the implementation plan before proceeding

### 3. Incremental Implementation

**Action**: Windsurf implements the feature in small, incremental changes.

- Windsurf implements the feature according to the approved plan
- Changes are made in small, manageable increments
- Each increment focuses on a specific part of the implementation
- Windsurf follows the documentation patterns described in the repository's Windsurf rules

**Wait for Developer Input**: Yes - After each increment, developer should review and approve before proceeding to the next increment

### 4. Testing Implementation (When Specified)

**Action**: Windsurf implements tests if specified in the requirements.

- If the feature request specifies that tests should be included, Windsurf will create appropriate tests
- Tests should follow the existing testing patterns in the codebase

**Wait for Developer Input**: Yes - Developer should review and approve the tests

### 5. Code Review and Verification

**Action**: Windsurf submits the implementation for review.

- Developer reviews the complete implementation
- Developer provides feedback on any issues or improvements
- After developer approval, Windsurf can run tests/checks to verify the implementation works as expected

**Wait for Developer Input**: Yes - Developer must review and approve the implementation

### 6. Commit Preparation

**Action**: Windsurf prepares commit messages following repository conventions.

- Windsurf follows the commit conventions described in the repository's Windsurf rules
- Windsurf suggests appropriate commit messages based on these conventions

**Wait for Developer Input**: Yes - Developer should approve the commit messages

### 7. Feedback Implementation

**Action**: Windsurf implements feedback from the developer.

- Windsurf makes revisions based on developer feedback
- Changes are made incrementally
- Each revision is presented to the developer for approval

**Wait for Developer Input**: Yes - Developer should review and approve each revision

## Conclusion

This workflow provides a structured approach to feature implementation using Windsurf. By following these steps, developers can leverage Windsurf's capabilities while maintaining control over the implementation process.
