# Context优化实施方案

**日期**: 2025-09-05  
**项目**: ClaudeCode-Kiro-Workflow  
**优化目标**: 解决命令读取文档导致Context占用过高的问题  

## 🎯 核心问题

### 问题描述
当前Kiro命令在执行时采用"读取所有相关文档"的策略，导致Context使用率过高：
- kiro-load: 读取所有SPECS文档 + session.md + project-info.md (可能消耗20-30% Context)
- kiro-next: 读取所有SPECS文档 + 当前任务信息
- kiro-sync: 读取所有SPECS文档 + 项目文件扫描

### 优化目标
将命令执行的Context使用从20-30%降至5-10%，同时保持决策质量不变。

## 💡 解决方案：端到端优化

### 核心策略
**按需精确读取** + **精简化生成** = **端到端Context效率提升**

## 🔧 具体优化方案

### 1. 生成端优化

#### kiro-save 精简化生成
**当前问题**: 生成的session.md包含大量详细历史信息  
**优化方案**: 生成结构化的精简session.md

```markdown
# Session State - {timestamp}

## 🎯 Current Focus (核心状态 - 必读)
- Active Feature: {feature_name}
- Current Task: {current_task_id}
- Progress: {completion_percentage}
- Git Branch: {branch_name}

## 📋 Next Actions (关键行动 - 必读)
- [ ] {next_immediate_task}
- [ ] {next_planned_task}

## 🔧 Technical Context (技术上下文 - 按需)
- Key Dependencies: {essential_deps}
- Important Decisions: {critical_decisions}

## 📚 Detailed History (详细历史 - 归档)
<details>
<summary>Complete Session Log (折叠详细内容)</summary>
{detailed_session_information}
</details>
```

#### kiro-info 分层化生成
**当前问题**: project-info.md包含过多非关键信息  
**优化方案**: 生成分层的project-info.md

```markdown
# Project Information

## 🚀 Essential Info (基础信息 - 必读)
- Project Type: {project_type}
- Tech Stack: {main_technologies}
- Development Stage: {current_stage}

## ⚙️ Technical Configuration (技术配置 - 按需)
- Framework Details: {framework_info}
- Build Configuration: {build_info}
- Development Environment: {env_info}

## 📖 Project Background (项目背景 - 参考)
<details>
<summary>Detailed Background (折叠详细背景)</summary>
{comprehensive_project_description}
</details>
```

### 2. 读取端优化

#### kiro-load 选择性读取
**当前**: 读取完整的session.md + project-info.md + 所有SPECS文档  
**优化为**:
- 读取session.md的## Current Focus和## Next Actions部分
- 读取project-info.md的## Essential Info部分
- 仅读取当前活跃任务相关的SPECS文档部分

#### kiro-next 按需读取
**当前**: 读取所有SPECS文档，然后查找下一个任务  
**优化为**:
- 读取tasks.md定位下一个未完成任务
- 仅读取该任务相关的requirements和design部分
- 按需读取相关代码文件

#### kiro-sync 智能对比
**当前**: 读取所有SPECS文档 + 扫描所有项目文件  
**优化为**:
- 读取tasks.md获取任务状态
- 仅扫描tasks中提到的相关文件
- 智能差异对比，而非全量读取

## 📊 预期优化效果

### Context使用优化
- **session.md核心部分**: 从1-2k tokens → 300-500 tokens
- **project-info.md基础部分**: 从800-1k tokens → 200-300 tokens  
- **命令执行Context消耗**: 从20-30% → 5-10%
- **整体Context节省**: 约50-70%

### 质量保证
- 保持决策准确性不变
- 加快命令响应速度
- 提升用户体验和开发效率

## 🛠️ 实施计划

### Phase 1: 生成端优化
1. 修改kiro-save.md - 添加精简化生成规则
2. 修改kiro-info.md - 添加分层化生成规则

### Phase 2: 读取端优化  
1. 修改kiro-load.md - 添加选择性读取规则
2. 修改kiro-next.md - 添加按需读取规则
3. 修改kiro-sync.md - 添加智能对比规则

### Phase 3: 验证与调优
1. 测试优化效果
2. 确保功能完整性
3. 收集使用反馈并调优

## 🔒 风险控制

### 回滚机制
- 创建Git回滚点在优化开始前
- 保留原始规则作为备份
- 提供传统模式回退选项

### 兼容性保证
- 保持现有命令接口不变
- 确保现有项目继续正常工作
- 优化对用户透明，无需学习新操作

## 📝 成功标准

### 量化指标
- Context使用率从20-30%降至5-10%
- 命令响应时间提升30%+
- 保持决策准确率95%+

### 定性标准
- 用户体验无感知优化
- 功能完整性保持100%
- 系统稳定性不受影响

---

**结论**: 通过端到端的精简化生成和选择性读取，实现显著的Context使用效率提升，同时保持系统功能完整性和用户体验一致性。