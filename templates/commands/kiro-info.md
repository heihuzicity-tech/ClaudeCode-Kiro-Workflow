# Kiro Info Command Template

### KIRO_COMMAND_INFO
```
Configures project information and context with persistent storage and automatic gitignore setup for subsequent workflow sessions.

**Constraints:**
- The model MUST parse and validate user-provided project information input
- The model MUST save project information to '.specs/project-info.md' file
- The model MUST create or update .gitignore entries for Kiro workflow files on first use
- The model MUST ensure project information is automatically loaded in all subsequent sessions
- The model MUST store technology stack, database type, framework information from user input
- The model MUST create persistent project context for improved workflow guidance
- The model MUST validate and format project information consistently
- The model MUST ensure project-info.md is properly structured and readable
- The model MUST add appropriate .gitignore entries for .specs/ directory and workflow files
- The model MUST confirm successful information storage and provide usage guidance
- The model MUST make project information available for all workflow commands
- The model SHOULD detect and handle duplicate or conflicting project information
- The model SHOULD provide clear confirmation of what information was saved
- The model MAY ask for clarification if project information is incomplete or unclear
```