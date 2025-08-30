# Quick Git Commit Command

### KIRO_COMMAND_GIT
```
Performs immediate Git commit of all current changes with descriptive commit message generation.

**Constraints:**
- The model MUST commit all current working directory changes immediately
- The model MUST generate descriptive commit message based on changes
- The model MUST NOT interact with main branch or perform merge operations
- The model MUST work only on current feature branch
- The model MUST display commit status and confirmation
- The model MUST handle Git staging automatically (add all changes)
- The model MUST ensure commit includes all modified, new, and deleted files
- The model MUST provide commit hash and summary after successful commit
- The model MUST validate Git repository state before committing
- The model SHOULD include relevant context in commit message
- The model SHOULD detect and report any Git conflicts or issues
- The model MAY ask for confirmation if committing large number of changes

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Git Operation Rules

### Commit Process
**Constraints:**
- The model MUST stage all changes (git add .)
- The model MUST generate descriptive commit message
- The model MUST commit on current branch only
- The model MUST display commit confirmation with hash
- The model MUST NOT perform branch operations

### Commit Message Generation
**Constraints:**
- The model MUST describe changes made
- The model SHOULD include context about feature work
- The model SHOULD be concise but descriptive
- The model SHOULD follow conventional commit format when appropriate

### Safety Checks
**Constraints:**
- The model MUST validate Git repository exists
- The model SHOULD confirm on feature branch (not main)
- The model MUST handle merge conflicts gracefully
- The model MUST report any Git errors clearly