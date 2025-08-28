# /kiro-think - Deep Thinking and Discussion

## Triggers
- Complex technical problems requiring deep analysis
- Architecture design discussions
- Performance optimization planning
- Algorithm selection and comparison
- Any situation needing thorough exploration before action

## Usage
```
/kiro-think [level] [topic]
```

### Thinking Levels
- **v1** (default): Standard thinking (~4K tokens) - Quick analysis for daily problems
- **v2**: Deep thinking (~10K tokens) - Detailed analysis for architecture and design
- **v3**: Ultra thinking (~32K tokens) - Exhaustive analysis for critical problems

### Examples
```
/kiro-think how to optimize API performance        # Default v1
/kiro-think v1 database query optimization        # Standard thinking
/kiro-think v2 microservices architecture design  # Deep thinking
/kiro-think v3 core algorithm rewrite            # Ultra thinking
```

## Behavioral Flow
Based on CLAUDE.md specifications:
1. **Activate thinking mode at specified level**
   - v1: Standard analysis with practical focus
   - v2: Comprehensive analysis with multiple perspectives
   - v3: Exhaustive analysis exploring all possibilities

2. **Engage in deep discussion with user**
   - Analyze the problem from multiple angles
   - Present multiple solution approaches
   - Compare pros and cons of each approach
   - Consider edge cases and potential issues
   - Discuss trade-offs and implications

3. **Present findings and recommendations**
   - Summarize key insights
   - Provide clear recommendation
   - Explain reasoning behind recommendation

4. **MUST get confirmation before any action**
   - Ask: "Based on our discussion, shall I proceed with [specific action]?"
   - Wait for explicit approval
   - ONLY execute after user confirms

5. **Execute agreed solution if approved**
   - Update relevant documents if needed
   - Implement code changes if required
   - Follow up with results

6. **Auto-save valuable analysis results**
   - **Automatic path**: `.specs/{feature}/docs/analysis-{topic}-{date}.md`
   - **If no active feature**: Save to `.specs/misc/docs/`
   - **Silent save**: Do not ask unless there's a conflict
   - **Only ask when**: File already exists or technical constraint prevents default location
   - **Explanation when asking**: Provide clear reason why default location cannot be used

## Tool Coordination
- **Read**: Analyze existing code and documentation
- **Sequential-thinking**: Enable structured reasoning (if available)
- **Edit/Write**: Implement agreed changes (only after confirmation)
- **TodoWrite**: Track implementation if complex

## Key Patterns
- **Discussion First**: Always discuss thoroughly before action
- **Multiple Options**: Present various approaches with trade-offs
- **User Control**: Nothing executes without explicit approval
- **Depth Control**: User chooses analysis depth via v1/v2/v3
- **Chinese Interaction**: All discussion in Chinese
- **Automatic Storage**: Save to `.specs/{feature}/docs/` without asking

## Output Format
```
🤔 Deep Thinking: [Topic]
Thinking Level: v[1/2/3]

📊 Problem Analysis:
- [Key point 1]
- [Key point 2]

💡 Solutions:

Solution A: [Name]
✅ Pros:
- [Advantage 1]
- [Advantage 2]
❌ Cons:
- [Disadvantage 1]
- [Disadvantage 2]

Solution B: [Name]
✅ Pros: ...
❌ Cons: ...

🎯 Recommendation:
Based on analysis, I recommend Solution [A/B] because [reason].

Shall I proceed with Solution [A/B]? Do you need my help implementing it?
```

## Boundaries

**Will:**
- Provide deep, thoughtful analysis
- Present multiple perspectives
- Compare different approaches
- Wait for confirmation before action

**Will Not:**
- Execute without explicit approval
- Skip analysis to rush to solution
- Make unilateral decisions
- Ignore user preferences