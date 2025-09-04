# Kiro Template System Configuration

## File Structure
All SPECS files are stored in: `.specs/{feature_name}/`
- `requirements.md` - Requirements document
- `design.md` - Design document  
- `tasks.md` - Task list
- `session.md` - Current active session (moved to feature directory on completion)
- `summary.md` - Generated completion summary
- `project-info.md` - Basic project information (stored in `.specs/` root)

## Directory Organization
```
.specs/
├── analysis/              # Code analysis results (independent storage)
│   └── code-analysis-{target}-{timestamp}.md  # AI expert analysis documents
├── {feature_name}/
│   ├── requirements.md     # Requirements specification document
│   ├── design.md          # Technical design and architecture
│   ├── tasks.md           # Implementation task list with progress tracking
│   ├── session-{date}.md  # Archived session file (after /kiro-end)
│   ├── summary.md         # Feature completion summary
│   ├── tests/             # Archived test files from project root
│   ├── scripts/           # Archived debug/utility scripts
│   ├── temp/              # Archived temporary files
│   └── docs/              # Additional documentation
├── project-info.md         # Basic project information and context
├── session.md             # Current active session (before /kiro-end)
└── backups/db/            # Database backups
    └── {feature}_backup_{timestamp}.sql
```

## Constants
- SPECS_DIRECTORY = "specs"
- SPEC_FILE_EXTENSIONS = ".md"
- SPEC_STORAGE_KEY = "KIRO::SPECS"
- PRODUCT_CONFIG_DIRECTORY = ".specs"

## Template Organization
### Workflow Templates
Located in `templates/workflows/`:
- `requirements.md` - Requirements gathering and clarification templates
- `design.md` - Design and research workflow templates
- `tasks.md` - Implementation planning and task breakdown templates
- `execution.md` - Task execution guidelines and constraints

### Command Templates  
Located in `templates/commands/`:
- `kiro-start.md` - Feature initiation with safety checks and setup
- `kiro-next.md` - Single task execution with progress tracking
- `kiro-save.md` - Progress saving and session persistence
- `kiro-load.md` - Session restoration and context recovery
- `kiro-end.md` - Feature completion with archiving and cleanup
- `kiro-info.md` - Project information configuration
- `kiro-status.md` - Project status display and progress calculation
- `kiro-think.md` - Deep analysis and requirement change management
- `kiro-git.md` - Quick Git commit operations
- `kiro-sync.md` - Synchronize discussion outcomes into SPECS documents
- `kiro-fix.md` - Bug fix workflow with lightweight documentation

### Rule Templates
Located in `templates/rules/`:
- `implicit-rules.md` - Workflow state rules and behavioral constraints

## Path Configuration Standards
### Primary Paths
- Project root: Current working directory
- SPECS storage: `.specs/` (relative to project root)
- Feature directories: `.specs/{feature_name}/`
- Database backups: `.specs/backups/db/`

### Template References
- Use `.specs/` format in all new templates (not `.kiro/specs/`)
- Maintain relative path structure for portability
- Ensure consistent file naming across all workflows
- Preserve existing path patterns from original kiro_specs_templates.md

## Global Behavioral Rules

### Language and Communication Rules
**Constraints:**
- The model MUST use Chinese language for ALL communication with users
- The model MUST provide user-facing messages, explanations, and interactions in Chinese
- The model MUST generate documents, comments, and user instructions in Chinese
- The model MAY use English for programming code, variable names, and technical identifiers following standard conventions
- The model MAY retain English format for technical configuration files and system settings when required

### Script and Command Rules
**Constraints:**
- The model MUST create bash shell scripts (.sh) exclusively
- The model MUST NOT create .bat (batch) or .ps1 (PowerShell) scripts under any circumstances
- The model SHOULD use bash commands that work on Linux, macOS, and Windows (WSL/Git Bash)
- The model SHOULD prioritize bash/Unix commands over PowerShell commands when available
- The model SHOULD assume Git Bash or WSL availability for bash execution on Windows systems

### Error Handling Strategy
**Constraints:**
- The model MUST follow the formula: Error occurs → Provide suggestions → Ask user → Wait for explicit instruction → Execute
- The model MUST NOT make assumptions about user preferences for error handling
- The model MUST provide clear error description and suggested options
- The model MUST NOT automatically retry or skip errors without user confirmation

### User Interaction Principles
**Constraints:**
- The model MUST require explicit user approval for all significant actions
- The model MUST NOT assume user preferences for critical decisions
- The model MUST provide detailed descriptions of proposed actions
- The model MUST wait for explicit user instruction before proceeding

### File Operation Standards
**Constraints:**
- The model MUST ensure all document updates are atomic (all succeed or all fail)
- The model SHOULD create backup versions before significant changes
- The model MUST use `.specs/` format consistently across all operations
- The model MUST verify file integrity and consistency after operations

### Database Backup Rules
**Constraints:**
- The model MUST execute backup immediately if database configuration is detected (without asking)
- The model MUST ask user for confirmation if no database configuration is detected
- The model MUST NOT skip database backup without user explicit confirmation
- The model MUST stop and provide solutions if backup fails, then ask user how to proceed

## Integration Guidelines
### Template Loading
Templates should be loaded in hierarchical order:
1. Global configuration (this file)
2. Workflow templates (for stage-specific behavior)
3. Command templates (for specific operations)
4. Rule templates (for behavioral constraints)

### Cross-Reference Maintenance
- Commands reference appropriate workflow templates
- Workflow templates reference execution guidelines
- All templates follow consistent path and naming conventions
- Rule templates provide behavioral boundaries for all operations