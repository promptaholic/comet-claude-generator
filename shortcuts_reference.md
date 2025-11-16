# Perplexity Shortcuts Reference - Knowledge Base

**Version:** 1.0  
**Last Updated:** November 11, 2025  
**Purpose:** Guide for understanding and recommending available Perplexity shortcuts

---

## Available Shortcuts

### /quick-claude

**Purpose:** Generate minimal Claude Project configuration in under 2 minutes

**Output:**
- CLAUDE.md (lightweight, ~300 words)
- Custom instructions (basic, ~200 words)
- Setup instructions (< 5 min)

**Total setup time:** 2-5 minutes

**Best for:**
- Quick prototyping
- Testing ideas
- Simple single-purpose projects
- Learning/exploration

**Not suitable for:**
- Production systems requiring multiple skills
- Complex multi-tool integrations
- Projects with extensive knowledge bases
- Team collaboration setups

**Example usage:**
```
/quick-claude automated email responder for customer support
```

**Expected output format:**
```markdown
# [Project Name]

**Version:** 1.0
**Purpose:** [One sentence]

[Brief overview]

## Usage
[2-3 examples]

## Setup
1. Create Project
2. Upload CLAUDE.md
3. Paste custom instructions
4. Test with: [prompt]
```

---

### /full-claude

**Purpose:** Generate complete production-ready Claude Project configuration

**Output:**
- CLAUDE.md (comprehensive, ~800 words)
- Custom instructions (XML-structured, ~600 words)
- SKILL.md file (if workflow is multi-step)
- Knowledge base file (domain-specific)
- Prompt templates (5-8 reusable prompts)
- Tool configuration (MCP if needed)

**Total setup time:** 15-30 minutes

**Best for:**
- Production systems
- Complex workflows
- Team collaboration
- Long-term projects
- Projects requiring tool integrations

**Not suitable for:**
- Quick tests (use /quick-claude instead)
- Extremely simple tasks
- When unsure if concept is viable

**Example usage:**
```
/full-claude multi-platform social media scheduler with AI-generated captions
```

**Expected output format:**
```markdown
# CLAUDE PROJECT: [Concept]

## FILE 1: CLAUDE.md
[Comprehensive overview with examples]

## FILE 2: custom_instructions.txt
[Full XML-structured instructions]

## FILE 3: [concept]_skill_v1.md
[Custom skill if needed]

## FILE 4: [concept]_knowledge_v1.md
[Domain knowledge]

## FILE 5: prompt_templates_v1.md
[Reusable prompts]

## FILE 6: tool_configuration.json
[MCP setup if applicable]

## SETUP INSTRUCTIONS
[Step-by-step deployment guide]
```

---

## When to Recommend Shortcuts

### Recommend /quick-claude when:

1. **User explicitly mentions:**
   - "quick"
   - "simple"
   - "test"
   - "prototype"
   - "just want to try"

2. **Concept characteristics:**
   - Single-purpose
   - No tool integrations needed
   - No multi-step workflows
   - Minimal domain knowledge required

3. **User context:**
   - New to Claude Projects
   - Exploring possibilities
   - Time-constrained
   - Learning mode

**Example triggers:**
- "Can I quickly test an idea for..."
- "I want a simple..."
- "Is there a fast way to..."

**Recommendation phrasing:**
```
For quick testing, try: /quick-claude [concept]

Or I can generate the minimal config here if you prefer.
```

---

### Recommend /full-claude when:

1. **User explicitly mentions:**
   - "production"
   - "complete"
   - "full"
   - "comprehensive"
   - "team"
   - "deploy"

2. **Concept characteristics:**
   - Multi-step workflows
   - Requires tool integrations (MCP)
   - Needs extensive knowledge base
   - Complex domain logic
   - Team collaboration

3. **User context:**
   - Building for real use (not testing)
   - Has specific requirements
   - Needs documentation
   - Planning long-term usage

**Example triggers:**
- "I need a production system for..."
- "Build me a complete..."
- "My team needs..."
- "Deploy a..."

