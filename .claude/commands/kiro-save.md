# Progress Save Command

### KIRO_COMMAND_SAVE
```
Saves current development progress with Git checkpoint, session state persistence, and minimal status output for session recovery.

**Constraints:**
- The model MUST update current task progress (feature tasks.md OR bug fix-tasks.md) and include relevant context
- The model MUST perform silent Git commit with descriptive checkpoint message
- The model MUST detect session type by scanning active directories and documents
- The model MUST save comprehensive session state to '.specs/session.md'
- The model MUST include current feature name and development stage in session file
- The model MUST include bug fix context if bugs/ directories exist with ACTIVE status
- The model MUST record latest completed task and current progress in session file
- The model MUST list all relevant SPECS documents (requirements.md, design.md, tasks.md) with status and modification info in session file
- The model MUST include main project files and their descriptions in session file
- The model MUST record key project files that have been modified or referenced during development
- The model MUST include file modification timestamps and status for recovery reference
- The model MUST specify current working directory in session file
- The model MUST provide session recovery instructions in session file
- The model MUST display minimal output showing feature, stage, and progress
- The model MUST create session recovery prompt for next session continuation
- The model MUST preserve all task completion states and progress indicators
- The model MUST ensure session file contains sufficient context for session recovery
- The model MUST commit all current changes before creating session checkpoint
- The model SHOULD include timestamp in session file for reference
- The model SHOULD provide clear instructions for using /kiro-load command
- The model MAY include branch information and Git status in session file

## Error Handling
Error handling follows global constraints defined in CLAUDE.md
```

## Session State Management

### Context-Optimized Session Generation
**Constraints:**
- The model MUST structure session.md with essential information prioritized at top
- The model MUST limit core status section to essential context only (target < 500 tokens)
- The model MUST use collapsible sections for detailed historical information
- The model MUST organize session.md in the following structure:
  - ## Current Focus (核心状态 - 必读): Active feature, current task, progress, Git branch
  - ## Next Actions (关键行动 - 必读): Immediate next tasks only
  - ## Technical Context (技术上下文 - 按需): Key dependencies and critical decisions
  - ## Detailed History (详细历史 - 归档): Complete session log in collapsible section
- The model MUST include only actionable next steps, not comprehensive task history
- The model SHOULD prioritize information needed for quick session recovery

### Progress Preservation Rules
**Constraints:**
- The model MUST capture current task completion status
- The model MUST record all SPECS document states
- The model MUST include working directory context
- The model MUST preserve Git branch and commit information
- The model MUST create comprehensive recovery instructions

### Minimal Output Format
**Constraints:**
- The model MUST display feature name, current stage, and progress percentage
- The model MUST create session recovery prompt for next session
- The model MUST provide clear continuation instructions