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
3. Commit all changes with descriptive message
4. Create pull request or merge to main
5. Provide final status report in Chinese

## Tool Coordination
- **Edit**: Update all SPECS documents to completed status
- **Write**: Generate summary.md document
- **Bash**: Git commit and merge operations
- **Read**: Gather information for summary

## Key Patterns
- Complete documentation closure
- Automatic summary generation
- Safe merge to main branch
- Chinese status reporting

## Boundaries

**Will:**
- Generate complete summary
- Update all document statuses
- Safely merge to main
- Archive feature documents

**Will Not:**
- Skip incomplete tasks
- Force merge conflicts
- Delete working branches prematurely
- Lose uncommitted changes