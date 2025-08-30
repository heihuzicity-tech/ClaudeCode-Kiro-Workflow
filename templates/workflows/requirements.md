# Requirements Workflow Templates

## Requirements Document Template

### SPEC_REQUIREMENTS_EXAMPLE
```md
# Requirements Document
## Introduction
[Introduction text here]
## Requirements
### Requirement 1
**User Story:** As a [role], I want [feature], so that [benefit]
#### Acceptance Criteria
This section should have EARS requirements
1. WHEN [event] THEN [system] SHALL [response]
2. IF [precondition] THEN [system] SHALL [response]
    
### Requirement 2
**User Story:** As a [role], I want [feature], so that [benefit]
#### Acceptance Criteria
1. WHEN [event] THEN [system] SHALL [response]
2. WHEN [event] AND [condition] THEN [system] SHALL [response]
```

### SPEC_WORKFLOW_REQUIREMENT_CLARIFICATION
```
### 1. Requirement Gathering
First, generate an initial set of requirements in EARS format based on the feature idea, then iterate with the user to refine them until they are complete and accurate.
Don't focus on code exploration in this phase. Instead, just focus on writing requirements which will later be turned into
a design.
**Constraints:**
- The model MUST create a '.specs/{feature_name}/requirements.md' file if it doesn't already exist
- The model MUST generate an initial version of the requirements document based on the user's rough idea WITHOUT asking sequential questions first
- The model MUST format the initial requirements.md document with:
  - A clear introduction section that summarizes the feature
  - A hierarchical numbered list of requirements where each contains:
    - A user story in the format "As a [role], I want [feature], so that [benefit]"
    - Acceptance criteria in EARS (Easy Approach to Requirements Syntax) format
- The model MUST proceed to the design phase after the user accepts the requirements
```