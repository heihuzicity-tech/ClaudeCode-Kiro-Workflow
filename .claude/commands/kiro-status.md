# /kiro-status - Check Project Status

## Triggers
- Need to view current development status
- Check progress before resuming work
- Verify which phase and task currently on
- Quick project health check
- Status reporting to team

## Usage
```
/kiro-status
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. **Detect current project**
   - Search for `.specs/` directory
   - Identify active feature from session.md or Git branch
   - Report if no active feature found

2. **Gather status information**
   - Read `.specs/session.md` for session state
   - Check Git branch and status
   - Analyze `.specs/{feature}/tasks.md` for progress
   - Determine current phase from existing documents
   - Calculate task completion percentage

3. **Display comprehensive status**
   - Format and display in Chinese
   - Show visual progress indicators
   - Highlight any issues or warnings

## Status Display Format
```
╔════════════════════════════════════════╗
║        KIRO Project Status Report       ║
╚════════════════════════════════════════╝

📁 Project Path: /path/to/project
🎯 Current Feature: user-authentication
🌿 Git Branch: feature/user-authentication
📊 Current Phase: Execution

📝 Task Progress: 5/10 completed (50%)
  
  ✅ Completed: 5 tasks
    - 1.1 Create user model
    - 1.2 Implement validation logic
    - 1.3 Create API endpoint
    - 2.1 Add authentication middleware
    - 2.2 Implement password encryption
  
  🔄 Current Task: 2.3 Create login interface
  
  ⏳ Pending: 4 tasks

📅 Time Information:
  - Feature Started: 2025-01-31 10:00
  - Last Updated: 2025-01-31 15:30
  - Working Time: 5.5 hours

💾 Session Status:
  - session.md: ✅ Up to date
  - Auto-save: ✅ Enabled
  
⚠️ Warnings:
  - Uncommitted changes (3 files)
  - Suggest using /kiro-git to commit progress

Next Steps:
  → Continue: /kiro-next
  → Save: /kiro-save  
  → Commit: /kiro-git
```

## Phase Detection Rules
1. **No documents** → Phase: "Not started"
2. **Only requirements.md** → Phase: "Requirements"
3. **Has design.md** → Phase: "Design"
4. **Has tasks.md** → Phase: "Task Planning"
5. **Has task progress** → Phase: "Execution"
6. **All tasks completed** → Phase: "Ready to complete"
7. **Has summary.md** → Phase: "Completed"

## Warning Conditions
- **Outdated session**: session.md older than tasks.md
- **Uncommitted changes**: Git has pending changes
- **Wrong branch**: Not on feature branch
- **No backup**: Database config but no recent backup
- **Long session**: Working >4 hours without save

## Tool Coordination
- **Read**: Load session.md, tasks.md, and SPECS documents
- **Bash**: Check Git status and branch
- **LS**: Verify project structure
- **Grep**: Count completed vs pending tasks

## Key Patterns
- **Comprehensive view**: All status in one place
- **Visual indicators**: Progress bars and icons
- **Chinese display**: All text in Chinese
- **Actionable**: Shows next steps
- **Health check**: Identifies issues

## Error Handling
- **No project**: "No Kiro project found, please run in project directory"
- **No feature**: "No active feature development, use /kiro-start to begin"
- **Corrupted files**: "Documents corrupted, please manually check .specs/ directory"

## Boundaries

**Will:**
- Show complete project status
- Calculate real progress
- Identify potential issues
- Suggest next actions

**Will Not:**
- Modify any files
- Execute any actions
- Fix problems automatically
- Make decisions for user