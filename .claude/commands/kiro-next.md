# Task Execution Command

### KIRO_COMMAND_NEXT
```
Executes the next uncompleted task from the tasks.md file with strict single-task focus and real-time progress tracking.

**Constraints:**
- The model MUST read .specs/project-info.md to load project context and information
- The model MUST read all SPECS documents (requirements.md, design.md, tasks.md) before execution
- The model MUST locate the next uncompleted task in the tasks.md file
- The model MUST execute only ONE task at a time, never multiple tasks
- The model MUST implement the task according to requirements and design specifications
- The model MUST update the task status in tasks.md in real-time during execution
- The model MUST stop and wait for user confirmation after completing each task
- The model MUST NOT automatically proceed to the next task without explicit user instruction
- The model MUST validate implementation against requirements specified in the task details
- The model MUST handle sub-tasks by starting with the first uncompleted sub-task
- The model MUST provide clear completion report showing what was accomplished
- The model MUST mark completed tasks with appropriate status indicators
- The model MUST preserve task progress and maintain task list integrity
- The model SHOULD recommend the next logical task if user asks for guidance
- The model SHOULD provide implementation details and reasoning during execution
- The model SHOULD verify task completion against acceptance criteria
- The model MAY ask for clarification if task requirements are ambiguous

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Task Execution Guidelines

### SPEC_TASK_PROMPT
```
Follow these instructions for user requests related to spec tasks. The user may ask to execute tasks or just ask general questions about the tasks.
## Executing Instructions
- Before executing any tasks, ALWAYS ensure you have read the specs requirements.md, design.md and tasks.md files. Executing tasks without the requirements or design will lead to inaccurate implementations.
- Look at the task details in the task list
- If the requested task has sub-tasks, always start with the sub tasks
- Only focus on ONE task at a time. Do not implement functionality for other tasks.
- Verify your implementation against any requirements specified in the task or its details.
- Once you complete the requested task, stop and let the user review. DO NOT just proceed to the next task in the list
- If the user doesn't specify which task they want to work on, look at the task list for that spec and make a recommendation
on the next task to execute.
Remember, it is VERY IMPORTANT that you only execute one task at a time. Once you finish a task, stop. Don't automatically continue to the next task without the user asking you to do so.
## Task Questions
The user may ask questions about tasks without wanting to execute them. Don't always start executing tasks in cases like this.
For example, the user may want to know what the next task is for a particular feature. In this case, just provide the information and don't start any tasks.
```

## Single Task Execution Rules

### Task Focus Constraint
**Constraints:**
- The model MUST execute only ONE task at a time
- The model MUST read all SPECS documents before starting any task
- The model MUST validate implementation against requirements
- The model MUST stop after completing each task and wait for user confirmation
- The model MUST NOT automatically proceed to next task

### Progress Tracking Rules
**Constraints:**
- The model MUST update task status in tasks.md in real-time
- The model MUST preserve completed task status
- The model MUST maintain task list integrity and hierarchy
- The model MUST provide clear completion reports
- The model MUST mark tasks with appropriate status indicators

### Task Selection Logic
**Constraints:**
- The model MUST locate next uncompleted task in task list
- The model MUST handle sub-tasks by starting with first uncompleted sub-task  
- The model SHOULD recommend next logical task if user asks for guidance
- The model MUST verify task completion against acceptance criteria