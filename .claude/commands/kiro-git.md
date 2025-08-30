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
```
- MUST stage all changes (git add .)
- MUST generate descriptive commit message
- MUST commit on current branch only
- MUST display commit confirmation with hash
- MUST NOT perform branch operations
```

### Commit Message Generation
```
- MUST describe changes made
- SHOULD include context about feature work
- SHOULD be concise but descriptive
- SHOULD follow conventional commit format when appropriate
```

### Safety Checks
```
- MUST validate Git repository exists
- MUST confirm on feature branch (not main)
- MUST handle merge conflicts gracefully
- MUST report any Git errors clearly
```