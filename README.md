# ClaudeCode-Kiro-Workflow

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.6-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-purple.svg)

**专为 Claude Code 优化的规范驱动开发工作流系统**

[简体中文](./README.md) | [English](./docs/README_EN.md)

</div>

## 🚀 概述

ClaudeCode-Kiro-Workflow 是专为 Claude Code 设计的 AI 驱动开发工作流系统。灵感来源于 Kiro IDE 的 SPECS（规范驱动开发）工作流，将这一成熟的开发方法论引入到 Claude Code 中。系统引导开发者完成从需求到实现的结构化流程，具备自动数据库备份、Git 分支隔离、会话无缝恢复等安全特性，确保开发过程高效且安全。

本系统使用 Claude Code 的 `.claude/commands` 机制，提供简化的命令系统和原生中文交互支持。

## 参考来源

- **核心灵感**：Kiro IDE 的 SPECS 工作流系统
- **方法论**：规范驱动开发（Specification-Driven Development）
- **运行环境**：针对 Claude Code（Anthropic 官方 CLI）优化
- **命令系统**：通过复制 `docs/commands/` 到项目的 `.claude/commands/` 实现

## 核心特性

1. **AI 引导工作流**：自动推进 需求 → 设计 → 任务 → 执行 各阶段
2. **极简命令系统**：仅需使用 10 个核心命令
3. **中文原生交互**：与 AI 进行自然流畅的中文对话
4. **数据库自动备份**：开发前智能检测并主动备份数据库，防止数据丢失
5. **Git 分支隔离**：自动创建功能分支，保护主分支不受影响
6. **会话连续性**：跨会话无缝保持项目上下文，支持断点恢复
7. **进度实时跟踪**：任务状态实时更新，自动持久化保存

## 命令参考

| 命令                     | 描述                                      | 使用示例                                 |
| ------------------------ | ----------------------------------------- | ---------------------------------------- |
| `/kiro-start [功能名]`   | 启动新的 SPECS 工作流（自动引导各阶段）   | `/kiro-start 用户登录`                   |
| `/kiro-next`             | 执行下一个未完成任务                      | `/kiro-next`                             |
| `/kiro-info [信息]`      | 保存项目上下文到 `.specs/project-info.md` | `/kiro-info "MySQL数据库，React 18前端"` |
| `/kiro-status`           | 查看当前项目状态和进度                    | `/kiro-status`                           |
| `/kiro-think [v1/v2/v3]` | 深度思考和讨论模式                        | `/kiro-think v2 架构设计`                |
| `/kiro-save`             | 保存进度并生成会话文件                    | `/kiro-save`                             |
| `/kiro-load`             | 自动加载保存的会话状态                    | `/kiro-load`                             |
| `/kiro-end`              | 完成功能（更新文档、生成总结、合并分支）  | `/kiro-end`                              |
| `/kiro-git`              | 立即提交当前更改                          | `/kiro-git`                              |
| `/kiro-change`           | 同步讨论结果到SPECS文档                   | `/kiro-change`                           |

## 工作流阶段

### 阶段 1：需求澄清
**目标**：将模糊想法转化为结构化需求文档
- 用户故事格式："作为[角色]，我想要[功能]，以便[好处]"
- EARS（易用需求语法）格式的验收标准
- 混合方式：快速生成初稿 + 针对性澄清关键问题
- **关键约束**：限制初始问题到关键信息（最多2-3个），创建requirements.md后必须获得用户批准

### 阶段 2：设计与研究
**目标**：基于需求开发综合设计方案
- 分析现有代码库模式和架构
- 创建包含决策理由的技术设计方案
- 研究集成点和依赖关系
- 支持 Mermaid 图表的设计文档
- **关键约束**：包含总览、架构、组件接口、数据模型、错误处理、测试策略等章节

### 阶段 3：任务规划
**目标**：基于需求和设计创建可执行的实施计划
- 分解为可独立执行的编码任务
- 测试驱动开发（TDD）方法
- 使用小数点标记法（1.1、1.2、2.1）表示任务层次
- 每个任务包含实施细节的子项目
- **关键约束**：只关注编写、修改或测试代码的任务，避免非编码任务

### 阶段 4：任务执行
**目标**：按照SPECS文档执行实施任务
- 严格的单任务执行原则
- 执行前必须读取所有SPECS文档
- 实时更新 tasks.md 中的进度
- 自动任务状态同步
- **增强规则**：
  - 始终使用 bash/shell 脚本，禁止 bat/ps1/PowerShell
  - 端口冲突时询问用户是否杀死进程，而非更改端口
  - 优先使用服务管理脚本（npm run, make）而非直接命令
- **关键约束**：与规划阶段明确分离，一次只执行一个任务，完成后等待用户指令

### 阶段 5：功能完成
**目标**：智能归档的清洁项目收尾
- 标记会话为已完成并加上时间戳
- 归档散落的测试/调试/临时文件到 `.specs/{feature}/`
- 移动 session.md 到功能目录以保存历史
- 生成综合总结文档
- **关键约束**：永不删除会话数据，文件归档需要确认，保护系统文件

