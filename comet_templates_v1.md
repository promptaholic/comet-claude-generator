# Comet Output Templates - Knowledge Base

**Version:** 1.0
**Last Updated:** November 15, 2025
**Purpose:** Standard templates for all Comet-generated Claude Project files

---

## CLAUDE.md Template

```markdown
# [Project Name]
**Version:** 1.0 | **Purpose:** [One sentence] | **User:** [Who]

## Overview
[2-3 paragraphs explaining the project's purpose, capabilities, and value proposition]

## Core Capabilities
1. [Key feature 1]
2. [Key feature 2]
3. [Key feature 3]

## Workflow
[Step-by-step process of how the project works]

## Success Metrics
- ✓ [Quantifiable metric 1]
- ✓ [Quantifiable metric 2]
- ✓ [Quantifiable metric 3]

## Usage Examples
**Example 1:** [Specific input] → [Expected output]
**Example 2:** [Specific input] → [Expected output]

## Maintenance
[Update triggers and versioning guidance]
```

---

## Custom Instructions Template

```xml
<identity>You are [role]. Specialize in [domain].</identity>

<core_rules>
1. [Non-negotiable behavior]
2. [Non-negotiable behavior]
3. [Non-negotiable behavior]
</core_rules>

<workflow>
When [trigger]:
1. [Step with specific action]
2. [Step with specific action]
3. Output: [Format specification]
</workflow>

<output_format>[Detailed specification]</output_format>

<constraints>
- ALWAYS [required behavior]
- NEVER [prohibited behavior]
- IF [condition] THEN [action]
</constraints>

<examples>
<example>
<user_input>[Real example input]</user_input>
<ideal_output>[Real example output with full formatting]</ideal_output>
</example>
</examples>

<quality_checks>
- [ ] [Pre-response check 1]
- [ ] [Pre-response check 2]
- [ ] [Pre-response check 3]
</quality_checks>
```

---

## SKILL.md Template

```markdown
---
name: concept-name-kebab-case
description: One sentence under 100 characters
version: 1.0
---

# Skill Name

## Purpose
[When to use this skill, what problem it solves]

## Triggers
- [User pattern that activates this skill]
- [Another pattern]

## Workflow
<workflow>
1. **[Step Name]:** [Action] → [Tools used] → [Output]
2. **[Step Name]:** [Action] → [Tools used] → [Output]
3. **[Step Name]:** [Action] → [Tools used] → [Output]
</workflow>

## Output Format
```
[Exact specification of output structure]
```

## Examples
**Input:** [Real example]
**Process:** [What happens step by step]
**Output:** [Real result]

## Quality Criteria
- ✓ [Success criterion 1]
- ✓ [Success criterion 2]

## Troubleshooting
**Problem:** [Common issue] | **Fix:** [Specific solution]
**Problem:** [Common issue] | **Fix:** [Specific solution]
```

---

## Knowledge Base Template

```markdown
# [Topic] Knowledge Base
**v1.0** | [Date] | [Purpose statement]

## Core Concepts

### [Concept 1]
[Explanation with example]

### [Concept 2]
[Explanation with example]

## Patterns & Best Practices

**Pattern 1:** When [context] → Use [approach]
**Example:** [Concrete example]

**Pattern 2:** When [context] → Use [approach]
**Example:** [Concrete example]

## Reference Data
[Tables, lists, specifications, or other structured reference material]

## Integration
[How this knowledge base connects to the project and when to reference it]
```

---

## Prompt Templates Template

```markdown
# Prompts for [Concept]
**v1.0** | [Date]

## Template 1: [Use Case Name]
**Purpose:** [When to use this prompt]

```
[Full prompt with {{variables}} marked]
```

**Variables:**
- `{{variable1}}`: [Description]
- `{{variable2}}`: [Description]

**Example:**
```
[Prompt with real values filled in]
```

---

## Template 2: [Use Case Name]
**Purpose:** [When to use this prompt]

```
[Full prompt with {{variables}} marked]
```

**Variables:**
- `{{variable1}}`: [Description]

**Example:**
```
[Prompt with real values filled in]
```

[Repeat for 5-8 total templates]
```

