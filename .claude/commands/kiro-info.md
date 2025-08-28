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
2. **Configure .gitignore for security** (first time only)
   - Check if .gitignore exists
   - Add Kiro-specific entries if not present
   - Protect sensitive files from accidental commits
3. Save to `.specs/project-info.md`
4. Auto-loaded in all future sessions
5. Store database config, tech stack, etc.

## .gitignore Configuration
Same as /kiro-start, add these entries if not present:
```
# Kiro SPECS sensitive files
.specs/project-info.md
.specs/session.md
.specs/backups/
*.backup
*.sql
```

## Tool Coordination
- **Write**: Create/update project-info.md and .gitignore
- **Read**: Verify saved information and check .gitignore
- **Bash**: Create .specs directory if needed

## Key Patterns
- **Persistent Context**: Information survives across sessions
- **Auto-Loading**: Automatically loaded by other commands
- **Database Config**: Special handling for database settings
- **Tech Stack**: Document frameworks and tools
- **Chinese Interaction**: All user dialogue must be in Chinese

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