## 使用示例

### 开始新功能开发
```
用户: /kiro-info "MySQL数据库，React前端，Node.js后端，使用JWT认证"

AI: 项目信息已保存到 .specs/project-info.md

用户: /kiro-start 用户认证系统

AI: 正在启动用户认证系统开发...
    
    检测到数据库配置
    是否需要备份数据库？(建议：是)

用户: 是

AI: 执行数据库备份...
    已创建功能分支：feature/用户认证系统
    
    开始需求收集，请回答以下问题：
    1. 需要支持哪些登录方式？
    2. 是否需要记住登录状态？
```

### 执行开发任务
```
用户: /kiro-next

AI: 读取 SPECS 文档...
    当前任务：1.1 创建用户模型
    
    开始执行任务...
    - 创建 src/models/User.js
    - 添加字段验证
    - 创建单元测试
    
    任务 1.1 已完成！是否继续下一个任务？

用户: 是

AI: 执行任务 1.2：实现登录接口...
```

### 会话保存和恢复
```
用户: /kiro-save

AI: 我正在使用 Kiro SPECS 开发用户登录功能
当前阶段：执行阶段
最新进度：已完成任务 2.1 - 创建用户模型

SPECS 文档：
- 需求：.specs/用户登录/requirements.md
- 设计：.specs/用户登录/design.md
- 任务：.specs/用户登录/tasks.md

主要文件：
- src/models/User.js - 用户数据模型
- src/routes/auth.js - 认证路由

当前目录：./

请继续：/kiro-load

--- 新会话 ---

用户: /kiro-load

AI: 已加载会话状态
功能：用户登录
分支：feature/用户登录
当前任务：2.2 - 实现登录接口

准备继续：/kiro-next

用户: /kiro-next

AI: 继续执行任务 2.2：实现密码验证...
```

### 处理需求变更
```
用户: /kiro-think

AI: 请描述需要变更的内容：

用户: 客户要求增加手机号登录方式

AI: 了解了，需要增加手机号登录。分析影响：
    - 需求文档：添加手机号登录需求
    - 设计文档：更新登录接口设计
    - 任务列表：新增3个相关任务
    
    分析完成。请使用 /kiro-change 同步这些变更到文档。

用户: /kiro-change

AI: 正在分析讨论内容并同步到SPECS文档...
    检测到需要更新：requirements.md, design.md, tasks.md
    
    变更预览：
    [显示具体的before/after对比]
    
    是否确认应用这些变更？

用户: 确认

AI: 正在应用变更...
    ✅ 已更新 requirements.md
    ✅ 已更新 design.md  
    ✅ 已更新 tasks.md（已完成任务状态保持不变）
    
    文档同步完成，请使用 /kiro-next 继续开发
```

### 完成功能开发
```
用户: /kiro-end

AI: 功能开发完成，正在整理项目...
    
    已完成：
    - 会话文件归档到 .specs/用户认证系统/
    - 临时文件清理完成
    - 测试文件归档完成
    - 生成功能总结文档
    
    分支合并：
    是否合并 feature/用户认证系统 到 main 分支？(建议：是)

用户: 是

AI: 分支已合并到 main
    用户认证系统开发完成！
    
    项目清理完成，所有文件已归档
    感谢使用 Kiro 工作流！
```

## 文件结构

```
.specs/
├── {功能名称}/
│   ├── requirements.md     # 需求规格文档
│   ├── design.md          # 技术设计方案
│   ├── tasks.md           # 实施任务列表及进度跟踪
│   ├── session-{日期}.md  # 归档的会话文件（/kiro-end 时保存）
│   ├── summary.md         # 完成时生成的总结
│   ├── tests/            # 从项目根目录归档的测试文件
│   ├── scripts/          # 归档的调试/工具脚本
│   ├── temp/             # 归档的临时文件
│   ├── analysis/         # 归档的分析文档
│   └── docs/             # 额外的文档
├── project-info.md        # 基本项目信息
├── session.md            # 当前活动会话（/kiro-end 时移动）
└── backups/db/           # 数据库备份
    └── {功能名}_backup_{时间戳}.sql
```

## 安全保障机制

### 数据库自动备份
- **智能检测**：启动开发时自动检测数据库配置
- **主动提醒**：发现数据库配置后主动询问是否备份
- **自动执行**：确认后自动执行完整数据库备份
- **备份路径**：`.specs/backups/db/{feature}_backup_{timestamp}.sql`
- **零数据丢失**：确保开发过程中的数据安全

### Git 分支隔离保护
- **自动创建功能分支**：每个功能独立分支 `feature/[name]`
- **主分支保护**：开发过程中不直接操作主分支
- **状态检查**：确保 Git 工作区干净后才创建分支
- **智能合并**：功能完成后才合并到主分支
- **冲突预防**：隔离开发避免代码冲突

