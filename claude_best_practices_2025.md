# Claude Best Practices 2025 - Knowledge Base

**Version:** 1.0  
**Last Updated:** November 11, 2025  
**Purpose:** Reference guide for advanced Claude configuration following Anthropic's latest standards

---

## XML Tag Standards

### Core Tags

- `<instructions>` - Commands and directives for Claude's behavior
- `<context>` - Background information and domain knowledge
- `<examples>` - Demonstrations of correct behavior
- `<thinking>` - Chain of thought reasoning (visible to user)
- `<answer>` - Final output section
- `<output>` - Structured results container
- `<workflow>` - Step-by-step process definitions

### Usage Rules

1. **Keep tags flat** - Nested tags confuse the parser
2. **Use consistently** - Same tag for same purpose
3. **Close properly** - Always match opening/closing tags
4. **Don't overuse** - Only when structure adds clarity

**Example:**
```xml
<instructions>
Generate a report on [topic].
</instructions>

<context>
User is a [role] working in [industry].
Target audience: [audience].
</context>

<examples>
<example>
<user_input>Create sales report for Q4</user_input>
<ideal_output>
# Q4 Sales Report
## Executive Summary
[Summary content]
</ideal_output>
</example>
</examples>
```

---

## SKILL.md Frontmatter Format

**Required structure:**

```yaml
---
name: skill-name-kebab-case
description: One sentence max 100 chars
version: 1.0
author: Your Name or Organization
license: MIT (optional)
---
```

**Critical rules:**
- Name: lowercase, hyphenated (kebab-case)
- Description: Clear, actionable, under 100 characters
- Version: Semantic versioning (1.0, 1.1, 2.0)
- No extra fields without purpose

**Invalid examples:**
```yaml
# ❌ Wrong - camelCase name
---
name: mySkillName
---

# ❌ Wrong - too long description
---
name: my-skill
description: This is a really long description that goes on and on and explains too much detail that should be in the body
---

# ❌ Wrong - no version
---
name: my-skill
description: Does something
---
```

**Valid example:**
```yaml
# ✅ Correct
---
name: content-analyzer
description: Analyzes content quality and suggests improvements
version: 1.0
author: AI Systems Team
---
```

---

## Progressive Disclosure Principles

**Concept:** Show minimum information needed at each decision point, reveal more as needed.

### Three Levels

**Level 1 - Discovery:**
- Skill name
- One-sentence description
- Version number
- **Purpose:** Help user/Claude decide IF to use this skill

**Level 2 - Selection:**
- Full SKILL.md content
- Workflow overview
- Trigger patterns
- **Purpose:** Understand HOW skill works before committing

**Level 3 - Execution:**
- Helper assets
- Reference data
- Detailed examples
- Scripts (if applicable)
- **Purpose:** Execute the skill with full context

### Implementation

```markdown
# Level 1 (Frontmatter only)
---
name: report-generator
description: Creates formatted reports from data
version: 1.0
---

# Level 2 (SKILL.md body)
## Purpose
Generates structured reports...

## Workflow
1. Collect data
2. Analyze patterns
3. Format output

# Level 3 (Assets loaded as needed)
- templates/report_template.md
- data/industry_benchmarks.csv
- scripts/format_output.py
```

**Key insight:** Never dump everything at once. Let Claude request more context when needed.

---

## Custom Instructions Best Structure

**Recommended format:**

```xml
<identity>
[Who Claude is in this context]
</identity>

<core_rules>
[Non-negotiable behaviors]
</core_rules>

<workflow>
[Step-by-step processes]
</workflow>

<output_format>
[How to structure responses]
</output_format>

<constraints>
[Absolute requirements]
</constraints>

<examples>
[Demonstrations of correct behavior]
</examples>

<quality_checks>
[Pre-response validation]
</quality_checks>
```

**Why this works:**
1. Identity sets context before rules
2. Core rules establish boundaries
3. Workflow defines process
4. Output format ensures consistency
5. Constraints prevent errors
6. Examples show don't tell
7. Quality checks catch issues before response

---

## Performance Optimization

### Token Management

**30/70 Guideline:**
- Long conversations: 30% user messages, 70% assistant responses
- Prevents context bloat
- Maintains conversation flow
- Enables better summarization

**Context Gathering Strategy:**
```
1. CLAUDE.md (auto-loaded) - High-level overview
2. Custom instructions - Core behavior
3. Skills (on-demand) - Specialized workflows
4. Knowledge files (referenced) - Deep domain knowledge
5. Tools (as needed) - External integrations
```

### XML Tag Efficiency

**Do:**
```xml
<instructions>
Create report: [topic]
Include: metrics, trends, recommendations
Format: Executive summary + 3 sections
</instructions>
```

**Don't:**
```xml
<instructions>
I need you to create a comprehensive report about [topic]. 
The report should include all relevant metrics and data points.
Please make sure to analyze trends over time.
Don't forget to add recommendations at the end.
Use a professional format with an executive summary.
Also include at least 3 main sections.
</instructions>
```

**Savings:** 60% fewer tokens, same clarity

---

## Few-Shot Learning

**Research finding:** One good example reduces errors by 60% (Anthropic internal testing, 2025)

### Quality Over Quantity

**Weak approach:**
```xml
<examples>
Example 1: [vague]
Example 2: [vague]
Example 3: [vague]
Example 4: [vague]
Example 5: [vague]
</examples>
```

