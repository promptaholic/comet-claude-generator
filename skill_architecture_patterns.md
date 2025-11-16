# Skill Architecture Patterns - Knowledge Base

**Version:** 1.0  
**Last Updated:** November 11, 2025  
**Purpose:** Design patterns for Claude Agent Skills and custom workflows

---

## Understanding Skills as Meta-Tools

### What Skills ARE

**Skills are NOT:**
- Direct action executors
- Function calls
- Code that runs

**Skills ARE:**
- Prompt injectors
- Context modifiers
- Behavior templates
- Execution environment modifiers

### How Skills Work

```
User Request
    ↓
Skill Meta-Tool Activated
    ↓
SKILL.md Content Injected into Conversation
    ↓
Claude's Execution Environment Modified
    ↓
Claude Processes Request with New Context
    ↓
Output Produced
```

**Key Insight:** Skills work through prompt expansion, not code execution

---

## The Two-Message Pattern

### How Claude Processes Skills

**Message 1: Tool Request**
```json
{
  "role": "user",
  "content": "Use the content-analyzer skill on this blog post"
}
```

**Message 2: Context Injection**
```
[System loads content-analyzer SKILL.md]
[Injects specialized instructions into conversation history]
[Claude now has domain-specific context]
```

**Result:** Claude responds AS IF it always knew the specialized instructions

---

## Four Skill Categories

### 1. Transform Skills

**Pattern:** Input → Processing → Output

**Characteristics:**
- Clear input format
- Defined transformation rules
- Predictable output structure

**Examples:**
- Content repurposing (blog → tweet thread)
- Format conversion (Markdown → HTML)
- Data transformation (CSV → JSON)

**Template:**
```markdown
---
name: transform-[type]
description: Transforms [input] into [output]
version: 1.0
---

# Transform Skill

## Input Format
```
[Specification]
```

## Transformation Rules
1. [Rule 1]
2. [Rule 2]

## Output Format
```
[Specification]
```

## Example
**Input:** [Example]
**Output:** [Result]
```

### 2. Analysis Skills

**Pattern:** Input → Evaluation → Insights

**Characteristics:**
- Assess quality/patterns
- Generate insights
- Provide recommendations

**Examples:**
- Code review (code → feedback)
- Content audit (article → quality score)
- Data analysis (dataset → trends)

**Template:**
```markdown
---
name: analyze-[domain]
description: Analyzes [thing] and provides [insights]
version: 1.0
---

# Analysis Skill

## Analysis Criteria
- [Criterion 1]
- [Criterion 2]

## Evaluation Process
<workflow>
1. **Assess:** [What to check]
2. **Score:** [How to rate]
3. **Recommend:** [What to suggest]
</workflow>

## Output Structure
- Score: [0-10]
- Strengths: [List]
- Weaknesses: [List]
- Recommendations: [List]
```

### 3. Generation Skills

**Pattern:** Parameters → Creation → Artifact

**Characteristics:**
- Create net-new content
- Follow templates/patterns
- Optimize for specific format

**Examples:**
- Report generation (data → formatted report)
- Code scaffolding (spec → boilerplate)
- Content creation (brief → article)

**Template:**
```markdown
---
name: generate-[artifact]
description: Generates [thing] from [parameters]
version: 1.0
---

# Generation Skill

## Required Parameters
- [Param 1]: [Type] - [Description]
- [Param 2]: [Type] - [Description]

## Generation Process
<workflow>
1. **Gather:** [What inputs]
2. **Structure:** [How to organize]
3. **Populate:** [How to fill]
4. **Polish:** [How to refine]
</workflow>

## Output Template
```
[Template structure]
```
```

### 4. Workflow Skills

**Pattern:** Multi-step → Orchestration → Result

**Characteristics:**
- Coordinate multiple sub-tasks
- Maintain state across steps
- Handle complex dependencies

**Examples:**
- Research pipeline (query → search → analyze → summarize → report)
- Deployment automation (test → build → deploy → verify)
- Content production (research → outline → draft → edit → publish)

**Template:**
```markdown
---
name: workflow-[process]
description: Orchestrates [multi-step process]
version: 1.0
---

# Workflow Skill

## Workflow Stages

### Stage 1: [Name]
**Inputs:** [What's needed]
**Actions:** [What happens]
**Outputs:** [What's produced]
**Tools:** [Which tools if any]

### Stage 2: [Name]
**Inputs:** [From Stage 1]
**Actions:** [What happens]
**Outputs:** [What's produced]
**Tools:** [Which tools if any]

### Stage 3: [Name]
**Inputs:** [From Stage 2]
**Actions:** [What happens]
**Outputs:** [Final result]
**Tools:** [Which tools if any]

## State Management
[How to track progress between stages]

## Error Recovery
**Stage fails:** [What to do]
**Partial success:** [How to handle]
```