### 文档完整性保护
- **原子操作**：文档更新要么全部成功，要么全部回滚
- **状态一致性**：确保 requirements、design、tasks 文档同步
- **进度持久化**：自动保存任务进度，防止丢失
- **版本追踪**：所有文档变更自动纳入 Git 管理

### 错误恢复机制
- **优雅降级**：单个操作失败不影响整体流程
- **智能重试**：网络或临时错误自动重试
- **状态恢复**：异常中断后可从断点继续
- **详细日志**：保留完整错误信息便于排查

### 会话连续性保护
- **自动保存进度**：`/kiro-save` 生成完整会话恢复文件
- **上下文保持**：新会话可无缝继续之前的工作
- **任务状态持久化**：已完成任务永不丢失
- **跨会话协作**：支持团队成员接续开发

## 命令特性

### 核心工作流命令
- **`/kiro-start [功能名]`**：启动新功能开发，自动创建分支和SPECS结构
- **`/kiro-next`**：执行下一个任务，自动保存进度
- **`/kiro-end`**：增强的功能完成，包含会话归档、文件整理和智能清理

### 会话管理命令 (v1.0.3 新增)
- **`/kiro-save`**：保存进度并持久化到 .specs/session.md
- **`/kiro-load`**：自动加载会话状态，恢复上下文
- **`/kiro-status`**：查看项目状态（简洁文字输出）

### 辅助开发命令
- **`/kiro-info [信息]`**：设置项目基础信息，自动配置 .gitignore
- **`/kiro-git`**：快速提交代码更改，不更新进度文档
- **`/kiro-think [v1/v2/v3]`**：深度思考模式，用于需求变更分析
- **`/kiro-change`**：同步 /kiro-think 讨论结果到SPECS文档

## 最佳实践

### 工作流遵循
1. **相信 AI 工作流**：让 AI 引导您完成最优开发流程
2. **提供清晰需求**：输入越清晰，AI 生成的文档越准确
3. **遵循审批关卡**：每个阶段完成后需明确批准才能继续
4. **专注单一任务**：一次只执行一个任务，完成后等待确认

### 会话管理
5. **定期保存进度**：会话结束前使用 `/kiro-save` 保存
6. **使用会话提示**：新会话开始时使用生成的提示词
7. **项目信息配置**：首次使用前配置 `/kiro-info` 项目信息

### 错误处理
8. **理解失败原因**：遇到错误时查看具体错误信息
9. **使用恢复建议**：按照AI提供的恢复建议处理问题
10. **需求变更管理**：需求变化时使用 `/kiro-think` 分析，然后用 `/kiro-change` 同步

### 安全实践
11. **数据库备份**：开发前确保数据库已备份
12. **分支隔离**：确保在正确的功能分支上工作
13. **渐进提交**：使用 `/kiro-git` 定期提交代码更改

## 安装配置

### 安装步骤
1. **复制命令文件到项目**
   ```bash
   # 创建 .claude 目录
   mkdir -p your-project/.claude
   
   # 复制所有命令文件
   cp -r docs/commands your-project/.claude/
   ```

2. **复制全局规则文件**
   ```bash
   # 复制全局规则配置
   cp CLAUDE.md your-project/
   ```

3. **验证安装**
   ```bash
   # 在项目目录中测试
   cd your-project
   # 在 Claude Code 中运行
   /kiro-info "项目基本信息"
   ```

### 文件结构
安装后您的项目应该有：
```
your-project/
├── CLAUDE.md                    # 全局规则配置
└── .claude/
    └── commands/               # Kiro 命令定义
        ├── kiro-start.md
        ├── kiro-next.md
        ├── kiro-save.md
        ├── kiro-load.md
        ├── kiro-end.md
        ├── kiro-git.md
        ├── kiro-info.md
        ├── kiro-status.md
        ├── kiro-think.md
        └── index.md
```

### 开始使用
```
/kiro-start [功能名]
```

## 参与贡献

欢迎提交 Issue 和 Pull Request！我们期待您的贡献：

- 报告问题或建议
- 改进文档
- 分享使用经验
- 贡献代码优化

## 开源协议

MIT License

## 致谢

- 感谢 Kiro IDE 团队提供的 SPECS 工作流灵感
- 感谢 Anthropic 团队开发的 Claude Code 平台
- 感谢所有使用和贡献此工作流系统的开发者

## 相关链接

- [GitHub 项目](https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow)
- [项目主页](https://www.heihuzicity.com)
- [Claude Code 官方文档](https://docs.anthropic.com/en/docs/claude-code)
- [问题反馈](https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow/issues)

---

**项目维护者**: heihuzicity-tech  
**GitHub**: https://github.com/heihuzicity-tech/ClaudeCode-Kiro-Workflow  
**网站**: https://www.heihuzicity.com  
**最后更新**: 2025-01-26  
**版本号**: 1.0.6