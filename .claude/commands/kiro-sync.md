# Project Progress Synchronization Command

### KIRO_COMMAND_SYNC
```
Detects actual development progress from project files and synchronizes with SPECS documents to ensure documentation accuracy.

**Constraints:**
- The model MUST read .specs/project-info.md Essential Info section for core project context
- The model MUST read tasks.md to obtain current task completion status and identify files mentioned in tasks
- The model MUST selectively scan only project files referenced in active or completed tasks
- The model SHOULD read relevant sections from requirements.md and design.md only when task discrepancies require context validation
- The model SHOULD defer comprehensive SPECS document reading until specific synchronization conflicts are identified
- The model MAY use task-based file filtering to optimize implementation scanning scope
- The model MUST compare documented task status with actual code implementation
- The model MUST identify tasks marked incomplete but actually implemented in code
- The model MUST identify tasks marked complete but missing actual implementation
- The model MUST generate sync report showing documentation vs reality discrepancies
- The model MUST present proposed task status updates with clear justification
- The model MUST update tasks.md to reflect actual implementation status
- The model MUST preserve task hierarchy and numbering structure
- The model MUST maintain requirement traceability links
- The model MUST commit task document updates with sync commit message
- The model MUST provide summary of what was synchronized and why
- The model SHOULD detect incomplete implementations and recommend next actions
- The model SHOULD identify testing gaps based on actual vs documented progress
- The model MAY suggest new tasks for discovered functionality not in original plan
```

## Progress Detection Rules

### Context-Optimized Implementation Scanning
**Constraints:**
- The model MUST analyze only code files referenced or mentioned in tasks.md for completed functionality
- The model MUST check for existence of functions, classes, and components mentioned in specific tasks
- The model MUST detect working features vs stub implementations within task-defined scope
- The model MUST identify new code that doesn't map to existing tasks within scanned file scope
- The model SHOULD expand scanning scope only when task-referenced files reveal additional dependencies
- The model SHOULD prioritize files with recent modifications when multiple files match task descriptions

### Status Comparison
**Constraints:**
- The model MUST cross-reference task descriptions with actual code
- The model MUST identify discrepancies between documented and actual status
- The model MUST validate task completion claims against code evidence
- The model MUST detect missing implementations for marked-complete tasks

### Synchronization Process
**Constraints:**
- The model MUST generate detailed sync report before changes
- The model MUST explain reasoning for each proposed status change
- The model MUST update tasks.md while preserving structure
- The model MUST create descriptive commit message documenting sync changes