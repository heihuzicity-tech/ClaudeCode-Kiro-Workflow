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
```
v1: Basic analysis - single perspective, straightforward solutions
v2: Enhanced analysis - multiple perspectives, trade-off consideration
v3: Comprehensive analysis - system-wide impacts, alternative scenarios
```

### Analysis Structure
```
1. Problem Definition and Context
2. Current State Assessment 
3. Impact Analysis on Existing SPECS
4. Solution Alternatives and Trade-offs
5. Recommended Approach with Rationale
6. Implementation Impact Assessment
```

### Change Management Rules
```
- MUST preserve completed task progress
- MUST maintain document consistency
- MUST provide clear before/after comparisons
- MUST support rollback to previous states
- MUST validate changes against original requirements
```

### Documentation Requirements
```
- MUST save analysis results with timestamps
- MUST document decision rationale
- MUST record alternative solutions considered
- MUST include implementation impact assessment
```