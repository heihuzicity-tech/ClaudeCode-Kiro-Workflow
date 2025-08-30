# Kiro Git Command Template

### KIRO_COMMAND_GIT
```
Performs immediate Git commit of all current changes with descriptive message generation and status feedback.

**Constraints:**
- The model MUST immediately commit all current changes in the working directory
- The model MUST generate descriptive and meaningful commit messages based on changes
- The model MUST use Git add and commit operations on current feature branch
- The model MUST NOT interact with main branch or perform branch operations
- The model MUST NOT update progress documents or workflow state files
- The model MUST display clear commit status and confirmation after completion
- The model MUST handle empty commits gracefully with appropriate messages
- The model MUST ensure commits are made on the correct feature branch
- The model MUST provide feedback about what files were committed
- The model MUST generate commit messages that follow project conventions
- The model MUST preserve existing Git history and branch structure
- The model SHOULD include brief description of what changes were committed
- The model SHOULD verify Git repository state before committing
- The model MAY ask for confirmation if committing large numbers of files
```