**Strong approach:**
```xml
<examples>
<example>
<user_input>
Analyze this sales data: Q1: $150k, Q2: $180k, Q3: $165k, Q4: $200k
</user_input>
<ideal_output>
# Sales Analysis

**Trend:** Upward trajectory (+33% YoY)
**Peak:** Q4 ($200k)
**Dip:** Q3 (-8% from Q2)

**Recommendation:** Investigate Q3 dip cause. Replicate Q4 success factors in Q1 2026.
</ideal_output>
</example>
</examples>
```

**One detailed example > Five vague ones**

### Example Fidelity

**Claude 4.x models pay EXTREME attention to example details:**
- Formatting matters (spacing, headers, bullets)
- Tone is replicated (formal vs casual)
- Structure is mirrored (sections, order)
- Edge cases shown become edge cases handled

**Rule:** Examples must match EXACTLY what you want replicated

---

## File Organization Standards

**Recommended structure:**

```
project_root/
├── CLAUDE.md (auto-loaded project context)
├── .claude/
│   ├── skills/
│   │   ├── skill_1_v1.md
│   │   ├── skill_2_v1.md
│   │   └── README.md (skill index)
│   └── commands/
│       ├── template_1.md (slash commands)
│       └── template_2.md
├── knowledge/
│   ├── domain_knowledge_v1.md
│   ├── reference_data_v1.csv
│   └── examples_library_v1.md
└── config/
    ├── .mcp.json (tool integrations)
    └── project_settings.json
```

**Why this structure:**
- CLAUDE.md is auto-discovered
- .claude/ is recognized standard location
- knowledge/ clearly separates reference data
- config/ isolates technical settings

---

## Error Prevention Techniques

### Date Validation

**Pattern:** Force Claude to validate before proceeding

```xml
<instructions>
Validate all dates: {#eval:/^\d{4}-\d{2}-\d{2}$/}
Then process the request.
</instructions>
```

**How it works:**
- Claude runs regex validation
- Retries up to 3x until passes
- Prevents malformed date outputs

### JSON Schema Enforcement

**Enable strict JSON mode** (beta, Aug 2025):

```python
# API parameter
should_write_json=true
```

**Provide schema:**
```xml
<instructions>
Output MUST conform to this schema:
{
  "type": "object",
  "properties": {
    "name": {"type": "string"},
    "value": {"type": "number"},
    "tags": {"type": "array", "items": {"type": "string"}}
  },
  "required": ["name", "value"]
}
</instructions>
```

**Result:** Claude validates against schema before responding

### Uncertainty Handling

**Add one line:** "If you are unsure, write 'I don't know'."

**Impact:** Accuracy improves immediately (vs hallucination)

---

## Code-Specific Features

### Language Tags

**Wrap code in fenced blocks with language-specific tags:**

```python
# refactor-js
# python-opt
# c-lint
# sql-fix
```

**Effect:** Triggers Claude Code's dedicated compiler/linters without extra API calls

**Example:**
````markdown
```python-opt
def slow_function(data):
    result = []
    for item in data:
        result.append(process(item))
    return result
```
````

**Claude will:** Auto-optimize to list comprehension or vectorized operation

### Chain of Thought Control

**Enable:** Include `<thinking>` tags in prompt  
**Disable:** Set `enable_cot=false` in API params (Pro tier)

**When to disable:**
- Legal memos (reasoning must stay hidden)
- Executive briefs (conciseness critical)
- API responses (no user-facing reasoning)

**When to enable:**
- Debugging (show logic)
- Complex analysis (validate reasoning)
- Educational content (teach process)

---

## Token Optimization

### Max Token Hints

**Set header:** `X-Max-Tokens-Hint: 6000`

**Effect:** Claude budgets response length upfront

**Best practice:** Set to 80% of actual limit (leaves buffer)

### Large Document Placement

**Do:** Place large documents BEFORE instructions

```
<document>
[10,000 word report]
</document>

<instructions>
Summarize the key findings above.
</instructions>
```

**Don't:** Place after instructions (wastes tokens on repeated context)

### Template Variables

**Use curly braces for dynamic parts:**

```
Translate {{source_text}} into {{target_language}} at a sixth-grade reading level.
```

**Benefit:** Same template works at scale, clear what varies

---

## Version Control

### Semantic Versioning

- **1.0** - Initial release
- **1.1** - Minor improvements, backward compatible
- **2.0** - Breaking changes, not backward compatible

### What Triggers Version Bump

**Minor (1.0 → 1.1):**
- Added optional fields
- Improved examples
- Bug fixes
- Performance optimizations

**Major (1.0 → 2.0):**
- Changed required fields
- Altered output format
- Removed features
- New core dependencies

### Changelog Template

```markdown
## Version History

### v2.0 (2025-11-15)
**Breaking Changes:**
- Changed output format from JSON to XML
- Removed deprecated `legacy_mode` parameter

**Improvements:**
- 40% faster processing
- Better error messages

### v1.1 (2025-10-01)
- Added optional `include_metadata` field
- Fixed edge case with empty inputs
```

---

## Integration Points

**This knowledge base connects to:**
- Custom instructions (use XML patterns here)
- SKILL.md files (follow frontmatter format)
- Project architecture (apply file organization)
- Prompt templates (implement few-shot learning)

**When to reference:**
- Creating new Claude Projects
- Debugging existing configurations
- Optimizing performance
- Standardizing team practices

---

**Version:** 1.0  
**Next Update:** When Anthropic releases new API features or Agent Skills updates
