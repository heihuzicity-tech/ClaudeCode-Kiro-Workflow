# Kiro Think Command Template

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
```