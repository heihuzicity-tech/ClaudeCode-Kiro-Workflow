# Deep Analysis Command

### KIRO_COMMAND_THINK
```
Activates multi-level deep analysis mode for complex problem solving, requirement changes, and comprehensive solution exploration with automatic documentation.

**Constraints:**
- The model MUST activate specified thinking level (v1/v2/v3) based on user input
- The model MUST perform systematic multi-angle analysis of the presented problem
- The model MUST analyze impacts on existing requirements, design, and task documents
- The model MUST provide structured recommendations with clear rationale
- The model MUST present analysis results and proposed solutions before execution
- The model MUST request explicit user confirmation before implementing any changes
- The model MUST update affected SPECS documents (requirements.md, design.md, tasks.md) if approved
- The model MUST preserve completed task status while incorporating new requirements
- The model MUST automatically save analysis results to docs/ directory with timestamps
- The model MUST maintain consistency across all SPECS documents after changes
- The model MUST offer to return to previous workflow states if major changes are needed
- The model MUST provide implementation impact assessment for proposed changes
- The model MUST support requirement change management without losing existing progress
- The model SHOULD compare multiple solution alternatives when appropriate
- The model SHOULD highlight trade-offs and decision criteria in analysis
- The model MAY escalate to higher thinking levels for particularly complex problems

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

## Deep Analysis Framework

### Multi-Level Thinking
**Constraints:**
- The model SHOULD use v1 for basic analysis with single perspective and straightforward solutions
- The model SHOULD use v2 for enhanced analysis with multiple perspectives and trade-off consideration
- The model SHOULD use v3 for comprehensive analysis with system-wide impacts and alternative scenarios

### Analysis Structure
**Constraints:**
- The model MUST include problem definition and context
- The model MUST perform current state assessment
- The model MUST analyze impact on existing SPECS
- The model MUST evaluate solution alternatives and trade-offs
- The model MUST provide recommended approach with rationale
- The model MUST assess implementation impact

### Change Management Rules
**Constraints:**
- The model MUST preserve completed task progress
- The model MUST maintain document consistency
- The model MUST provide clear before/after comparisons
- The model MUST support rollback to previous states
- The model MUST validate changes against original requirements

### Documentation Requirements
**Constraints:**
- The model MUST save analysis results with timestamps
- The model MUST document decision rationale
- The model MUST record alternative solutions considered
- The model MUST include implementation impact assessment