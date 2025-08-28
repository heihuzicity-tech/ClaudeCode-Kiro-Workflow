# /kiro-save - Save Progress & Generate Session Prompt

## Triggers
- Session ending or context limit approaching
- Need to checkpoint current progress
- Preparing for session handover
- Creating recovery point

## Usage
```
/kiro-save
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Update `.specs/[feature]/tasks.md` with current progress status
2. **Create/overwrite `.specs/session.md` with current state**
   - MUST overwrite previous session file completely
   - Include feature name, branch, phase, progress
   - Add timestamp for tracking
3. Git commit progress (continue if Git fails)
4. Generate continuation prompt including:
   - Feature name, phase, and current task progress
   - SPECS document paths
   - Main modified files with descriptions
   - Primary working directory
5. Display formatted prompt for easy copy-paste:
```
=== Next Session Prompt ===
I am developing [feature_name] using Kiro SPECS
Session state saved to: .specs/session.md

Please load session with: /kiro-load
Or manually continue with: /kiro-next
=====================
```

## Session File Format
The `.specs/session.md` file should contain:
```markdown
# Kiro Session State
**Feature**: [feature_name]
**Branch**: [git_branch]
**Updated**: [timestamp]

## Current Phase
[requirements|design|tasks|execution]

## Task Progress
- [x] Task 1.1 - Description
- [x] Task 1.2 - Description
- [ ] Task 1.3 - Description (current)

## Working Context
- Main directory: [primary_directory]
- Modified files:
  - [file_path] - [description]

## Next Step
Continue with `/kiro-load` or `/kiro-next`
```

## Tool Coordination
- **Edit**: Update tasks.md progress
- **Write**: Create/overwrite .specs/session.md
- **Bash**: Git commit operations, get branch info
- **Read**: Gather context for session file

## Key Patterns
- **Progress Persistence**: Save exact task state
- **Context Preservation**: Include all relevant paths and status
- **Session Recovery**: Enable seamless continuation
- **Formatted Output**: Easy copy-paste prompt
- **Full Overwrite**: Complete session file replacement (vs /kiro-next lightweight update)
- **Chinese Communication**: All user interactions must be in Chinese

## Boundaries

**Will:**
- Save complete progress state
- Generate comprehensive prompt
- Commit changes safely
- Format for easy reuse

**Will Not:**
- Lose work if Git fails
- Skip important context
- Merge to main branch
- Delete working files