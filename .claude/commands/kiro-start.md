# Feature Initialization Command

### KIRO_COMMAND_START
```
Initiates a new feature development workflow with automated safety checks, database backup, Git branch creation, and comprehensive document generation including requirements, design, and tasks.

**Constraints:**
- The model MUST perform safety checks and load project context before starting
- The model MUST detect database configurations and offer backup options
- The model MUST create a new feature branch with format `feature/[name]`
- The model MUST ensure Git working directory is clean before branch creation
- The model MUST create a '.specs/{feature_name}/' directory structure
- The model MUST create requirements.md, design.md, and tasks.md files in the feature directory
- The model MUST follow the complete workflow from requirements gathering through task planning
- The model MUST execute database backup immediately if database configuration is detected
- The model MUST ask user for confirmation if no database configuration is detected
- The model MUST request user approval before proceeding between workflow phases
- The model MUST NOT proceed to next phase without explicit user approval
- The model SHOULD detect existing project configurations and context
- The model SHOULD provide clear feedback about each setup step being performed
- The model MAY ask for clarification about feature scope during initial setup

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Requirements Workflow Integration

### SUPERCLAUDE_EXPERT_ENHANCEMENT
```
**Expert Enhancement Engine** - Embedded SuperClaude Framework Integration
After requirements confirmation, internally activate domain experts to enhance document quality and professional completeness:

**Enhancement Timing**: AFTER user confirms final requirements, BEFORE document generation
**User Experience**: Transparent to user - Kiro appears more professional, no direct expert interaction
**Expert Role**: Backend quality enhancement, not frontend requirement discovery

**Available Experts for Document Enhancement:**
- **requirements-analyst**: Review requirement completeness and clarity
- **system-architect**: Validate architectural feasibility and scalability
- **security-engineer**: Identify security gaps and compliance requirements
- **frontend-architect**: Review UI/UX requirement completeness
- **backend-architect**: Validate data integrity and API design requirements
- **quality-engineer**: Enhance testing strategy and quality criteria

**Enhancement Process:**
1. **Internal Analysis**: Kiro analyzes confirmed requirements for expert selection
2. **Silent Consultation**: Embed expert instructions without user awareness
3. **Quality Enhancement**: Expert reviews confirmed requirements for gaps and improvements
4. **Kiro Integration**: Kiro filters and integrates expert suggestions appropriately
5. **Enhanced Documentation**: Generate professional-quality requirements document

**Expert Instruction Constraint:**
You are acting as a [expert-type] providing backend quality enhancement for confirmed user requirements.
CRITICAL CONSTRAINTS:
- DO NOT redefine or expand the user's confirmed requirements scope
- DO NOT add features beyond user's explicit needs
- FOCUS ON: gap identification, risk assessment, quality improvement
- OUTPUT: Professional suggestions for enhancing existing requirements
- MAINTAIN: User's intended complexity level and scope boundaries

