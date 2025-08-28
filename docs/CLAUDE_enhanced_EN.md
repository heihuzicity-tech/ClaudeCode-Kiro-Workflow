# Kiro Workflow Global Rules Configuration
# These rules are extracted from project command documents to avoid repetition in each command

## 🔴 Core Common Rules

### 1. Language Rules
**All Kiro command user interactions must be in Chinese**
- Source: All kiro-*.md documents contain this rule
- Exceptions: Code, variable names, technical terms can be in English

### 2. Script Format Rules
**Only .sh scripts are allowed**
- Common rule for all commands
- Prohibited: .bat, .ps1, .cmd, PowerShell scripts
- Windows execution: Run .sh via Git Bash
- All tests and scripts must use bash/shell

### 3. Git Branch Rules
**Direct development on main/master branches is prohibited**
- Source: /kiro-start.md, /kiro-end.md
- Use feature/[name] branches for development
- Merge via PR/merge after completion

### 4. Tool Usage Priority
**Prefer advanced tools over raw commands**
- Source: Tool Coordination sections in multiple command documents
- File search: Use Glob instead of find (Glob handles path separators automatically)
- Content search: Use Grep instead of bash grep
- File listing: Use LS instead of ls (LS requires absolute paths)
- File reading: Use Read instead of cat (Read handles encoding automatically)
- Bulk editing: Use MultiEdit instead of multiple Edits

### 5. Port Conflict Handling
**Ask user when encountering port conflicts**
- Applies to all service startup scenarios
- Prohibited: Automatically changing port numbers
- Prompt user to kill the process occupying the port
- Must wait for user decision on how to proceed

### 6. Service Management Scripting
**Use shell scripts to manage services instead of direct commands**
- Applies to all service start, stop, restart scenarios
- Create `.sh` scripts to manage service lifecycle
- Scripts can include: starting services, checking ports, handling errors
- Example: create `service.sh` or `start.sh` instead of directly running `npm start`
- Service management scripts go in project root or `scripts/` directory (not .specs)

### 7. Path Handling Rules
**Cross-platform path handling standards**
- Windows environment: Use backslash `\` or double backslash `\\`
- Prefer absolute paths: Use full paths like `E:\workspace\project\.specs`
- Avoid mixing: Don't mix `/` and `\` in the same path
- Filename standards: Avoid Chinese and special characters, use kebab-case
- Encoding consistency: All files use UTF-8 encoding

## 🟡 Project Structure Standards

### Standard SPECS Directory Structure
```
.specs/
├── {feature-name}/     # Feature directory (kebab-case)
│   ├── requirements.md # Requirements document
│   ├── design.md       # Design document  
│   ├── tasks.md        # Task list
│   ├── scripts/        # Shell scripts (all .sh scripts)
│   ├── tests/          # Test files
│   ├── docs/           # Documentation and analysis reports
│   └── temp/           # Temporary files
├── session.md          # Current session
└── project-info.md     # Project information
```

### File Placement Rules
**File organization during development**
- **Project files** (permanent):
  - Service management scripts → project root or `scripts/`
  - Unit tests → project's `tests/` or `__tests__/` directory
  - Configuration files → project root
- **Temporary files** (development process):
  - Test scripts → `.specs/{feature}/scripts/` (must be .sh)
  - Analysis documents → `.specs/{feature}/docs/`
  - Debug files → `.specs/{feature}/temp/`
  - Feature tests → `.specs/{feature}/tests/`

## ⚠️ Common Issue Prevention

### Avoiding Path Handling Errors
1. **Never use** `find`, `ls`, `cat` and other Unix commands
2. **Always use** Claude Code native tools (Glob, LS, Read)
3. **Path examples**:
   - ❌ Wrong: `./specs`, `find . -name`
   - ✅ Correct: `Glob("**/.specs")`, `LS("E:\\workspace\\project")`

### Avoiding Encoding Issues
1. **File naming**: Only use English, numbers, hyphens
2. **Directory naming**: Use kebab-case (user-auth, payment-system)
3. **Prohibited**: Chinese, spaces, special characters

## 🟢 Common Behaviors During Command Execution

### /kiro-load Enhancement
**Should reload CLAUDE.md during execution**
- Purpose: Prevent rule loss after /clear
- Ensures rules remain effective in any situation

### Common Patterns for All Commands
1. Read relevant SPECS documents
2. Interact with users in Chinese
3. Create files in correct directories
4. Follow Git branch strategy

## 📝 Note

This file only contains **commonly repeated rules** extracted from actual project documents.
For specific command behaviors, refer to individual command documents in `.claude/commands/`.