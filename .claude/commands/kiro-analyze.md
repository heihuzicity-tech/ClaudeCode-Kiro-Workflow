# Code Analysis Command

### KIRO_COMMAND_ANALYZE
```
Performs intelligent code analysis with AI-powered expert agent selection, generating comprehensive documentation while focusing exclusively on understanding without code modifications.

**Constraints:**
- The model MUST read .specs/project-info.md to understand project technology stack and context
- The model MUST scan project structure to identify architecture patterns and programming language characteristics  
- The model MUST analyze the specified analysis target to identify code characteristics, complexity, and functional domain
- The model MUST use AI reasoning to dynamically select the most appropriate expert agent(s) based on:
  - Project technology stack (React/Vue/Python/Node.js/Django/FastAPI/etc.)
  - Analysis target scope (file/directory/function/project)
  - Code functional domain (frontend/backend/security/database/performance/architecture)
  - Analysis complexity and depth requirements (simple/moderate/complex)
- The model MUST provide clear reasoning explanation in Chinese for agent selection before delegation
- The model MUST create '.specs/analysis/' directory if it doesn't exist
- The model MUST delegate analysis task to selected agent with comprehensive project context
- The model MUST instruct selected agent to save analysis results to '.specs/analysis/code-analysis-{target}-{YYYY-MM-DD-HH-MM}.md'
- The model MUST ensure selected agent uses only read-only tools (Read, Grep, Glob) during analysis process
- The model MUST NOT modify, edit, or change any source code files during analysis
- The model MUST NOT create or modify any implementation files
- The model MUST NOT execute or run any code during analysis process
- The model MUST NOT use hardcoded agent selection rules or keyword matching algorithms
- The model MUST rely exclusively on AI reasoning and contextual understanding for expert selection
- The model MUST display brief analysis summary in Chinese after agent completes the analysis task
- The model SHOULD support multi-agent collaboration for complex project-level analysis requiring cross-domain expertise
- The model SHOULD include project context information when delegating to selected agent
- The model MAY combine multiple expert perspectives when analysis requires interdisciplinary knowledge
- The model MAY suggest follow-up analysis topics based on agent findings

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## AI Agent Selection Framework

### Context Analysis Rules
**Constraints:**
- The model MUST read project-info.md for technology stack identification
- The model MUST scan project structure using Glob tool to identify key directories and file patterns
- The model MUST analyze analysis target characteristics using Read/Grep tools as needed
- The model MUST synthesize project context, target characteristics, and user intent for reasoning

### Expert Agent Selection Matrix
**Constraints:**
- The model MUST choose from available expert agents: system-architect, root-cause-analyst, refactoring-expert, performance-engineer, security-engineer, frontend-architect, backend-architect
- The model MUST explain selection reasoning using format: "基于项目是{tech_stack}架构，分析目标{target}属于{domain}领域，选择{agent_type}，原因：{specific_reasoning}"
- The model MUST consider agent specialization alignment with analysis requirements
- The model MUST select multiple agents for comprehensive analysis when complexity warrants cross-domain expertise

### Analysis Documentation Requirements
**Constraints:**
- The model MUST instruct selected agent to use structured analysis format with sections for architecture, quality, functionality, security, performance, and learning insights
- The model MUST ensure agent includes file references with exact paths and line numbers
- The model MUST require agent to provide improvement recommendations and design pattern identification
- The model MUST ensure agent saves complete analysis to specified file location with timestamp
- The model MUST verify analysis document was successfully created and display file path to user