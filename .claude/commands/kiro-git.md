# /kiro-git - Quick Commit Changes

## Triggers
- Need to save code changes quickly
- Checkpoint current work
- Version control without merging
- Incremental progress commits

## Usage
```
/kiro-git
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Immediately commit current changes on active branch
2. NOT merge or interact with main branch
3. Generate descriptive commit message
4. Show commit status in Chinese

## Tool Coordination
- **Bash**: Git add and commit operations
- **Read**: Analyze changes for commit message
- **Write**: Update any pending documentation

## Key Patterns
- Quick commits without merge
- Stay on feature branch
- Automatic message generation
- Chinese status display

## Boundaries

**Will:**
- Commit all current changes
- Generate meaningful messages
- Stay on current branch
- Report status in Chinese

**Will Not:**
- Merge to main branch
- Switch branches
- Push to remote
- Resolve conflicts