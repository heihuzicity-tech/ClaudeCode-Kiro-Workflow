# /kiro-info - Save Project Information

## Triggers
- Project initialization
- Database configuration setup
- Technology stack documentation
- Project context updates

## Usage
```
/kiro-info [information]
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. Parse information from user input
2. Save to `.specs/project-info.md`
3. Auto-loaded in all future sessions
4. Store database config, tech stack, etc.

## Tool Coordination
- **Write**: Create/update project-info.md
- **Read**: Verify saved information
- **Bash**: Create .specs directory if needed

## Key Patterns
- **Persistent Context**: Information survives across sessions
- **Auto-Loading**: Automatically loaded by other commands
- **Database Config**: Special handling for database settings
- **Tech Stack**: Document frameworks and tools

## Boundaries

**Will:**
- Save any project information
- Create .specs directory if needed
- Make info available globally
- Support incremental updates

**Will Not:**
- Validate database connections
- Execute database operations
- Overwrite without confirmation
- Expose sensitive credentials