---

## Tool Configuration Template

```json
{
  "mcpServers": {
    "[server-name]": {
      "command": "[command]",
      "args": ["[arg1]", "[arg2]"],
      "env": {
        "[ENV_VAR]": "[value]"
      }
    }
  }
}
```

**Common MCP Configurations:**

### Web Search
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### File System
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed/directory"]
    }
  }
}
```

### GitHub
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your-token-here"
      }
    }
  }
}
```

---

## Complete Output Format

When generating a Claude Project, structure output as follows:

```
# CLAUDE PROJECT: [Concept Name]

## FILE 1: CLAUDE.md
[Full CLAUDE.md content following template above]

---

## FILE 2: custom_instructions.txt
[Full XML-structured custom instructions following template above]

---

## FILE 3: [name]_skill_v1.md (if applicable)
[Full SKILL.md content following template above]

---

## FILE 4: [name]_knowledge_v1.md
[Full knowledge base content following template above]

---

## FILE 5: prompt_templates_v1.md
[Full prompt templates following template above]

---

## FILE 6: tool_configuration.json (if MCP needed)
[Full tool config following template above]

---

## SETUP INSTRUCTIONS

### Quick Start (5 min)
1. Create new Claude Project: "[Project Name]"
2. Upload CLAUDE.md to project
3. Copy custom_instructions.txt → Project Settings → Custom Instructions
4. Test with: "[Example prompt]"
5. Expected result: "[What should happen]"

### Full Setup (15-30 min)
1. Create new Claude Project: "[Project Name]"
2. Upload all files (CLAUDE.md, knowledge files, etc.)
3. Configure Custom Instructions (custom_instructions.txt)
4. If MCP tools needed:
   - Open Claude Desktop settings
   - Add tool_configuration.json content to MCP section
   - Restart Claude Desktop
5. Test with prompts from prompt_templates_v1.md
6. Verify all features work as expected

---

## USAGE GUIDANCE

### Quick Commands
- [Common command 1 and expected result]
- [Common command 2 and expected result]

### Advanced Workflows
- [Complex workflow 1 with step-by-step]
- [Complex workflow 2 with step-by-step]

---

## SUCCESS METRICS
- ✓ [Metric 1 with specific target]
- ✓ [Metric 2 with specific target]
- ✓ [Metric 3 with specific target]
```

---

## Template Selection Guide

### Use MINIMAL template set when:
- Concept is simple (single purpose)
- User requested /quick-claude
- No tools needed
- No multi-step workflow

**Output:** CLAUDE.md + custom_instructions.txt only

---

### Use STANDARD template set when:
- Concept is moderate complexity
- Some domain knowledge needed
- 2-3 step workflow
- Standard use case

**Output:** CLAUDE.md + custom_instructions.txt + knowledge_v1.md + prompt_templates_v1.md

---

### Use COMPLETE template set when:
- Concept is complex
- User requested /full-claude
- Multi-step workflow requiring skill
- MCP tools needed
- Team collaboration

**Output:** All 6 files (CLAUDE.md, custom_instructions, SKILL.md, knowledge, prompts, tool_config)

---

## Quality Standards

Every generated file must include:
- ✓ Real examples (not "[Example here]" placeholders)
- ✓ Specific values (not vague descriptions)
- ✓ Version numbers (semantic versioning)
- ✓ Clear setup instructions
- ✓ Success criteria
- ✓ Troubleshooting section
- ✓ XML structure (for custom instructions)
- ✓ Valid YAML frontmatter (for SKILL.md)

---

## Integration Points

**This template knowledge base connects to:**
- Custom instructions (apply these templates when generating)
- Claude best practices (ensure XML compliance)
- Skill architecture patterns (follow design principles)
- Shortcuts reference (match output format expectations)

**When to reference:**
- Generating any Claude Project configuration
- Validating output quality
- Ensuring consistency across generations
- Standardizing team output

---

**Version:** 1.0
**Next Update:** When Anthropic changes Claude Project structure or new template patterns emerge
