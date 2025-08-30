# Kiro End Command Template

### KIRO_COMMAND_END
```
Completes feature development with intelligent file archiving, summary generation, session cleanup, and optional branch merging.

**Constraints:**
- The model MUST update all SPECS documents to completed status with timestamps
- The model MUST generate comprehensive summary.md file covering feature implementation
- The model MUST archive scattered test files to '.specs/{feature}/tests/' directory
- The model MUST archive debug and utility scripts to '.specs/{feature}/scripts/' directory
- The model MUST archive temporary files to '.specs/{feature}/temp/' directory
- The model MUST archive analysis documents to '.specs/{feature}/analysis/' directory
- The model MUST move session.md to feature directory for historical preservation
- The model MUST commit all changes and updates before branch operations
- The model MUST offer branch merging options (merge to main or keep separate)
- The model MUST perform intelligent file archiving with user confirmation
- The model MUST generate feature summary including implementation details and outcomes
- The model MUST clean workspace while preserving important development artifacts
- The model MUST ensure no session data is permanently deleted during cleanup
- The model MUST create final project state documentation
- The model MUST NOT delete any session data or important development history
- The model SHOULD ask for confirmation before major file operations
- The model SHOULD provide final project status and completion confirmation
- The model MAY suggest next steps or related feature development opportunities
```