# Project Information Configuration Command

### KIRO_COMMAND_INFO
```
Configures project information and initializes Kiro workflow system with project context and .gitignore setup.

**Constraints:**
- The model MUST parse and process user-provided project information
- The model MUST create '.specs/project-info.md' with structured project details
- The model MUST configure appropriate .gitignore entries for .specs directory (first-time setup)
- The model MUST save project context for use in all subsequent workflow operations
- The model MUST include project description, technology stack, and key requirements
- The model MUST establish project baseline for feature development workflow
- The model MUST ensure project information is loaded automatically in future sessions
- The model MUST validate project information completeness
- The model MUST provide confirmation of successful project setup
- The model SHOULD detect existing project configurations and merge appropriately
- The model SHOULD include project structure and key directories in info
- The model MAY ask for additional clarification if project information is incomplete

## Error Handling
Error handling follows global constraints defined in CLAUDE.md
```

## Project Configuration Rules

### Context-Optimized Project Information Structure
**Constraints:**
- The model MUST structure project-info.md with essential information prioritized at top
- The model MUST organize project-info.md in the following layered structure:
  - ## Essential Info (基础信息 - 必读): Project type, tech stack, development stage (target < 300 tokens)
  - ## Technical Configuration (技术配置 - 按需): Framework details, build config, environment info
  - ## Project Background (项目背景 - 参考): Comprehensive description in collapsible section
- The model MUST limit essential info section to immediately actionable technical information
- The model MUST use collapsible sections for detailed configuration and background information
- The model MUST include project name and core technology stack in essential section
- The model MUST specify key requirements and constraints in essential section
- The model SHOULD include directory structure and organization in technical configuration
- The model SHOULD document development environment setup in technical configuration
- The model MAY include detailed testing and deployment information in collapsible background section

### .gitignore Configuration
**Constraints:**
- The model MUST add .specs/ directory patterns appropriately
- The model MUST exclude session.md from version control
- The model MUST exclude database backup files
- The model MUST preserve existing .gitignore entries

### Context Persistence
**Constraints:**
- The model MUST save project info to .specs/project-info.md
- The model MUST ensure automatic loading in future sessions
- The model MUST maintain project context across workflow operations
- The model MUST validate information completeness