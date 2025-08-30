# Project Status Display Command

### KIRO_COMMAND_STATUS
```
Displays comprehensive project status including current feature, development stage, task progress, and Git information.

**Constraints:**
- The model MUST detect current project using Glob search for .specs files
- The model MUST collect status information from session.md, Git repository, and tasks.md
- The model MUST calculate completion percentage based on task progress
- The model MUST display current feature name and development stage
- The model MUST show completed vs total task counts
- The model MUST display current Git branch and commit status
- The model MUST present information in clear, formatted Chinese output
- The model MUST handle missing status files gracefully with appropriate messages
- The model MUST validate and cross-reference status information
- The model MUST provide next recommended action based on current status
- The model SHOULD include recent progress and activity summary
- The model SHOULD detect any inconsistencies in project state
- The model MAY provide warnings about stale sessions or outdated information

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Status Display Rules

### Status Collection
**Constraints:**
- The model MUST detect project using Glob search for .specs
- The model MUST read session.md for current feature and stage
- The model MUST read tasks.md for progress calculation
- The model MUST check Git status and branch information
- The model MUST validate status file consistency

### Progress Calculation
**Constraints:**
- The model MUST count completed vs total tasks
- The model MUST calculate completion percentage
- The model MUST identify current active task
- The model SHOULD detect any blocked or problematic tasks

### Display Format
**Constraints:**
- The model MUST display feature name and description
- The model MUST show current development stage
- The model MUST present task progress (X/Y completed, Z% done)
- The model MUST display Git branch and commit status
- The model MUST provide next recommended action
- The model MUST use Chinese language formatting