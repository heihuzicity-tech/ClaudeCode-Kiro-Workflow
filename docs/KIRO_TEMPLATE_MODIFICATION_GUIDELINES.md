# Kiro Template Modification Guidelines

## 🎯 Core Principles for Template Changes

### **Modification Authority**
- **NEVER modify templates without explicit user approval**
- **ALWAYS present proposed changes for discussion first**
- **WAIT for clear user confirmation before applying any modifications**
- **Immediately revert changes if user objects**

### **Template Consistency Standards**
- **MUST maintain exact syntax patterns from original kiro_specs_templates.md**
- **MUST use identical heading format**: `### SPEC_XXX` or `### KIRO_COMMAND_XXX`
- **MUST wrap template content in**: ```` ```...``` ````
- **MUST use constraint structure**: `**Constraints:**`
- **MUST follow RFC-style requirements**: `- The model MUST/SHOULD/MAY...`
- **MUST preserve exact indentation and markdown formatting**

## 📋 Error Handling Design Principles

### **Simple Error Strategy**
**Formula**: Error occurs → Provide suggestions → Ask user → Wait for explicit instruction → Execute

### **User Decision Authority**
- **AI MUST NOT make assumptions about error handling preferences**
- **AI MUST provide clear error description and suggested options**
- **AI MUST wait for explicit user instruction on how to proceed**
- **AI MUST NOT automatically retry or skip errors**

### **Database Backup Critical Rules**
- **If database configuration detected**: Execute backup immediately (NO asking)
- **If no database configuration detected**: MUST ask user for confirmation
- **NEVER skip database backup without user explicit confirmation**
- **If backup fails**: Stop, describe error, provide suggestions, ask user

## 🔧 Template Structure Standards

### **Command Template Format**
```markdown
# [Command Name] Command Template

### KIRO_COMMAND_[NAME]
```
[Brief description of command functionality]

**Constraints:**
- The model MUST [specific requirement]
- The model SHOULD [recommended behavior] 
- The model MAY [optional behavior]

## Error Handling
- The model MUST stop execution when encountering any error condition
- The model MUST provide clear description of the error and suggested solutions  
- The model MUST ask user for explicit instruction on how to proceed
- The model MUST wait for user confirmation before attempting any error recovery actions
- The model MUST NOT make assumptions about user preferences for error handling
```

### **Workflow Template Format**
```markdown
# [Workflow Name] Templates

## [Section Name]

### SPEC_WORKFLOW_[NAME]
```
[Template content with original syntax preserved]
**Constraints:**
- The model MUST [requirements following original pattern]
```

## 🎯 Specific Command Requirements

### **kiro-start Database Backup Rules**
- **MUST execute database backup immediately if database configuration is detected**
- **MUST ask user for confirmation if no database configuration is detected**
- **MUST include general error handling section for all other errors**

### **kiro-sync Context Rules**
- **MUST analyze current conversation context to extract change requirements**
- **MUST provide before/after comparison before applying changes**
- **MUST preserve completed task status when updating tasks.md**
- **MUST perform atomic updates (all succeed or all fail)**

### **kiro-load Recovery Rules**
- **MUST first read ./CLAUDE.md file to restore global rules**
- **MUST read .specs/session.md file content to restore session state**
- **MUST execute Read tool on CLAUDE.md before any other file operations**

## 📁 File Organization Standards

### **Directory Structure**
```
templates/
├── workflows/      # SPEC_WORKFLOW_* templates
├── commands/       # KIRO_COMMAND_* templates  
├── rules/          # Behavioral rules and constraints
└── CLAUDE.md       # Central configuration (project root)
```

### **Path Configuration**
- **Use `.specs/` format in all templates** (not `.kiro/specs/`)
- **Maintain relative path structure for portability**
- **Ensure consistent file naming across workflows**

## 🔄 Workflow Integration Rules

### **Think → Change Pattern**
- **`/kiro-think`**: Analyze problems, discuss solutions (no document changes)
- **`/kiro-sync`**: Apply discussed changes to SPECS documents
- **These commands work as a pair**: think first, then change

### **Save → Load Pattern**
- **`/kiro-save`**: Create comprehensive session.md with recovery context
- **`/kiro-load`**: Restore complete working context from session.md
- **Load must read both CLAUDE.md and session.md files**

## ✅ Modification Approval Process

### **Before Making Changes**
1. **Analyze**: Understand the modification request
2. **Design**: Create proposed solution following all standards
3. **Present**: Show the user what will be changed and why
4. **Wait**: Get explicit user approval
5. **Execute**: Apply changes only after confirmation

### **During Changes**
- **One change at a time**: Don't batch multiple modifications
- **Show progress**: Confirm each step as it's completed
- **Stop on objection**: Immediately revert if user objects

### **After Changes**
- **Verify**: Confirm changes match user expectations
- **Document**: Update related files if needed
- **Validate**: Check syntax and consistency

## 🚨 Critical Violations to Avoid

### **NEVER Do These**
- ❌ Modify templates without user approval
- ❌ Make assumptions about error handling preferences
- ❌ Skip database backup validation
- ❌ Change syntax patterns from original templates
- ❌ Create new constraint formats or structures
- ❌ Batch multiple changes without individual approval

### **ALWAYS Do These**
- ✅ Ask before modifying
- ✅ Present changes for review
- ✅ Wait for explicit approval
- ✅ Follow exact syntax patterns
- ✅ Include comprehensive error handling
- ✅ Maintain template consistency

## 📖 Reference Standards

### **Original Syntax Source**
- **Base all syntax on**: `kiro_specs_templates.md`
- **Maintain heading patterns**: Exactly as shown in original
- **Preserve constraint structure**: Follow RFC-style format
- **Keep indentation**: Exact spacing and formatting

### **Functional References**
- **README.md**: For command functionality descriptions
- **流程梳理.md**: For command execution flows and data flow
- **User requirements**: Primary source for new features

This document serves as the complete reference for all future Kiro template modifications. Follow these guidelines strictly to maintain system consistency and user trust.