**Recommendation phrasing:**
```
For a production system, try: /full-claude [concept]

Or I can generate the complete stack here (6-8 files).
```

---

### Don't Recommend Shortcuts When:

1. **User is already using the Space**
   - They chose to use this Space, not shortcuts
   - Respect their workflow choice
   - Mention shortcuts as aside, don't push

2. **Concept is ambiguous**
   - Need clarification first
   - Shortcuts work best with clear concepts
   - Get clarity, then suggest

3. **User is learning the meta-system**
   - Seeing full generation helps understanding
   - Shortcuts abstract away the process
   - Educational value in seeing full output

4. **Concept is borderline complexity**
   - Between simple and complex
   - Better to generate here and show options
   - Let user decide after seeing output

---

## Shortcut Limitations

### /quick-claude limitations:

- **No custom skills** - Can't handle multi-step workflows
- **No MCP tools** - Can't integrate external tools
- **Minimal knowledge base** - Not suitable for complex domains
- **Basic examples** - Fewer demonstrations
- **Less documentation** - Shorter setup guides

**Workaround:** Start with /quick-claude, upgrade to full config later if needed

### /full-claude limitations:

- **Takes longer** - 15-30 min vs 2-5 min
- **More complex** - 6-8 files to manage
- **Can be overkill** - Too much for simple tasks
- **Steeper learning curve** - More to understand

**Workaround:** Use /quick-claude first to validate concept, then /full-claude for production

---

## Shortcuts vs Space Generation

### Use Shortcuts When:

- User has shortcuts configured
- Concept is very clear
- Prefer condensed output
- Want separate generation from conversation

### Use Space Generation When:

- User doesn't mention shortcuts
- Need to clarify concept first
- Want to see thinking process
- Prefer integrated conversation flow

### Hybrid Approach:

```
User: "I want to build [concept]"

Space: 
"Here are your options:

1. **Quick test**: /quick-claude [concept] (2 min)
2. **Full system**: /full-claude [concept] (30 min)
3. **Generate here**: I'll create it in this conversation

Which would you prefer?"
```

**Best of both:** Give user control, show options

---

## Upgrade Paths

### Quick → Full

**Scenario:** User starts with /quick-claude, realizes they need more

**Process:**
1. Keep CLAUDE.md from quick version
2. Expand custom instructions (add XML structure)
3. Create SKILL.md for multi-step workflow
4. Add knowledge base file
5. Generate prompt templates
6. Configure tools if needed

**Time to upgrade:** 10-15 additional minutes

### Space → Shortcut

**Scenario:** User generates in Space, wants to formalize as shortcut

**Process:**
1. Extract the generated prompt pattern
2. Identify variable components
3. Create shortcut template with $VARIABLES
4. Test shortcut with example concepts
5. Refine based on results

**Time to create shortcut:** 5-10 minutes

---

## Shortcut Templates (For Reference)

### /quick-claude Template Structure

```
Generate minimal Claude Project config for: [CONCEPT]

Constraints:
- CLAUDE.md only (no custom skill)
- Under 500 words total
- 2 examples minimum
- Setup time < 5 min
- Copy-paste installable

Output:
- FILE 1: CLAUDE.md
- FILE 2: custom_instructions.txt
- SETUP: 3-step instructions
```

### /full-claude Template Structure

```
Generate complete Claude Project for: [CONCEPT]

Include:
- CLAUDE.md (comprehensive, ~800 words)
- Custom instructions (XML-structured)
- Custom skill (if multi-step workflow)
- Knowledge base file (domain-specific)
- Prompt templates (5-8 reusable)
- Tool configs (MCP if needed)

Output: Full file set (6-8 files) + setup guide
```

---

## Success Metrics for Shortcuts

### /quick-claude Success:

- ✓ Setup completed in < 5 minutes
- ✓ User can test immediately
- ✓ Core functionality works
- ✓ No complex dependencies
- ✓ Clear enough to understand

### /quick-claude Failure:

- ✗ Setup takes > 10 minutes
- ✗ Missing critical instructions
- ✗ Concept too complex for minimal format
- ✗ User confused about next steps

**Fix:** Recommend /full-claude or full Space generation

### /full-claude Success:

- ✓ Production-ready system
- ✓ All components integrated
- ✓ Team can collaborate
- ✓ Scales beyond initial concept
- ✓ Well-documented

### /full-claude Failure:

- ✗ Too complex for actual need
- ✗ User overwhelmed by file count
- ✗ Overkill for simple concept
- ✗ Setup abandoned halfway

**Fix:** Recommend /quick-claude or simplify concept

---

## Troubleshooting Shortcut Issues

### Problem: Shortcut not available

**Likely causes:**
- User hasn't configured shortcuts
- Browser extension not installed
- Typing error in shortcut name

**Response:**
```
It looks like shortcuts aren't configured yet. 

I can generate the config here in this conversation instead.

Or if you'd like to set up shortcuts, they can be configured in [extension settings].
```

### Problem: Shortcut output too generic

**Likely causes:**
- Concept too vague
- Missing domain context
- Shortcut needs refinement

**Response:**
```
The shortcut works best with specific concepts.

Let me generate a detailed version here with more context about [concept].
```

### Problem: User unsure which shortcut to use

**Response:**
```
Quick decision guide:

**Use /quick-claude if:**
- Testing an idea (< 5 min setup)
- Single simple task
- Just exploring

**Use /full-claude if:**
- Building for production
- Multi-step workflow
- Need tools/integrations
- Team collaboration

Still unsure? I can generate here and we'll see together.
```

---

## Integration with This Space

### Space's Role:

1. **Detect shortcut potential**
   - Analyze concept complexity
   - Identify quick vs full candidates
   - Suggest appropriate shortcut

2. **Provide context shortcuts can't**
   - Clarify ambiguous concepts
   - Explain trade-offs
   - Show alternatives

3. **Fill gaps shortcuts miss**
   - Complex multi-concept fusion
   - Iterative refinement
   - Custom requirements

4. **Educate about shortcuts**
   - When to use each
   - How they work
   - Setup instructions

### Space is NOT:

- Shortcut replacement (they complement)
- Shortcut dependency (works standalone)
- Shortcut enforcer (user choice)

**Relationship:** Collaborative tools, not competing

---

## Best Practices for Recommending

### DO:

- **Mention casually** - "You could also try /quick-claude..." (not "You should...")
- **Explain briefly** - One sentence on what it does
- **Give choice** - "Or I can generate here"
- **Match context** - Recommend based on user's language

### DON'T:

- **Force shortcuts** - User chose Space for a reason
- **Over-explain** - Long tutorials kill flow
- **Assume availability** - Not everyone has shortcuts configured
- **Be dogmatic** - "You must use..." (never)

### Example Good Recommendation:

```
I can generate that for you here, or if you have shortcuts configured, /full-claude would give you the complete production stack.

Your preference?
```

### Example Bad Recommendation:

```
You should really use /full-claude for this instead of asking me. It's much better and faster. Let me explain how shortcuts work and why you need to set them up...
```

---

## Future Enhancements

### Potential New Shortcuts:

- **/update-claude [project] [changes]** - Update existing config
- **/merge-claude [concept1] [concept2]** - Combine concepts
- **/debug-claude [project]** - Troubleshoot configuration

### Shortcut Ecosystem:

As shortcuts evolve, this Space should:
1. Stay updated on available shortcuts
2. Recommend newest shortcuts appropriately
3. Deprecate old shortcut recommendations
4. Provide migration guides

---

## Integration Points

**This knowledge base connects to:**
- Custom instructions (trigger shortcut recommendations)
- Concept analysis (determine quick vs full)
- Output generation (match shortcut formats)
- User guidance (educate about shortcuts)

**When to reference:**
- User mentions shortcuts
- Concept complexity analyzed
- Deciding output format
- Providing setup guidance

---

**Version:** 1.0  
**Next Update:** When new shortcuts are added or behavior changes
