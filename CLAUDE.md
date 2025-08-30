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
├── {feature_name}/
│   ├── requirements.md     # Requirements specification document
│   ├── design.md          # Technical design and architecture
│   ├── tasks.md           # Implementation task list with progress tracking
│   ├── session-{date}.md  # Archived session file (after /kiro-end)
│   ├── summary.md         # Feature completion summary
│   ├── tests/             # Archived test files from project root
│   ├── scripts/           # Archived debug/utility scripts
│   ├── temp/              # Archived temporary files
│   ├── analysis/          # Archived analysis documents
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
- `kiro-change.md` - Synchronize discussion outcomes into SPECS documents

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