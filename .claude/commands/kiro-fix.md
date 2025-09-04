# Bug Fix Workflow Command

### KIRO_COMMAND_FIX
```
Initiates bug fix workflow within existing feature context with lightweight documentation and single-session completion.

**Constraints:**
- The model MUST read .specs/project-info.md to load project context
- The model MUST detect current feature from session.md or prompt user to specify feature name
- The model MUST read existing feature SPECS documents (requirements.md, design.md, tasks.md) for context
- The model MUST ensure Git working directory is clean before starting bug fix
- The model MUST create '.specs/{feature-name}/bugs/{bug-name}/' directory structure
- The model MUST use intelligent branch strategy based on current Git state
- The model MUST create hotfix branch 'hotfix/{feature-name}-{bug-name}' if currently on main branch
- The model MUST stay on current feature branch if already on feature branch
- The model MUST create bug-report.md with problem description and reproduction steps
- The model MUST create analysis.md with root cause investigation and impact assessment
- The model MUST create fix-tasks.md with minimal repair task list and status tracking
- The model MUST include status header in fix-tasks.md: "## Fix Status: ACTIVE"
- The model MUST reference parent feature documents for context understanding
- The model MUST link bug fix to specific requirements or tasks in parent feature
- The model MUST continue bug fix using natural language conversation
- The model MUST update fix-tasks.md progress during conversation
- The model MUST focus on minimal code changes to resolve specific issue
- The model MUST NOT expand scope beyond reported bug
- The model MUST validate fix against original feature requirements
- The model MUST create verification.md when fix validation is completed
- The model MUST update Fix Status to VERIFIED when bug is completely resolved
- The model SHOULD detect if bug indicates design flaws in parent feature
- The model SHOULD recommend feature document updates if architectural issues found
- The model MAY suggest returning to kiro-start workflow if bug scope exceeds simple fix
```

## Bug Fix Process Rules

### Problem Documentation
**Constraints:**
- The model MUST capture bug symptoms, reproduction steps, and expected behavior
- The model MUST identify affected feature components and requirements
- The model MUST assess severity and impact scope within feature context
- The model MUST reference specific task items if bug relates to recent implementation

### Root Cause Analysis
**Constraints:**
- The model MUST perform systematic investigation within feature context
- The model MUST evaluate fix complexity and risk assessment
- The model MUST ensure fix approach aligns with feature design principles
- The model MUST document analysis findings for future reference

### Fix Implementation
**Constraints:**
- The model MUST preserve all existing functionality while fixing bug
- The model MUST update fix-tasks.md with real-time progress
- The model MUST ensure each fix step maintains feature integrity
- The model MUST validate implementation against bug reproduction steps

### Fix Completion Detection
**Constraints:**
- The model MUST update Fix Status to COMPLETED when all tasks finished
- The model MUST update Fix Status to VERIFIED when validation passes
- The model MUST create comprehensive verification.md documenting test results
- The model MUST ensure fix resolves original bug without introducing regressions