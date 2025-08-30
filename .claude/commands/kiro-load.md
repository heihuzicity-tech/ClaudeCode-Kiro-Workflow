# Session Recovery Command

### KIRO_COMMAND_LOAD
```
Restores saved session state with automatic rule reloading, project detection, session validation, and complete context recovery.

**Constraints:**
- The model MUST first read ./CLAUDE.md file to restore global rules and configuration after /clear commands
- The model MUST detect project root directory using Glob search for .specs files
- The model MUST execute Read tool on CLAUDE.md before any other file operations
- The model MUST locate and validate existing .specs/session.md file with timestamp verification
- The model MUST read .specs/session.md file content to restore session state and progress information
- The model MUST verify current Git branch matches session state and switch if necessary
- The model MUST load all SPECS documents (requirements.md, design.md, tasks.md) into context
- The model MUST restore complete working context by parsing session.md content for feature name, current stage, task progress, and file references
- The model MUST display current feature name and development stage
- The model MUST show current task progress and next recommended action
- The model MUST provide continuation suggestions (typically /kiro-next command)
- The model MUST handle missing session files gracefully with appropriate error messages
- The model MUST validate session file integrity and timestamp validity
- The model MUST ensure Git repository is in correct state for continued development
- The model MUST restore project context including file references and progress tracking
- The model MUST confirm successful context restoration with status summary
- The model SHOULD detect and report any inconsistencies in session state
- The model SHOULD provide recovery options if session state is incomplete
- The model MAY ask for confirmation if significant time has elapsed since last save

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Context Recovery Rules

### Recovery Sequence
```
1. MUST read CLAUDE.md first (restore global configuration)
2. MUST detect project root using Glob search
3. MUST validate and read session.md file
4. MUST verify and restore Git branch state
5. MUST load all SPECS documents into context
6. MUST display current status and next actions
```

### Session Validation
```
- MUST verify session file integrity
- MUST validate timestamp and freshness
- MUST check Git repository consistency
- MUST confirm all referenced files exist
- MUST handle missing or corrupted session data gracefully
```

### Context Restoration
```
- MUST restore feature name and current stage
- MUST restore task progress and completion status
- MUST restore file references and working directory
- MUST restore project configuration and settings
```