# /kiro-end - Complete Feature Development

## Triggers
- All tasks completed
- Feature ready for delivery
- Development cycle completion
- Final documentation needed

## Usage
```
/kiro-end
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Update all progress documents to completed status
2. Generate `.specs/{feature_name}/summary.md`
3. Mark session.md as completed with timestamp
4. Archive scattered files to `.specs/{feature_name}/`
5. Move session.md to `.specs/{feature_name}/session-{timestamp}.md`
6. Commit all changes with descriptive message
7. Create pull request or merge to main
8. Provide final status report in Chinese

## Tool Coordination
- **Edit**: Update all SPECS documents to completed status
- **Write**: Generate summary.md document
- **Bash**: Git commit and merge operations
- **Read**: Gather information for summary
- **Glob**: Detect scattered files for archiving
- **Move**: Archive files to proper directories

## Key Patterns
- Complete documentation closure
- Automatic summary generation
- Safe merge to main branch
- Chinese status reporting
- Session archiving with timestamp
- Intelligent file organization

## Enhanced Features

### Session Management
- **Mark Completion**: Update session.md with `## Project Completed ✅` and timestamp
- **Archive Session**: Move to `.specs/{feature}/session-{timestamp}.md`
- **Preserve History**: Never delete session data, only archive

### Intelligent File Archiving
Automatically detect and archive scattered files from project root:
```
Pattern → Target Directory
test_*.* → .specs/{feature}/tests/
*.test.* → .specs/{feature}/tests/
debug.* → .specs/{feature}/scripts/
temp_*.* → .specs/{feature}/temp/
script.* → .specs/{feature}/scripts/
analysis_*.* → .specs/{feature}/analysis/
New *.md files → .specs/{feature}/docs/
```

### Archiving Rules
- **Time-based Detection**: Files created after feature start time
- **Pattern Matching**: Recognize test scripts, debug files, temporary files
- **Smart Protection**: Never move system files (package.json, README.md, etc.)
- **Confirmation Required**: Display file list before archiving

## Boundaries

**Will:**
- Generate complete summary
- Update all document statuses
- Safely merge to main
- Archive feature documents
- Mark session as completed
- Organize scattered files
- Preserve session history

**Will Not:**
- Skip incomplete tasks
- Force merge conflicts
- Delete working branches prematurely
- Lose uncommitted changes
- Delete session.md (only archive)
- Move system configuration files
- Archive without confirmation

## Example Execution

```
User: /kiro-end

AI: Starting feature completion process...

    📋 Updating session status...
    ✅ Session marked as completed at 2025-01-28 16:45

    🔍 Scanning for files to archive...
    Found the following files to organize:
    
    Files to Archive:
    ├── test_auth.js → .specs/user-auth/tests/
    ├── debug.sh → .specs/user-auth/scripts/
    ├── temp_data.json → .specs/user-auth/temp/
    ├── analysis_results.md → .specs/user-auth/analysis/
    └── implementation_notes.md → .specs/user-auth/docs/
    
    Do you want to archive these files? (yes/no)

User: yes

AI: Archiving files...
    ✅ Files organized into .specs/user-auth/
    ✅ Session archived to .specs/user-auth/session-20250128.md
    
    📝 Generating summary...
    ✅ Summary saved to .specs/user-auth/summary.md
    
    🔄 Updating project-info.md...
    ✅ Project information updated
    
    📦 Committing changes...
    ✅ All changes committed
    
    🎯 Feature Development Completed
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━
    Feature: user-auth
    Files Archived: 5
    Session Preserved: session-20250128.md
    Status: Ready for merge to main
    
    Next steps:
    - Review the summary document
    - Create PR or merge to main
```