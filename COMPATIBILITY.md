# Compatibility Guide

## 🎯 Supported Environments

### Claude Code (Native)
- **Version**: All versions
- **Commands**: `/kiro [command]` 
- **Configuration**: `CLAUDE.md` in project root
- **Status**: ✅ Fully supported

### SuperClaude
- **Version**: Latest
- **Commands**: `/kiro-[command]`
- **Configuration**: `.claude/commands/` directory
- **Status**: ✅ Fully supported

## 📦 Installation

### For Claude Code
1. Copy `CLAUDE.md` to your project root
2. Commands are immediately available

### For SuperClaude
1. Copy entire `.claude/` directory to your project
2. Commands are registered automatically
3. Use colon syntax: `/kiro-start` instead of `/kiro start`

## 🔄 Command Mapping

| Claude Code | SuperClaude | Function |
|-------------|-------------|----------|
| `/kiro start` | `/kiro-start` | Start SPECS workflow |
| `/kiro next` | `/kiro-next` | Execute next task |
| `/kiro info` | `/kiro-info` | Save project info |
| `/kiro save` | `/kiro-save` | Save progress |
| `/kiro end` | `/kiro-end` | Complete feature |
| `/kiro git` | `/kiro-git` | Quick commit |
| `/kiro change` | `/kiro-change` | Handle changes |

## 🛠️ Configuration Files

```
your-project/
├── CLAUDE.md                 # For Claude Code
└── .claude/                  # For SuperClaude
    └── commands/
        ├── kiro-start.md
        ├── kiro-next.md
        ├── kiro-info.md
        ├── kiro-save.md
        ├── kiro-end.md
        ├── kiro-git.md
        └── kiro-change.md
```

## ⚙️ Behavior Differences

Both implementations follow the same SPECS workflow:
- Same phase progression (Requirements → Design → Tasks → Execution)
- Same safety protocols (Git branches, database backups)
- Same Chinese communication
- Same document generation

The only difference is the command syntax:
- Claude Code: Space-separated (`/kiro start`)
- SuperClaude: Colon-separated (`/kiro-start`)

## 🔍 Troubleshooting

### Commands not recognized in Claude Code
- Ensure `CLAUDE.md` is in project root
- Check file is named exactly `CLAUDE.md` (case-sensitive)

### Commands not recognized in SuperClaude
- Ensure `.claude/commands/` directory exists
- Check all `kiro-*.md` files are present
- Use colon syntax (`/kiro-command`)

## 📝 Notes

- Both systems can coexist in the same project
- SPECS documents (`.specs/` directory) are identical for both
- Session prompts work across both systems
- All features are fully compatible