Based on these confirmed user requirements: [insert user's final requirements]
Provide quality enhancement suggestions that improve completeness without scope expansion.
```

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
### 1. Traditional Kiro Requirement Gathering with Backend Expert Enhancement
Follow the traditional Kiro workflow for requirement discussion and clarification. After user confirms final requirements, internally enhance document quality using relevant SuperClaude experts.

**Phase 1: Standard Kiro Requirements Discussion**
- Generate initial requirements based on user's feature request
- Iterate with user through traditional Kiro discussion process
- Focus on understanding user's actual needs and scope preferences
- Continue until user explicitly confirms the final requirements

**Phase 2: Silent Expert Enhancement (Must Execute)**
- After user confirms requirements, EXECUTE the following steps:
- ANALYZE confirmed requirements to identify primary domain (auth/frontend/backend/data/security)
- SELECT 1-2 most relevant experts from: requirements-analyst, system-architect, security-engineer, frontend-architect, backend-architect, quality-engineer
- USE Task tool to invoke selected expert with this exact instruction format:
  "You are acting as [expert-type] providing quality enhancement for these confirmed user requirements: [insert exact user requirements]. CRITICAL CONSTRAINTS: DO NOT expand scope or add features. ONLY provide enhancement suggestions for completeness, quality, and professional best practices within the existing scope. Focus on gap identification and risk assessment."
- INTEGRATE expert suggestions that enhance quality without scope expansion
- PROCEED to Phase 3 with expert-enhanced requirements

**Phase 3: Enhanced Requirements Generation**
Don't focus on code exploration in this phase. Generate requirements document incorporating expert enhancement suggestions while maintaining user's confirmed scope exactly.

**Constraints:**
- The model MUST create a '.specs/{feature_name}/requirements.md' file if it doesn't already exist
- The model MUST follow traditional Kiro requirement discussion process FIRST
- The model MUST NOT introduce expert consultation during user discussion phase
- The model MUST obtain user confirmation of final requirements BEFORE expert enhancement
- The model MUST EXECUTE Phase 2 expert enhancement using Task tool after user confirmation
- The model MUST use Task tool with exact instruction format specified in Phase 2
- The model MUST constrain expert analysis to enhancement, not scope expansion
- The model MUST generate the requirements document with expert-enhanced quality
- The model MUST format the initial requirements.md document with:
  - A clear introduction section that summarizes the feature
  - A hierarchical numbered list of requirements where each contains:
    - A user story in the format "As a [role], I want [feature], so that [benefit]"
    - Acceptance criteria in EARS (Easy Approach to Requirements Syntax) format
  - Quality enhancements from expert analysis (seamlessly integrated)
- The model MUST proceed to the design phase after generating the enhanced requirements document
```

## Design Workflow Integration

### SPEC_WORKFLOW_DESIGN_TEMPLATE
```
  - Overview
  - Architecture
  - Components and Interfaces
  - Data Models
  - Error Handling
  - Testing Strategy
```

### SPEC_WORKFLOW_RESEARCH_DESIGN
```
### 2. Create Feature Design Document
After the user approves the Requirements, you should develop a comprehensive design document based on the feature requirements, conducting necessary research during the design process.
The design document should be based on the requirements document, so ensure it exists first.
**Constraints:**
- The model MUST create a '.specs/{feature_name}/design.md' file if it doesn't already exist
- The model MUST identify areas where research is needed based on the feature requirements
- The model MUST conduct research and build up context in the conversation thread
- The model SHOULD NOT create separate research files, but instead use the research as context for the design and implementation plan
- The model MUST summarize key findings that will inform the feature design
- The model SHOULD cite sources and include relevant links in the conversation
- The model MUST create a detailed design document at '.specs/{feature_name}/design.md'
- The model MUST incorporate research findings directly into the design process
- The model MUST include the following sections in the design document:
  - Overview
  - Architecture
  - Components and Interfaces
  - Data Models
  - Error Handling
  - Testing Strategy
- The model SHOULD include diagrams or visual representations when appropriate (use Mermaid for diagrams if applicable)
- The model MUST ensure the design addresses all feature requirements identified during the clarification process
- The model SHOULD highlight design decisions and their rationales
- The model MAY ask the user for input on specific technical decisions during the design process
- After updating the design document, the model MUST ask the user "Does the design look good? If so, we can move on to the implementation plan." using the 'userInput' tool.
- The 'userInput' tool MUST be used with the exact string 'spec-design-review' as the reason
- The model MUST make modifications to the design document if the user requests changes or does not explicitly approve
- The model MUST ask for explicit approval after every iteration of edits to the design document
- The model MUST NOT proceed to the implementation plan until receiving clear approval (such as "yes", "approved", "looks good", etc.)
- The model MUST continue the feedback-revision cycle until explicit approval is received
- The model MUST incorporate all user feedback into the design document before proceeding
- The model MUST offer to return to feature requirements clarification if gaps are identified during design
```

## Tasks Workflow Integration

### SPEC_WORKFLOW_IMPLEMENTATION_PLAN
```
### 3. Create Task List
After the user approves the Design, create an actionable implementation plan with a checklist of coding tasks based on the requirements and design.
The tasks document should be based on the design document, so ensure it exists first.
**Constraints:**
- The model MUST create a '.specs/{feature_name}/tasks.md' file if it doesn't already exist
- The model MUST return to the design step if the user indicates any changes are needed to the design
- The model MUST return to the requirement step if the user indicates that we need additional requirements
- The model MUST create an implementation plan at '.specs/{feature_name}/tasks.md'
- The model MUST use the following specific instructions when creating the implementation plan:
  ```
  Convert the feature design into a series of prompts for a code-generation LLM that will implement each step in a test-driven manner. Prioritize best practices, incremental progress, and early testing, ensuring no big jumps in complexity at any stage. Make sure that each prompt builds on the previous prompts, and ends with wiring things together. There should be no hanging or orphaned code that isn't integrated into a previous step. Focus ONLY on tasks that involve writing, modifying, or testing code.
  ```
- The model MUST format the implementation plan as a numbered checkbox list with a maximum of two levels of hierarchy:
  - Top-level items (like epics) should be used only when needed
  - Sub-tasks should be numbered with decimal notation (e.g., 1.1, 1.2, 2.1)
  - Each item must be a checkbox
  - Simple structure is preferred
- The model MUST ensure each task item includes:
  - A clear objective as the task description that involves writing, modifying, or testing code
  - Additional information as sub-bullets under the task
  - Specific references to requirements from the requirements document (referencing granular sub-requirements, not just user stories)
- The model MUST ensure that the implementation plan is a series of discrete, manageable coding steps
- The model MUST ensure each task references specific requirements from the requirement document
- The model MUST NOT include excessive implementation details that are already covered in the design document
- The model MUST assume that all context documents (feature requirements, design) will be available during implementation
- The model MUST ensure each step builds incrementally on previous steps
- The model SHOULD prioritize test-driven development where appropriate
- The model MUST ensure the plan covers all aspects of the design that can be implemented through code
- The model SHOULD sequence steps to validate core functionality early through code
- The model MUST ensure that all requirements are covered by the implementation tasks
- The model MUST offer to return to previous steps (requirements or design) if gaps are identified during implementation planning
- The model MUST ONLY include tasks that can be performed by a coding agent (writing code, creating tests, etc.)
- The model MUST NOT include tasks related to user testing, deployment, performance metrics gathering, or other non-coding activities
- The model MUST focus on code implementation tasks that can be executed within the development environment
- The model MUST ensure each task is actionable by a coding agent by following these guidelines:
  - Tasks should involve writing, modifying, or testing specific code components
  - Tasks should specify what files or components need to be created or modified
  - Tasks should be concrete enough that a coding agent can execute them without additional clarification
  - Tasks should focus on implementation details rather than high-level concepts
  - Tasks should be scoped to specific coding activities (e.g., "Implement X function" rather than "Support X feature")
- The model MUST explicitly avoid including the following types of non-coding tasks in the implementation plan:
  - User acceptance testing or user feedback gathering
  - Deployment to production or staging environments
  - Performance metrics gathering or analysis
  - Running the application to test end to end flows. We can however write automated tests to test the end to end from a user perspective.
  - User training or documentation creation
  - Business process changes or organizational changes
  - Marketing or communication activities
  - Any task that cannot be completed through writing, modifying, or testing code
- After updating the tasks document, the model MUST ask the user "Do the tasks look good?" using the 'userInput' tool.
- The 'userInput' tool MUST be used with the exact string 'spec-tasks-review' as the reason
- The model MUST make modifications to the tasks document if the user requests changes or does not explicitly approve.
- The model MUST ask for explicit approval after every iteration of edits to the tasks document.
- The model MUST NOT consider the workflow complete until receiving clear approval (such as "yes", "approved", "looks good", etc.).
- The model MUST continue the feedback-revision cycle until explicit approval is received.
- The model MUST stop once the task document has been approved.
**This workflow is ONLY for creating design and planning artifacts. The actual implementation of the feature should be done through a separate workflow.**
- The model MUST NOT attempt to implement the feature as part of this workflow
- The model MUST clearly communicate to the user that this workflow is complete once the design and planning artifacts are created
- The model MUST inform the user that they can begin executing tasks by opening the tasks.md file, and clicking "Start task" next to task items.
```

### SPEC_WORKFLOW_EXAMPLE_PLAN
```markdown
# Implementation Plan
- [ ] 1. Set up project structure and core interfaces
   - Create directory structure for models, services, repositories, and API components
   - Define interfaces that establish system boundaries
   - _Requirements: 1.1_
- [ ] 2. Implement data models and validation
  - [ ] 2.1 Create core data model interfaces and types
    - Write TypeScript interfaces for all data models
    - Implement validation functions for data integrity
    - _Requirements: 2.1, 3.3, 1.2_
  - [ ] 2.2 Implement User model with validation
    - Write User class with validation methods
    - Create unit tests for User model validation
    - _Requirements: 1.2_
  - [ ] 2.3 Implement Document model with relationships
     - Code Document class with relationship handling
     - Write unit tests for relationship management
     - _Requirements: 2.1, 3.3, 1.2_
- [ ] 3. Create storage mechanism
  - [ ] 3.1 Implement database connection utilities
     - _Requirements: 4.3_
[Additional coding tasks continue...]
```

## Workflow State Rules

### INITIAL_RULE
```
Focus on creating a new spec file or identifying an existing spec to update. 
If starting a new spec, create a requirements.md file in the .specs directory with clear user stories and acceptance criteria. 
If working with an existing spec, review the current requirements and suggest improvements if needed. 
Do not make direct code changes yet. First establish or review the spec file that will guide our implementation.
```

### REQUIREMENTS_RULE
```
You are working on the requirements document. Ask the user to review the requirements and confirm if they are complete. 
Make sure the requirements include clear user stories and acceptance criteria in EARS format. 
Once approved, proceed to the design phase by creating or updating a design.md file that outlines the technical approach, 
architecture, data models, and component structure.
```

### DESIGN_RULE
```
You are working on the design document. Ask the user to review the design and confirm if it meets their expectations. 
Ensure the design addresses all the requirements specified in the requirements document. 
Once approved, proceed to create or update a tasks.md file with specific implementation tasks broken down into manageable steps.
```

### IMPLEMENTATION_PLAN_RULE
```
You are working on the implementation plan. Ask the user to review the plan and confirm if it covers all necessary tasks. 
Ensure each task is actionable, references specific requirements, and focuses only on coding activities. 
Once approved, inform the user that the spec is complete and they can begin implementing the tasks by opening the tasks.md file.
```