# /kiro-next - Execute Next Task

## Triggers
- Continue task execution in SPECS workflow
- Resume development after breaks
- Progress to next implementation step

## Usage
```
/kiro-next
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Check current progress in tasks.md
2. Find next uncompleted task
   - Identify next task from tasks.md
   - Recommend if user doesn't specify
3. Execute with reference to requirements/design
   - Execute only ONE task at a time
   - Verify implementation against task requirements
4. Update task status immediately
   - Mark task progress in real-time
   - NOT mark completed until: code implemented, functionality tested, user confirms
5. Stop after task and wait for user instruction
   - NOT automatically proceed to next task
   - Provide clear completion reports

## Tool Coordination
- **Read**: Load SPECS documents as needed
- **Edit/Write**: Implement code changes
- **TodoWrite**: Update task status
- **Bash**: Run tests or commands

## Key Patterns
- **Single Task**: Execute only ONE task at a time
- **Status Tracking**: Real-time updates to tasks.md
- **User Review**: Mandatory review after each task

## Boundaries

**Will:**
- Execute one task at a time
- Update progress immediately
- Wait for user confirmation

**Will Not:**
- Execute multiple tasks automatically
- Skip task dependencies
- Modify task list during execution
- Proceed without user review