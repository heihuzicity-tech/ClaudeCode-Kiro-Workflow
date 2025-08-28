# /kiro-load - Auto-load Session State

## Triggers
- Resuming work after session end
- Loading saved progress
- Recovering from interruption
- Starting new session on existing feature

## Usage
```
/kiro-load
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. **Reload global rules** (prevent rules loss after /clear)
   - Check if CLAUDE.md exists in project root
   - If exists, read and apply all global rules
   - This ensures rules work even after /clear command
   - Maintains Chinese interaction, script format rules, etc.

2. **Detect project root**
   - Search for `.specs/` directory in current or parent directories
   - Verify this is a Kiro project
   - Report error if not in Kiro project

3. **Load and validate session file**
   - Read `.specs/session.md` if exists
   - Parse feature name, branch, phase, progress
   - **Check timestamp validity**:
     - Compare session.md timestamp with tasks.md modification time
     - If tasks.md is newer than session.md, warn user
     - Prompt: "Session may be outdated. Options: [1] Use saved session [2] Scan current files [3] Cancel"
   - Report error if no session file found

4. **Verify Git branch**
   - Check current Git branch with `git branch`
   - Switch to correct feature branch if needed
   - Warn if branch doesn't exist

5. **Load SPECS documents**
   - Read all relevant SPECS documents:
     - `.specs/[feature]/requirements.md`
     - `.specs/[feature]/design.md`
     - `.specs/[feature]/tasks.md`
   - Display current phase and progress

6. **Show continuation guidance**
   - Display next uncompleted task
   - Suggest using `/kiro-next` to continue
   - Show summary of loaded state in Chinese

## Tool Coordination
- **Read**: Load CLAUDE.md first, then session.md and SPECS documents
- **Bash**: Check/switch Git branch
- **LS**: Verify project structure
- **TodoWrite**: Restore task tracking

## Key Patterns
- **Auto-detection**: Find project root automatically
- **State restoration**: Fully restore previous context
- **Branch alignment**: Ensure correct Git branch
- **Chinese feedback**: All user messages in Chinese

## Session File Location
- Always reads from `.specs/session.md` in project root
- Searches upward from current directory to find `.specs/`
- Maximum 5 levels up to prevent infinite search

## Validation Rules
- **Timestamp Check**: Always compare session.md vs tasks.md timestamps
- **Conflict Detection**: Warn if files modified after last session save
- **User Choice**: Let user decide how to handle outdated sessions
- **Safe Default**: When in doubt, prompt user rather than auto-decide

## Error Handling
- **No .specs/ found**: "Not in a Kiro project directory"
- **No session.md**: "No saved session found, use /kiro-start"
- **Branch missing**: "Feature branch not found, may need to fetch"
- **Corrupted session**: "Session file corrupted, please check manually"
- **Outdated session**: "Session outdated, showing options..."

## Boundaries

**Will:**
- Auto-detect project root
- Load complete session state
- Switch to correct branch
- Restore full context

**Will Not:**
- Create new features
- Modify existing documents
- Resolve Git conflicts
- Start new workflows