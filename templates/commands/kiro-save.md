# Kiro Save Command Template

### KIRO_COMMAND_SAVE
```
Saves current development progress with Git checkpoint, session state persistence, and minimal status output for session recovery.

**Constraints:**
- The model MUST update tasks.md with current progress and task completion status
- The model MUST perform silent Git commit with descriptive checkpoint message
- The model MUST save comprehensive session state to '.specs/session.md'
- The model MUST include current feature name and development stage in session file
- The model MUST record latest completed task and current progress in session file
- The model MUST list all relevant SPECS documents (requirements.md, design.md, tasks.md) in session file
- The model MUST include main project files and their descriptions in session file
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
```