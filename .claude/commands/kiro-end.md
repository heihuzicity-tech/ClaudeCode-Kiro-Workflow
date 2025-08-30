# Feature Completion Command

### KIRO_COMMAND_END
```
Completes feature development with document finalization, file archiving, summary generation, and branch management.

**Constraints:**
- The model MUST update all SPECS documents to completed status
- The model MUST generate comprehensive feature summary at '.specs/{feature_name}/summary.md'
- The model MUST archive scattered files (tests, scripts, temp files, analysis docs) to feature directory
- The model MUST move current session.md to feature directory as session-{date}.md
- The model MUST commit all final changes with completion message
- The model MUST create pull request or merge to main branch based on project workflow
- The model MUST clean up working directory of temporary files and artifacts
- The model MUST ensure all tasks in tasks.md are marked as completed
- The model MUST validate that all requirements have been implemented
- The model MUST provide final project status and completion confirmation
- The model MUST create feature completion summary including metrics and outcomes
- The model SHOULD backup final state before branch operations
- The model SHOULD validate code quality and test coverage before completion
- The model SHOULD provide deployment readiness assessment
- The model MAY ask for confirmation before branch merge operations

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Feature Completion Process

### Document Finalization
```
- MUST mark all tasks as completed in tasks.md
- MUST update all SPECS documents to completed status
- MUST validate requirement implementation coverage
- MUST generate comprehensive summary.md
```

### File Archiving Rules
```
- MUST move tests/ directory to .specs/{feature_name}/tests/
- MUST move scripts/ directory to .specs/{feature_name}/scripts/
- MUST move temp/ files to .specs/{feature_name}/temp/
- MUST move analysis docs to .specs/{feature_name}/analysis/
- MUST archive session.md as session-{date}.md in feature directory
```

### Branch Management
```
- MUST commit all final changes
- MUST create pull request OR merge to main (based on project workflow)
- MUST clean up feature branch after successful merge
- MUST ensure working directory is clean
```

### Completion Validation
```
- MUST verify all requirements implemented
- MUST validate all tasks completed
- MUST ensure code quality standards met
- MUST confirm deployment readiness
```