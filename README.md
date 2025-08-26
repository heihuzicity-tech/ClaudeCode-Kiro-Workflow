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

1. **AI-Guided Workflow** - Automatic progression through Requirements → Design → Tasks → Execution
2. **Minimal Command System** - Only 7 essential commands to remember
3. **Native Chinese Support** - Natural and fluent Chinese interaction with AI
4. **Automatic Database Backup** - Intelligent detection and proactive database backup before development
5. **Git Branch Isolation** - Automatic feature branch creation, protecting main branch
6. **Session Continuity** - Seamless context preservation across sessions with breakpoint recovery
7. **Real-time Progress Tracking** - Task status updates with automatic persistence

## 📋 Commands

| Command | Description | Example |
|---------|-------------|---------|
| `/kiro-start [feature]` | Start new SPECS workflow (auto-guides through phases) | `/kiro-start user-login` |
| `/kiro-next` | Execute next uncompleted task | `/kiro-next` |
| `/kiro-info [info]` | Save project context to `.specs/project-info.md` | `/kiro-info "MySQL DB, React 18"` |
| `/kiro-save` | Save progress and generate session file | `/kiro-save` |
| `/kiro-end` | Complete feature (update docs, generate summary, merge) | `/kiro-end` |
| `/kiro-git` | Immediately commit current changes | `/kiro-git` |
| `/kiro-change` | Return to planning workflow for requirement changes | `/kiro-change` |

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
- **Key Constraints**: Clear separation from planning phase, execute only one task at a time, wait for user instruction after completion

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
    Session file generated: .specs/user-login/session_2.1.md
    Progress committed to git
    
    === Next Session Prompt ===
    I am developing user-login using Kiro SPECS
    Please read .specs/user-login/session_2.1.md to continue development
    
    Continue with: /kiro-next
    =====================

--- New Session ---

User: I am developing user-login using Kiro SPECS
      Please read .specs/user-login/session_2.1.md to continue development

AI: Loaded project progress. You're developing user-login feature,
    completed task 2.1, next task is 2.2.

User: /kiro-next

AI: Continuing task 2.2: Implement password validation...
```

### Handling Requirement Changes
```
User: /kiro-change

AI: Please describe what needs to be changed:

User: Client requires phone number login support

AI: Understood, adding phone number login. Analyzing impact:
    - Requirements document: Add phone login requirement
    - Design document: Update login interface design
    - Task list: Add 3 related tasks
    
    Proceed with this plan?

User: yes

AI: Updating documents...
    Updated requirements.md
    Updated design.md
    Updated tasks.md (preserved completed task status)
    
    Please use /kiro-next to continue development
```

## 📁 File Structure

```
.specs/
├── {feature_name}/
│   ├── requirements.md     # Requirements documentation
│   ├── design.md          # Technical design
│   ├── tasks.md           # Implementation tasks and progress tracking
│   ├── session_*.md       # Session recovery files (e.g., session_2.1.md)
│   └── summary.md         # Generated on completion
├── project-info.md        # Basic project information
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

- **`/kiro-save`**: Saves progress and generates session recovery file, solving AI session context limitations
- **`/kiro-end`**: Completes feature development, generates summary document and merges to main branch
- **`/kiro-git`**: Quick code commit without updating progress documents
- **`/kiro-change`**: Intelligently handles requirement changes, automatically updates related documents while preserving completed status

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