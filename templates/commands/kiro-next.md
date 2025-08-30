# Kiro Next Command Template

### KIRO_COMMAND_NEXT
```
Executes the next uncompleted task from the tasks.md file with strict single-task focus and real-time progress tracking.

**Constraints:**
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
- The model MUST follow the single-task execution principle from SPEC_TASK_PROMPT
- The model SHOULD recommend the next logical task if user asks for guidance
- The model SHOULD provide implementation details and reasoning during execution
- The model SHOULD verify task completion against acceptance criteria
- The model MAY ask for clarification if task requirements are ambiguous
```