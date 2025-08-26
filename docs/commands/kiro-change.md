# /kiro-change - Handle Requirement Changes

## Triggers
- Requirements need modification
- Design changes required
- New features discovered during development
- Scope adjustments needed

## Usage
```
/kiro-change
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Understand change need through discussion
2. Reload and display current requirements/design
3. Return to appropriate planning phase
4. Regenerate downstream documents after upstream changes
5. Remind user to use `/kiro-next` after planning updates

## Tool Coordination
- **Read**: Load current SPECS documents
- **Edit**: Update requirements/design/tasks
- **Write**: Regenerate affected documents
- **TodoWrite**: Track change process

## Key Patterns
- Upstream changes cascade downstream
- Preserve completed task status
- Return to appropriate phase
- Maintain document consistency

## Boundaries

**Will:**
- Handle any scope changes
- Preserve completed work
- Maintain document integrity
- Guide through change process

**Will Not:**
- Lose completed progress
- Skip impact analysis
- Auto-approve changes
- Break existing functionality