---

## Design Principles

### 1. Single Responsibility

**Bad:**
```markdown
---
name: content-master
description: Does everything related to content
---
```

**Why bad:** Unclear when to use, hard to maintain, too broad

**Good:**
```markdown
---
name: content-repurposer
description: Converts long-form content into social media posts
---
```

**Why good:** Clear purpose, obvious trigger, maintainable

### 2. Clear Triggers

**Trigger patterns should be:**
- Specific (not vague)
- Unambiguous (not overlapping)
- Discoverable (easy to remember)

**Examples:**

**Good triggers:**
- "When user asks to convert blog post to tweets"
- "When user provides code for review"
- "When user requests competitive analysis"

**Bad triggers:**
- "When user needs help with content"
- "When user wants to improve something"
- "When analysis is required"

### 3. Fail Gracefully

**Every skill should handle:**

```markdown
## Error Handling

**Missing inputs:**
Response: "I need [X] to proceed. Please provide [specific format]."

**Invalid format:**
Response: "Expected [format], got [what was provided]. Here's an example: [show example]"

**Out of scope:**
Response: "This request is outside the skill's capability. Try [alternative skill] instead."

**Tool unavailable:**
Response: "This requires [tool] which isn't available. Manual alternative: [steps]"
```

### 4. Version Properly

**When to version bump:**

**Patch (1.0.1):**
- Fixed typo
- Improved example
- Clarified wording

**Minor (1.1.0):**
- Added optional parameter
- Enhanced output detail
- New optional feature

**Major (2.0.0):**
- Changed required parameters
- Altered output format
- Removed features
- New dependencies

### 5. Test Thoroughly

**Every skill should include:**

```markdown
## Test Cases

### Test 1: Happy Path
**Input:** [Normal valid input]
**Expected Output:** [What should happen]

### Test 2: Edge Case
**Input:** [Boundary condition]
**Expected Output:** [How to handle]

### Test 3: Invalid Input
**Input:** [Bad data]
**Expected Output:** [Error handling]

### Test 4: Minimal Input
**Input:** [Bare minimum required]
**Expected Output:** [Still works]
```

---

## Progressive Disclosure in Skills

### Level 1: Frontmatter Only

**What user/Claude sees:**
```yaml
---
name: report-generator
description: Creates formatted reports from data
version: 1.0
---
```

**Decision point:** "Should I use this skill?"

### Level 2: Full SKILL.md

**What loads when skill selected:**
```markdown
## Purpose
Generates structured reports from datasets...

## Workflow
1. Validate data format
2. Calculate key metrics
3. Generate visualizations
4. Format as report

## Required Inputs
- Dataset (CSV or JSON)
- Report type (summary | detailed | executive)
```

**Decision point:** "How do I use this skill?"

### Level 3: Assets & References

**What loads during execution:**
- templates/report_template.md
- data/industry_benchmarks.csv
- examples/sample_reports/

**Decision point:** "What are the implementation details?"

---

## Composition vs Monoliths

### Composable Skills (Preferred)

```
report-generator (orchestrator)
├── uses: data-validator
├── uses: metric-calculator
├── uses: chart-generator
└── uses: document-formatter
```

**Benefits:**
- Reusable components
- Easier testing
- Clear responsibilities
- Maintainable

### Monolithic Skills (Avoid)

```
mega-reporting-tool
└── does: validation + calculation + visualization + formatting all in one
```

**Problems:**
- Hard to maintain
- Difficult to test
- Not reusable
- Unclear boundaries

**Exception:** Very simple, truly atomic tasks

---

## Naming Conventions

### Skill Names

**Format:** `[verb]-[noun]` (kebab-case)

**Good:**
- `analyze-code`
- `generate-report`
- `transform-content`
- `workflow-deploy`

**Bad:**
- `CodeAnalyzer` (camelCase)
- `analyze_code` (snake_case)
- `analysis` (too vague)
- `the-best-code-analyzer-v2` (too long)

### File Names

**Format:** `[skill-name]_v[version].md`

**Examples:**
- `analyze-code_v1.md`
- `generate-report_v2.md`
- `transform-content_v1.md`

