# Session Recovery Command

### KIRO_COMMAND_LOAD
```
Restores saved session state with automatic rule reloading, project detection, session validation, and complete context recovery.

**Constraints:**
- The model MUST first read ./CLAUDE.md file to restore global rules and configuration after /clear commands
- The model MUST detect project root directory using Glob search for .specs files
- The model MUST execute Read tool on CLAUDE.md before any other file operations
- The model MUST read .specs/project-info.md Essential Info section for core project context
- The model MUST locate and validate existing .specs/session.md file with timestamp verification
- The model MUST read .specs/session.md Current Focus and Next Actions sections for immediate session state
- The model MUST verify current Git branch matches session state and switch if necessary
- The model MUST selectively load relevant SPECS document sections based on current session focus
- The model SHOULD read complete project-info.md Technical Configuration section only when needed for technical decisions
- The model SHOULD read complete session.md Detailed History section only when context gaps are identified
- The model SHOULD load complete SPECS documents only when current session requires comprehensive context
- The model MAY defer loading detailed documentation until specific information is needed for task execution
- The model MUST detect session type from session.md content
- The model MUST restore complete working context by parsing session.md content for appropriate workflow type (feature development OR bug fix OR mixed)
- The model MUST check bug fix status and recommend appropriate continuation
- The model MUST display current feature name and development stage
- The model MUST show current progress and provide context-aware continuation suggestions based on detected workflow type
- The model MUST handle missing session files gracefully with appropriate error messages
- The model MUST validate session file integrity and timestamp validity
- The model MUST ensure Git repository is in correct state for continued development
- The model MUST restore project context including file references and progress tracking
- The model MUST confirm successful context restoration with status summary
- The model SHOULD detect and report any inconsistencies in session state
- The model SHOULD provide recovery options if session state is incomplete
- The model MAY ask for confirmation if significant time has elapsed since last save

## Error Handling
Error handling follows global constraints defined in CLAUDE.md
```

## Context Recovery Rules

### Context-Optimized Recovery Sequence
**Constraints:**
- The model MUST read CLAUDE.md first (restore global configuration)
- The model MUST detect project root directory using Glob search for .specs files
- The model MUST validate and selectively read essential sections from session.md file
- The model MUST verify and restore Git branch state
- The model MUST selectively load relevant SPECS document sections based on session focus
- The model MUST display current status and next actions
- The model SHOULD defer comprehensive document loading until specific context is needed

### Session Validation
**Constraints:**
- The model MUST verify session file integrity
- The model MUST validate timestamp and freshness
- The model MUST check Git repository consistency
- The model MUST confirm all referenced files exist
- The model MUST handle missing or corrupted session data gracefully

### Context Restoration
**Constraints:**
- The model MUST restore feature name and current stage
- The model MUST restore task progress and completion status
- The model MUST restore file references and working directory
- The model MUST restore project configuration and settings