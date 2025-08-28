# Kiro SPECS Command Rules Documentation

## Document Status
✅ **Complete** - All command rule files have been created and are fully synchronized with the .claude/commands directory

## Document Structure

### Core Command Files
| Filename | Description | CLAUDE.md Sync Status |
|----------|-------------|---------------------|
| `kiro-start.md` | Start new SPECS workflow | ✅ Fully synced |
| `kiro-next.md` | Execute next uncompleted task | ✅ Fully synced |
| `kiro-save.md` | Save progress and generate session prompt | ✅ Fully synced |
| `kiro-end.md` | Complete feature and merge to main | ✅ Fully synced |
| `kiro-info.md` | Save project context information | ✅ Fully synced |
| `kiro-git.md` | Immediately commit current changes | ✅ Fully synced |
| `kiro-status.md` | View project status and progress | ✅ Fully synced |
| `kiro-think.md` | Deep thinking and discussion mode | ✅ Fully synced |
| `kiro-load.md` | Auto-load saved session state | ✅ Fully synced |

### Auxiliary Files
| Filename | Description |
|----------|-------------|
| `index.md` | Command index and general protocols |
| `README.md` | Document status and overview (this file) |

## Synchronization Verification Checklist

### ✅ Core Rules Fully Matched
- [x] All command prefixes use `/kiro-` format (consistent with Claude Code filename recognition)
- [x] Chinese interaction requirement explicitly stated in each command
- [x] Automatic context loading protocol consistent in each command
- [x] Error handling protocol aligned with CLAUDE.md

### ✅ Execution Flow Fully Matched
- [x] `/kiro start` security and setup protocol (8 required steps)
- [x] `/kiro next` enhanced execution rules (bash-only, port handling, service scripts)
- [x] `/kiro save` session recovery mechanism and prompt format
- [x] `/kiro end` completion flow (4 required phases)
- [x] `/kiro git` commit rules (no merge constraint)
- [x] `/kiro info` project information save and auto-load
- [x] `/kiro status` status display format and warnings
- [x] `/kiro think` three-level thinking system
- [x] `/kiro load` timestamp verification and conflict handling

### ✅ Constraints Fully Matched
- [x] Mandatory user approval gates
- [x] Automatic task management (one task at a time)
- [x] Separated workflow and planning principles
- [x] Git operation safety constraints
- [x] Document state consistency maintenance

### ✅ Templates and Formats Fully Matched
- [x] Requirements document template (User Story + EARS format)
- [x] Design document template (6 required sections)
- [x] Task document template (progress tracking format)
- [x] Session recovery prompt format (exact match)
- [x] Commit message format standards

## Refactoring Quality Assurance

### Code Simplification Principles
- **Minimize Cognitive Load**: Each command file has clear structure, avoiding complex nesting
- **Eliminate Repetition**: Common protocols unified in `index.md`, referenced by command files
- **Pattern Consistency**: All command files use same structural pattern (description→syntax→protocol→flow→error handling→success criteria)

### Technical Debt Management
- **Documentation Sync Debt**: Established full sync with CLAUDE.md, avoiding document inconsistency
- **Maintainability Enhancement**: Each command in separate document for independent maintenance
- **Version Tracking**: Clearly marked as based on CLAUDE.md version 1.0.3

### SOLID Principles Application
- **Single Responsibility**: Each command file only defines rules for one command
- **Open/Closed**: Command rules extensible without modifying core protocols
- **Interface Segregation**: Each command has independent interface definition, not interdependent
- **Dependency Inversion**: All commands depend on abstract rules in CLAUDE.md, not concrete implementations

## Usage Guide

### Developer Usage
1. Check `index.md` for command overview
2. Check specific command files for detailed rules
3. Refer to CLAUDE.md for complete workflow

### Maintenance Guide
1. Any modifications to CLAUDE.md must be synchronized to corresponding command files
2. Maintain format consistency across all command files
3. Update version information when CLAUDE.md version changes

## Version Information
- **Created**: 2025-01-31
- **Based on Version**: CLAUDE.md v1.0.3
- **Document Status**: Complete and verified
- **Sync Status**: 100% synchronized

---

**Note**: This document collection is a refactoring and structuring of CLAUDE.md, without adding any content not present in CLAUDE.md, ensuring complete rule consistency.