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
2. Git commit progress (continue if Git fails)
3. Generate continuation prompt including:
   - Feature name, phase, and current task progress
   - SPECS document paths
   - Main modified files with descriptions
   - Primary working directory
4. Display formatted prompt for easy copy-paste:
```
=== Next Session Prompt ===
I am developing [feature_name] using Kiro SPECS
Current phase: [execution_phase]
Latest progress: Completed task [X.X] - [task_description]

SPECS documents:
- Requirements: .specs/[feature_name]/requirements.md
- Design: .specs/[feature_name]/design.md
- Tasks: .specs/[feature_name]/tasks.md

Main files:
- [file1_path] - [brief description]
- [file2_path] - [brief description]

Working directory: [primary_directory_path]

Please continue with: /kiro-next
=====================
```

## Tool Coordination
- **Edit**: Update tasks.md progress
- **Bash**: Git commit operations
- **Read**: Gather context for prompt
- **Write**: Save session state

## Key Patterns
- **Progress Persistence**: Save exact task state
- **Context Preservation**: Include all relevant paths and status
- **Session Recovery**: Enable seamless continuation
- **Formatted Output**: Easy copy-paste prompt

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