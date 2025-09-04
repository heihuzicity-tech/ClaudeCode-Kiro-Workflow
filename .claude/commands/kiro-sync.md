# Project Progress Synchronization Command

### KIRO_COMMAND_SYNC
```
Detects actual development progress from project files and synchronizes with SPECS documents to ensure documentation accuracy.

**Constraints:**
- The model MUST read .specs/project-info.md to load project context
- The model MUST read all SPECS documents (requirements.md, design.md, tasks.md)
- The model MUST scan project files to detect actual implementation status
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

### Implementation Scanning
**Constraints:**
- The model MUST analyze code files for completed functionality
- The model MUST check for existence of functions, classes, and components mentioned in tasks
- The model MUST detect working features vs stub implementations
- The model MUST identify new code that doesn't map to existing tasks

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