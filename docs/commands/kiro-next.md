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
1. Load current tasks.md and progress
   - Read requirements.md, design.md and tasks.md before executing
2. Find next uncompleted task
   - Identify next task from tasks.md
   - Recommend if user doesn't specify
3. Execute with reference to requirements/design
   - Execute only ONE task at a time
   - Verify implementation against task requirements
   - **Script Execution Rule**: ALWAYS use bash/sh scripts, NEVER use bat/ps1/PowerShell
   - **Port Conflict Rule**: When port conflict detected, ASK user to kill conflicting process FIRST, NEVER change service port
   - **Service Management Rule**: ALWAYS use existing service management scripts (npm scripts, make, etc.) NOT direct commands
   - **Automatic file placement**:
     - Test scripts → `.specs/{feature}/scripts/` (automatic, must be .sh NOT .bat/.ps1)
     - Documentation → `.specs/{feature}/docs/` (automatic)
     - Temporary/debug files → `.specs/{feature}/artifacts/temp/` (automatic)
     - Test code → `.specs/{feature}/tests/` by default
     - **Exception**: Unit/integration tests that must integrate with test framework → `/tests/`
     - **Only ask when**: Technical requirement forces different location (explain why)
4. Update task status immediately
   - Mark task progress in real-time
   - NOT mark completed until: code implemented, functionality tested, user confirms
5. **Auto-update session progress** (lightweight)
   - Update only task progress in `.specs/session.md`
   - Do NOT overwrite entire session file
   - Only update: current task, completion status, timestamp
   - This ensures session stays current without manual /kiro-save
6. Stop after task and wait for user instruction
   - NOT automatically proceed to next task
   - Provide clear completion reports

## Tool Coordination
- **Read**: Load SPECS documents and session.md
- **Edit/Write**: Implement code changes
- **Edit**: Update session.md task progress (lightweight)
- **TodoWrite**: Update task status
- **Bash**: Run tests or commands (MUST use bash/sh, NOT PowerShell/bat)

## Session Auto-Update Strategy
When task completes successfully:
```markdown
# Only update these lines in session.md:
**Updated**: [new_timestamp]

## Task Progress
- [x] Task 1.1 - Description
- [x] Task 1.2 - Description  
- [x] Task 1.3 - Description (just completed) ← Update this
- [ ] Task 1.4 - Description (next)

## Current Task
**Latest**: Completed task 1.3 at [timestamp]
```

## Key Patterns
- **Single Task**: Execute only ONE task at a time
- **Status Tracking**: Real-time updates to tasks.md and session.md
- **Auto-Save Progress**: Lightweight session updates on task completion
- **User Review**: Mandatory review after each task
- **Reference Docs**: Always check requirements and design
- **Auto Directory**: Use `.specs/{feature}/` automatically, only deviate when necessary
- **Bash Priority**: MUST use bash/shell scripts for ALL testing and scripting, NOT bat/ps1/PowerShell
- **Port Conflicts**: ASK user to kill process when port conflict, NEVER auto-change ports
- **Service Scripts**: Use package.json scripts, Makefile, etc. NOT raw commands (npm run dev NOT node server.js)
- **Chinese Interaction**: All user communication must be in Chinese

## Boundaries

**Will:**
- Execute one task at a time
- Update progress immediately
- Reference SPECS documents
- Wait for user confirmation

**Will Not:**
- Execute multiple tasks automatically
- Skip task dependencies
- Modify task list during execution
- Proceed without user review
- Change service ports when conflicts occur
- Use direct commands when scripts exist

## Execution Examples

### Port Conflict Handling
```bash
# WRONG - Automatically changing port
Error: Port 3000 is already in use
Changing to port 3001...

# CORRECT - Ask user first
Error: Port 3000 is already in use by process PID 12345
Would you like to kill this process? (yes/no)
```

### Service Management
```bash
# WRONG - Using direct command
node server.js
python app.py
java -jar application.jar

# CORRECT - Using management scripts
npm run dev        # when package.json has "dev" script
make run          # when Makefile exists
./start.sh        # when start script exists
```

### Script Format
```bash
# WRONG - Windows-specific scripts
test.bat
deploy.ps1
setup.cmd

# CORRECT - Cross-platform bash scripts
test.sh
deploy.sh
setup.sh
```