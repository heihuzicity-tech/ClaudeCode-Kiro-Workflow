# ClaudeCode-Kiro-Workflow

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.1-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-purple.svg)

**A Specification-Driven Development workflow system optimized for Claude Code**

[English](./README.md) | [简体中文](./docs/README_CN.md)

</div>

## 🚀 Overview

ClaudeCode-Kiro-Workflow is a powerful AI-driven development workflow system designed specifically for Claude Code. Inspired by the SPECS (Specification-Driven Development) workflow from Kiro IDE, it brings structured, safe, and efficient development practices to Claude Code. The system guides developers through a proven process from requirements to implementation, featuring automatic database backups, Git branch isolation, and seamless session recovery.

This system uses Claude Code's `.claude/commands` mechanism, providing a simplified command system and native Chinese interaction support.

## 📚 References

- **Core Inspiration**: SPECS workflow system from Kiro IDE
- **Methodology**: Specification-Driven Development (SPECS)
- **Runtime**: Optimized for Claude Code (Anthropic's official CLI)
- **Command System**: Implemented using `.claude/commands` mechanism

## ✨ Key Features

1. **AI-Guided Workflow** - Automatic progression through Requirements → Design → Tasks → Execution → Completion
2. **Comprehensive Command System** - 9 powerful commands covering full development lifecycle
3. **Native Chinese Support** - Natural and fluent Chinese interaction with AI
4. **Automatic Database Backup** - Intelligent detection and proactive database backup before development
5. **Git Branch Isolation** - Automatic feature branch creation, protecting main branch
6. **Enhanced Session Management** - Persistent session saving to .specs/session.md with auto-recovery
7. **Real-time Progress Tracking** - Task status updates with automatic persistence
8. **Intelligent File Archiving** - Auto-organization of test/debug/temp files on project completion
9. **Deep Thinking Mode** - Three-level analysis system for complex problems (v1/v2/v3)
10. **Smart Confirmation System** - Commands execute directly, discussions require confirmation

## 📋 Commands

| Command | Description | Example |
|---------|-------------|---------|
| `/kiro-start [feature]` | Start new SPECS workflow (auto-guides through phases) | `/kiro-start user-login` |
| `/kiro-next` | Execute next uncompleted task | `/kiro-next` |
| `/kiro-info [info]` | Save project context to `.specs/project-info.md` | `/kiro-info "MySQL DB, React 18"` |
| `/kiro-status` | View current project status and progress | `/kiro-status` |
| `/kiro-think [v1/v2/v3]` | Deep thinking and discussion mode | `/kiro-think v2 architecture` |
| `/kiro-save` | Save progress and generate session file | `/kiro-save` |
| `/kiro-load` | Auto-load saved session state | `/kiro-load` |
| `/kiro-end` | Complete feature (update docs, generate summary, merge) | `/kiro-end` |
| `/kiro-git` | Immediately commit current changes | `/kiro-git` |

## 🔄 Workflow Phases

### Phase 1: Requirements Clarification
**Goal**: Transform vague ideas into structured requirement documents
- User story format: "As a [role], I want [feature], so that [benefit]"
- EARS (Easy Approach to Requirements Syntax) acceptance criteria
- Hybrid approach: Quick initial draft + targeted clarification of key issues
- **Key Constraints**: Limit initial questions to critical information (max 2-3), must obtain user approval after creating requirements.md

### Phase 2: Design & Research
**Goal**: Develop comprehensive design solution based on requirements
- Analyze existing codebase patterns and architecture
- Create technical design with decision rationale
- Research integration points and dependencies
- Support Mermaid diagrams in design documents
- **Key Constraints**: Include sections for overview, architecture, component interfaces, data models, error handling, testing strategy

### Phase 3: Task Planning
**Goal**: Create executable implementation plan based on requirements and design
- Break down into independently executable coding tasks
- Test-Driven Development (TDD) approach
- Use decimal notation (1.1, 1.2, 2.1) for task hierarchy
- Each task includes implementation details as sub-items
- **Key Constraints**: Focus only on tasks that involve writing, modifying, or testing code; avoid non-coding tasks

### Phase 4: Task Execution
**Goal**: Execute implementation tasks according to SPECS documents
- Strict single-task execution principle
- Must read all SPECS documents before execution
- Real-time progress updates in tasks.md
- Automatic task status synchronization
- **Enhanced Rules**: 
  - Always use bash/shell scripts, never bat/ps1/PowerShell
  - Ask user to kill conflicting processes instead of changing ports
  - Use service management scripts (npm run, make) over direct commands
- **Key Constraints**: Clear separation from planning phase, execute only one task at a time, wait for user instruction after completion

### Phase 5: Feature Completion
**Goal**: Clean project closure with intelligent archiving
- Mark session as completed with timestamp
- Archive scattered test/debug/temp files to `.specs/{feature}/`
- Move session.md to feature directory for history preservation
- Generate comprehensive summary document
- **Key Constraints**: Never delete session data, require confirmation for file archiving, protect system files

## 💡 Usage Examples

### Security Features Demo
```
User: /kiro-info "mysql -uroot -ppass123 -hlocalhost dbname=shop"

AI: Project information saved to .specs/project-info.md

User: /kiro-start payment-feature

AI: Starting payment feature development...

    Database configuration detected: mysql dbname=shop
    Do you want to backup the database? This will ensure your data safety (recommended: yes)

User: yes

AI: Executing database backup...
    Backup successful: .specs/backups/db/payment-feature_backup_20250126_143022.sql
    
    Checking Git status...
    Working directory clean, creating feature branch...
    Created and switched to branch: feature/payment-feature
    
    Current branch: feature/payment-feature
    Main branch is protected, all development will proceed in feature branch
    
    Starting requirements gathering phase...
```

### Starting New Feature
```
User: /kiro-info "MySQL database, React frontend, Node.js backend with JWT auth"

AI: Project information saved to .specs/project-info.md

User: /kiro-start user-authentication

AI: Starting user authentication development...
    
    Database configuration detected
    Do you want to backup the database? (recommended: yes)

User: yes

AI: Executing database backup...
    Created feature branch: feature/user-authentication
    
    Starting requirements gathering, please answer:
    1. Which login methods do you need?
    2. Do you need persistent login sessions?
```

### Executing Development Tasks
```
User: /kiro-next

AI: Reading SPECS documents...
    Current task: 1.1 Create user model
    
    Starting task execution...
    - Creating src/models/User.js
    - Adding field validation
    - Creating unit tests
    
    Task 1.1 completed! Continue with next task?

User: yes

AI: Executing task 1.2: Implement login endpoint...
```

### Session Recovery
```
User: /kiro-save

AI: Saving progress...
    Session state saved to: .specs/session.md
    Progress committed to git
    
    === Next Session Prompt ===
    I am developing user-login using Kiro SPECS
    Session state saved to: .specs/session.md
    
    Please load session with: /kiro-load
    Or manually continue with: /kiro-next
    =====================

--- New Session ---

User: /kiro-load

AI: Loading saved session...
    Feature: user-login
    Branch: feature/user-login
    Progress: Completed task 2.1, next is 2.2
    
    Ready to continue with: /kiro-next

User: /kiro-next

AI: Continuing task 2.2: Implement password validation...
```

### Check Project Status
```
User: /kiro-status

AI: ╔════════════════════════════════════════╗
    ║          KIRO Project Status           ║
    ╚════════════════════════════════════════╝
    
    📁 Project: /workspace/myproject
    🎯 Feature: user-authentication
    🌿 Branch: feature/user-authentication
    📊 Phase: Execution
    
    📝 Progress: ████████░░░░  5/10 (50%)
    
    ✅ Completed: 5 tasks
    🔄 Current: Task 2.3 - Create login endpoint
    ⏳ Remaining: 4 tasks
    
    💾 Session: ✅ Up to date
    📅 Last update: 2025-01-31 15:30
    
    Next: /kiro-next to continue
```

### Deep Thinking and Discussion
```
User: /kiro-think v2 how to optimize database performance

AI: 🤔 Deep Thinking: Database Performance Optimization
    Thinking Level: v2
    
    📊 Problem Analysis:
    - Current bottleneck: Slow query response times
    - Database size: 50GB with 10M records
    - Peak load: 1000 queries/second
    
    💡 Solutions:
    
    Solution A: Index Optimization
    ✅ Pros: Quick implementation, low risk
    ❌ Cons: Limited improvement for complex queries
    
    Solution B: Read Replicas + Caching
    ✅ Pros: Significant performance boost
    ❌ Cons: Higher complexity and cost
    
    🎯 Recommendation:
    Based on analysis, I recommend Solution B for long-term scalability.
    
    Shall I proceed with implementing Solution B? Need help with implementation?

User: Yes, proceed with Solution B

AI: Starting implementation...
    [Begins implementing the agreed solution]
```

## 📁 File Structure

```
.specs/
├── {feature_name}/
│   ├── requirements.md     # Requirements documentation
│   ├── design.md          # Technical design
│   ├── tasks.md           # Implementation tasks and progress tracking
│   ├── session-{date}.md  # Archived session files (preserved on /kiro-end)
│   ├── summary.md         # Generated on completion
│   ├── tests/            # Archived test files from project root
│   ├── scripts/          # Archived debug/utility scripts
│   ├── temp/             # Archived temporary files
│   ├── analysis/         # Archived analysis documents
│   └── docs/             # Additional documentation
├── project-info.md        # Basic project information
├── session.md            # Current active session (moved on /kiro-end)
└── backups/db/           # Database backups
    └── {feature}_backup_{timestamp}.sql
```

## 🔒 Security Mechanisms

### Automatic Database Backup
- **Smart Detection**: Automatically detects database configuration at startup
- **Proactive Reminder**: Prompts for backup when database config is found
- **Auto Execution**: Performs complete database backup upon confirmation
- **Backup Path**: `.specs/backups/db/{feature}_backup_{timestamp}.sql`
- **Zero Data Loss**: Ensures data safety during development

### Git Branch Isolation
- **Auto Feature Branch**: Each feature gets isolated branch `feature/[name]`
- **Main Branch Protection**: No direct operations on main branch during development
- **Status Check**: Ensures clean Git workspace before creating branch
- **Smart Merge**: Merges to main only after feature completion
- **Conflict Prevention**: Isolated development prevents code conflicts

### Document Integrity Protection
- **Atomic Operations**: Document updates either all succeed or all rollback
- **State Consistency**: Ensures requirements, design, tasks documents stay in sync
- **Progress Persistence**: Automatically saves task progress to prevent loss
- **Version Tracking**: All document changes automatically tracked in Git

### Error Recovery
- **Graceful Degradation**: Single operation failure doesn't affect overall flow
- **Smart Retry**: Automatic retry for network or temporary errors
- **State Recovery**: Resume from breakpoint after abnormal interruption
- **Detailed Logs**: Complete error information for troubleshooting

### Session Continuity Protection
- **Auto Progress Save**: `/kiro-save` generates complete session recovery file
- **Context Preservation**: New sessions can seamlessly continue previous work
- **Task State Persistence**: Completed tasks never lost
- **Cross-session Collaboration**: Supports team member handover

## 🎯 Command Features

### Core Workflow Commands
- **`/kiro-start [feature]`**: Start new feature development, auto-create branch and SPECS structure
- **`/kiro-next`**: Execute next task with automatic progress saving
- **`/kiro-end`**: Enhanced feature completion with session archiving, file organization, and intelligent cleanup

### Session Management (v1.0.3 Enhanced)
- **`/kiro-save`**: Save progress and persist to .specs/session.md
- **`/kiro-load`**: Auto-load session state, restore context
- **`/kiro-status`**: View project status with clean text output

### Development Support
- **`/kiro-info [info]`**: Set project information, auto-configure .gitignore
- **`/kiro-git`**: Quick code commit without updating progress documents
- **`/kiro-think [v1/v2/v3]`**: Deep thinking mode, replaced /kiro-change

## 🎨 Best Practices

### Workflow Adherence
1. **Trust AI Workflow**: Let AI guide you through optimal development process
2. **Provide Clear Requirements**: Clearer input leads to more accurate AI-generated documents
3. **Follow Approval Gates**: Each phase requires explicit approval before continuing
4. **Focus on Single Task**: Execute one task at a time, wait for confirmation

### Session Management
5. **Regular Progress Saves**: Use `/kiro-save` before ending sessions
6. **Use Session Prompts**: Start new sessions with generated prompts
7. **Configure Project Info**: Setup `/kiro-info` project information before first use

### Error Handling
8. **Understand Failures**: Check specific error messages when encountering issues
9. **Use Recovery Suggestions**: Follow AI-provided recovery recommendations
10. **Manage Requirement Changes**: Use `/kiro-change` for changes instead of direct modification

### Security Practices
11. **Database Backups**: Ensure database is backed up before development
12. **Branch Isolation**: Ensure working on correct feature branch
13. **Progressive Commits**: Use `/kiro-git` for regular code commits

## 🛠️ Installation

### Option A: Quick Installation (Recommended)
```bash
# Copy entire .claude folder to your project
cp -r .claude your-project/
```

### Option B: Custom Installation
If you already have `.claude` configurations:
1. Copy command files from `docs/commands/*.md`
2. Place them in your `.claude/commands/` directory
3. Ensure filenames match: `kiro-start.md`, `kiro-save.md`, etc.

### Start Using
```
/kiro-start [feature_name]
```

## 🤝 Contributing

We welcome contributions! Please submit Issues and Pull Requests:

- Report bugs or suggestions
- Improve documentation
- Share usage experiences
- Contribute code optimizations

## 📄 License

MIT License

## 🙏 Acknowledgments

- Thanks to Kiro IDE team for the SPECS workflow inspiration
- Thanks to Anthropic team for developing Claude Code platform
- Thanks to all users and contributors to this workflow system

## 🔗 Links

- [GitHub Project](https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow)
- [Project Website](https://www.heihuzicity.com)
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Report Issues](https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow/issues)

---

**Maintainer**: heihuzicity-tech  
**GitHub**: https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow  
**Website**: https://www.heihuzicity.com  
**Last Updated**: 2025-01-26  
**Version**: 1.0.2