# /kiro-start - Start SPECS Development

## Triggers
- New feature development requests
- Project initialization with SPECS workflow
- Beginning a structured development cycle

## Usage
```
/kiro-start [feature_name]
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Execute safety checks and auto context loading
   - Check project root - verify `.specs/` folder exists
   - Load project info - auto-read `.specs/project-info.md` if exists
   - Load current context - check for active features and progress
2. Prompt for database backup if configured
   - Check `.specs/project-info.md` for database configuration
   - Execute backup to `.specs/backups/db/{feature_name}_backup_{timestamp}.sql`
3. Create feature branch `feature/[name]`
   - Check git clean state
   - Create and switch to feature branch
4. Start requirements phase with auto-guidance
   - Create `.specs/{feature_name}/requirements.md`
   - Use hybrid approach for requirements gathering
   - Request approval: "需求包含以下要点：[列出要点]。看起来如何？可以进入设计阶段吗？"

## Tool Coordination
- **Read**: Check `.specs/project-info.md`
- **Bash**: Create directories, Git operations, database backup
- **Write**: Generate requirements.md
- **TodoWrite**: Track phase progression

## Key Patterns
- **Phase Progression**: Requirements → Design → Tasks → Execution
- **User Approval**: Mandatory gates between phases
- **Chinese Communication**: All dialogue in Chinese
- **Auto Documentation**: Generate structured SPECS documents

## Boundaries

**Will:**
- Create complete SPECS documentation structure
- Guide through all development phases
- Ensure safety with backups and Git branches
- Communicate in Chinese with users

**Will Not:**
- Skip safety checks or approval gates
- Auto-generate code without requirements
- Proceed without user confirmation
- Mix English in Chinese communication