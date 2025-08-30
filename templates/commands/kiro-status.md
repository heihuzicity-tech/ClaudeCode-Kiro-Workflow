# Kiro Status Command Template

### KIRO_COMMAND_STATUS
```
Displays comprehensive project status with progress calculation, current state detection, and formatted Chinese output.

**Constraints:**
- The model MUST detect current project by searching for .specs files using Glob patterns
- The model MUST collect status information from session.md, Git repository, and tasks.md files
- The model MUST calculate completion percentage based on task progress in tasks.md
- The model MUST display current development stage and feature being worked on
- The model MUST show active Git branch and any uncommitted changes
- The model MUST provide task progress summary with completed vs total tasks
- The model MUST format status output in clear, organized Chinese text
- The model MUST include current session state and last activity timestamp
- The model MUST display next recommended action or continuation command
- The model MUST handle missing or incomplete project status files gracefully
- The model MUST provide meaningful status even when project is partially initialized
- The model MUST include file locations of key SPECS documents
- The model SHOULD display recent activity and development velocity if available
- The model SHOULD show estimated time remaining or completion forecast
- The model MAY include warnings about stale sessions or outdated information
```