# Implicit Rules

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