---

## State Management

### Stateless Skills (Simple)

**No memory between invocations:**
```markdown
## Workflow
1. Receive input
2. Process
3. Return output
4. Done (no state retained)
```

**Good for:**
- Transformations
- Analysis
- One-shot generation

### Stateful Skills (Complex)

**Maintains context across steps:**
```markdown
## Workflow
1. Initialize state
2. Step 1 → Update state
3. Step 2 → Update state
4. Step 3 → Update state
5. Final output + state summary

## State Tracking
```
{
  "current_step": 2,
  "completed": ["step1"],
  "pending": ["step3", "step4"],
  "data": {...}
}
```
```

**Good for:**
- Multi-stage workflows
- Iterative processes
- Long-running tasks

**Warning:** State management adds complexity. Use only when necessary.

---

## Tool Integration Patterns

### Skills That Use Tools

```markdown
## Required Tools
- `web_search` - For gathering external data
- `bash_tool` - For file operations
- `custom_mcp` - For domain-specific integration

## Tool Usage Pattern
<workflow>
1. **Gather:** Use `web_search` to find [X]
2. **Process:** Use `bash_tool` to manipulate [Y]
3. **Integrate:** Use `custom_mcp` to send [Z]
</workflow>

## Fallback (Tools Unavailable)
If tools aren't available:
1. Request manual input for [X]
2. Generate [Y] without file ops
3. Output [Z] for manual integration
```

---

## Performance Considerations

### Token Budget

**Skill size guidelines:**
- **Small:** < 1,000 tokens (simple transforms)
- **Medium:** 1,000-3,000 tokens (standard workflows)
- **Large:** 3,000-5,000 tokens (complex orchestration)
- **Too large:** > 5,000 tokens (consider splitting)

**Why it matters:** Every skill loads into context, consuming token budget

### Loading Strategy

**Lazy loading:**
```markdown
## References
[Only load these if needed during execution]
- templates/ (500 tokens each)
- examples/ (1000 tokens each)
- data/ (variable)

Don't preload. Request explicitly.
```

**Eager loading:**
```markdown
## Core Context
[Always load with skill]
- Workflow steps
- Required parameters
- Output format

Total: 800 tokens (acceptable overhead)
```

---

## Quality Checklist

Before deploying a skill:

- [ ] **Frontmatter valid** (YAML syntax, required fields)
- [ ] **Single responsibility** (does one thing well)
- [ ] **Clear triggers** (obvious when to use)
- [ ] **Graceful errors** (handles failures)
- [ ] **Real examples** (not placeholders)
- [ ] **Versioned properly** (semantic versioning)
- [ ] **Tested thoroughly** (happy path + edge cases)
- [ ] **Token efficient** (< 5,000 tokens if possible)
- [ ] **Tool dependencies documented** (if any)
- [ ] **Fallbacks provided** (for missing tools)

---

## Common Anti-Patterns

### 1. Vague Descriptions

**Bad:**
```yaml
description: Helps with content stuff
```

**Good:**
```yaml
description: Converts blog posts into Twitter threads with hooks
```

### 2. Missing Error Handling

**Bad:**
```markdown
## Workflow
1. Process input
2. Generate output
```

**Good:**
```markdown
## Workflow
1. Validate input (if invalid: return error + example)
2. Process (if fails: attempt recovery or abort gracefully)
3. Generate output (if incomplete: note limitations)
```

### 3. No Examples

**Bad:**
```markdown
## Usage
Provide data and get report.
```

**Good:**
```markdown
## Usage Example
**Input:**
```json
{"sales": [100, 200, 150]}
```

**Output:**
```
# Sales Report
Total: $450
Trend: Upward (+50% peak)
```
```

### 4. Unclear Scope

**Bad:**
```markdown
## Purpose
Analyzes things and provides insights.
```

**Good:**
```markdown
## Purpose
Analyzes Python code for:
- PEP 8 compliance
- Security vulnerabilities
- Performance bottlenecks

Does NOT analyze: JavaScript, logic errors, architecture
```

---

## Integration Points

**This knowledge base connects to:**
- SKILL.md creation (use templates and patterns here)
- Custom instructions (implement workflow patterns)
- Claude Projects architecture (apply composition principles)
- Tool configurations (follow integration patterns)

**When to reference:**
- Designing new skills
- Refactoring existing workflows
- Troubleshooting skill behavior
- Optimizing performance

---

**Version:** 1.0  
**Next Update:** When new skill patterns emerge from usage
