# Changelog

All notable changes to this project will be documented in this file.

## [1.0.3] - 2025-08-28

### Added
- New `/kiro-load` command for automatic session recovery
- New `/kiro-status` command for clean project status display
- New `/kiro-think [v1/v2/v3]` command for deep thinking mode (replaces `/kiro-change`)
- Enhanced `/kiro-end` with intelligent file archiving
- Session persistence to `.specs/session.md` for `/kiro-save`
- Session preservation with timestamp archiving
- Automatic organization of scattered test/debug/temp files
- File archiving confirmation mechanism
- Phase 5 documentation for Feature Completion workflow
- Double verification mechanism for `/kiro-next` with auto-save
- `.gitignore` auto-configuration in `/kiro-start` and `/kiro-info`

### Changed
- `/kiro-end` now marks session.md as completed instead of deleting
- `/kiro-end` archives session.md to `.specs/{feature}/session-{timestamp}.md`
- Updated file structure to include organized subdirectories
- Enhanced project closure workflow with better file organization
- All SPECS files automatically saved to `.specs/{feature}/` structure
- Commands execute directly without confirmation
- Normal discussions require confirmation before code changes
- `/kiro-next` now enforces bash/shell scripts only, prohibits bat/ps1/PowerShell
- `/kiro-next` asks user to kill conflicting processes instead of changing ports
- `/kiro-next` prioritizes service management scripts over direct commands

### Improved
- Better separation of concerns for project files
- Preserved session history for future reference
- Smart protection for system configuration files
- Cleaner project structure after feature completion
- English rules with Chinese interaction support
- Automatic directory compliance without constant prompting

### Removed
- `/kiro-change` command (replaced by `/kiro-think`)

## [1.0.2] - 2025-01-31

### Changed
- Simplified CLAUDE.md with template references to GitHub repository
- Cleaned up project structure for better clarity
- Updated documentation organization

### Removed
- Removed embedded templates from CLAUDE.md (now referenced externally)
- Removed unnecessary compatibility layers
- Removed overly complex documentation structure

## [1.0.1] - 2025-01-31

### Added
- Error Handling Protocol section in README documentation (both CN and EN versions)
- Version synchronization between CLAUDE.md and README files
- CHANGELOG.md for tracking version history

### Changed
- Enhanced error handling descriptions in safety features section
- Updated version numbers to 1.0.1 across all documentation

### Fixed
- Documentation consistency between CLAUDE.md and README files
- Missing error handling protocol in user-facing documentation

## [1.0.0] - 2025-01-31

### Initial Release
- Core Kiro SPECS workflow system for Claude Code
- 7 essential commands (`/kiro start`, `/kiro next`, `/kiro info`, `/kiro save`, `/kiro end`, `/kiro git`, `/kiro change`)
- 4-phase development workflow (Requirements → Design → Tasks → Execution)
- Session recovery mechanism with continuation prompts
- Automatic safety protocols (database backup, Git branch management)
- Chinese language optimization for native speakers
- Comprehensive documentation in both Chinese and English
- SPECS document templates for requirements, design, and task planning