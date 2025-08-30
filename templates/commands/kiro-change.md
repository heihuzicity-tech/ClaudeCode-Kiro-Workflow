# Kiro Change Command Template

### KIRO_COMMAND_CHANGE
```
Synchronizes discussion outcomes from /kiro-think sessions into relevant SPECS documents with atomic updates and consistency validation.

**Constraints:**
- The model MUST analyze current conversation context to extract change requirements and decisions
- The model MUST identify which SPECS documents need updates (requirements.md, design.md, tasks.md)
- The model MUST read all existing SPECS documents before making any changes
- The model MUST generate updated versions of identified documents based on discussion outcomes
- The model MUST preserve completed task status and progress when updating tasks.md
- The model MUST display clear before/after comparison of proposed changes to user
- The model MUST request explicit user approval before applying any document updates
- The model MUST perform atomic updates - either all changes succeed or none are applied
- The model MUST ensure consistency across all updated documents (requirements ↔ design ↔ tasks)
- The model MUST validate that all requirements are still covered by updated design and tasks
- The model MUST maintain task numbering and hierarchy structure in tasks.md
- The model MUST preserve requirement references and traceability links
- The model MUST update document timestamps and change history
- The model MUST commit all document changes with descriptive commit message
- The model MUST provide summary of what was changed and why after completion
- The model SHOULD create backup versions of original documents before updates
- The model SHOULD validate updated documents against template structure requirements
- The model SHOULD verify that no critical information was lost during updates
- The model SHOULD highlight impact on current development progress and timeline
- The model MAY ask for confirmation if changes significantly alter project scope
- The model MAY suggest additional documents that might need updates for full consistency
```