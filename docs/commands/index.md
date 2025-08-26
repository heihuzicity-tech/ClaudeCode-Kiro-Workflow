# Kiro SPECS 命令规则索引

## 概述
此目录包含基于 CLAUDE.md 的所有 Kiro SPECS 命令的详细规则定义。每个命令都有完整的执行流程、约束条件和错误处理协议。

**核心原则**：所有命令必须使用中文与用户交互。

## 命令列表

### 核心工作流命令
- [`/kiro start`](./kiro-start.md) - 启动新的 SPECS 工作流
- [`/kiro next`](./kiro-next.md) - 执行下一个未完成任务
- [`/kiro save`](./kiro-save.md) - 保存进度并生成会话提示符
- [`/kiro end`](./kiro-end.md) - 完成功能开发并合并

### 支持命令
- [`/kiro info`](./kiro-info.md) - 保存项目上下文信息
- [`/kiro git`](./kiro-git.md) - 立即提交当前更改
- [`/kiro change`](./kiro-change.md) - 返回规划工作流处理需求变更

## 通用执行协议

### 自动上下文加载协议
每个 `/kiro` 命令必须首先执行：
1. 检查项目根目录 - 验证 `.specs/` 文件夹是否存在
2. 加载项目信息 - 如果存在则自动读取 `.specs/project-info.md`
3. 加载当前上下文 - 检查活跃功能和进度
4. 目录安全 - 确保操作在正确的项目根目录中进行

### 错误处理协议
- 必须优雅地处理操作失败，不中断工作流
- 必须报告具体的错误信息
- 必须在错误期间保持文档状态一致性
- 应该为每种失败类型提供恢复建议
- 必须不进行破坏性操作，如果出现错误

## 文件结构
```
.specs/
├── {feature_name}/
│   ├── requirements.md     # 需求文档
│   ├── design.md          # 技术设计
│   ├── tasks.md           # 实现任务和进度追踪
│   ├── session_*.md       # 会话恢复文件 (例如 session_2.1.md)
│   └── summary.md         # 完成时生成的总结
├── project-info.md        # 基本项目信息
└── backups/db/           # 数据库备份
    └── {feature}_backup_{timestamp}.sql
```

## 版本信息
- 基于 CLAUDE.md 版本：1.0.1
- 最后更新：2025-01-31