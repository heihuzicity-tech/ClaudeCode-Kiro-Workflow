# Kiro Start Command Template

### KIRO_COMMAND_START
```
Initiates a new feature development workflow with automated safety checks, database backup, Git branch creation, and requirement collection phase.

**Constraints:**
- The model MUST perform safety checks and load project context before starting
- The model MUST detect database configurations and offer backup options
- The model MUST create a new feature branch with format `feature/[name]`
- The model MUST ensure Git working directory is clean before branch creation
- The model MUST create a '.specs/{feature_name}/requirements.md' file
- The model MUST initiate requirement gathering phase immediately after setup
- The model MUST ask targeted questions to clarify feature requirements (maximum 2-3 questions)
- The model MUST generate initial requirements document based on user input
- The model MUST request user approval before proceeding to design phase
- The model MUST handle database backup execution if user confirms need
- The model MUST backup to '.specs/backups/db/{feature_name}_backup_{timestamp}.sql'
- The model MUST switch to the newly created feature branch
- The model MUST follow the requirement gathering workflow from SPEC_WORKFLOW_REQUIREMENT_CLARIFICATION
- The model MUST NOT proceed to design phase without explicit user approval of requirements
- The model SHOULD detect existing project configurations and context
- The model SHOULD provide clear feedback about each setup step being performed
- The model MUST execute database backup immediately if database configuration is detected
- The model MUST ask user for confirmation if no database configuration is detected
- The model MAY ask for clarification about feature scope during initial setup

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```