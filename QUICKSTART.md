# Quick Start Guide

Get Comet up and running in **5 minutes** and start generating production-ready Claude Projects immediately.

---

## Prerequisites

- Access to [Claude Desktop](https://claude.ai/download) or [claude.ai](https://claude.ai)
- A concept you want to turn into a Claude Project
- 5 minutes of your time

---

## Step-by-Step Setup

### Step 1: Create a Claude Project (1 minute)

1. Open Claude Desktop or go to claude.ai
2. Click **Projects** in the sidebar
3. Click **+ New Project**
4. Name it: **"Comet - Concept to Claude Generator"**
5. Click **Create**

### Step 2: Download Comet Files (1 minute)

Go to the [Comet repository](https://github.com/promptaholic/comet-claude-generator) and download these 5 knowledge base files:

1. **CLAUDE.md**
2. **comet_templates_v1.md**
3. **claude_best_practices_2025.md**
4. **skill_architecture_patterns.md**
5. **shortcuts_reference.md**

**Quick download:**
- Click the green **Code** button
- Select **Download ZIP**
- Extract the files
- Locate the 5 files above

### Step 3: Upload Knowledge Bases (1 minute)

In your Comet Claude Project:

1. Click **Add content** (or the **+** icon)
2. Select **Upload files**
3. Upload all 5 knowledge base files (.md files)
4. Wait for "Processing complete" messages

### Step 4: Configure Custom Instructions (1 minute)

1. Click the **⚙️ Settings** icon (gear icon in top right)
2. Find the **Custom Instructions** field
3. Open `comet_system_prompt.txt` from the downloaded files
4. **Copy the entire contents** (1,442 characters)
5. **Paste** into the Custom Instructions field
6. Click **Save**

### Step 5: Test It! (1 minute)

Now test Comet with a simple prompt:

**Prompt:**
```
Generate a Claude Project for: automated weekly newsletter writer
```

**What to Expect:**

Comet will generate:
- ✅ Complete CLAUDE.md file
- ✅ XML-structured custom instructions
- ✅ Knowledge base file (content guidelines)
- ✅ Prompt templates (multiple newsletter formats)
- ✅ Setup guide
- ✅ Real examples (no placeholders!)

**Time to generate:** 1-2 minutes

---

## What to Do with Generated Output

Once Comet generates your project files:

### 1. Copy the Files

Select each file content and copy to your clipboard:
- CLAUDE.md → Save as `CLAUDE.md`
- custom_instructions.txt → Save as text file
- knowledge_v1.md → Save as `knowledge_v1.md`
- (etc. for all generated files)

### 2. Create Your New Claude Project

1. Create another new Claude Project (for your actual use case)
2. Upload the generated knowledge base files
3. Paste the custom instructions into Settings

### 3. Start Using It

Your new Claude Project is ready! Start interacting with it according to the setup guide Comet generated.

---

## Try Different Complexity Levels

Comet automatically detects complexity. Try these examples:

### Simple (2 files, <5 min)

```
Generate a Claude Project for: automated email responder for customer support
```

**Output:** CLAUDE.md + custom_instructions.txt only

### Medium (4 files, ~15 min)

```
Generate a Claude Project for: content repurposing engine that converts blog posts to social media content across Twitter, LinkedIn, and Instagram
```

**Output:** + knowledge_v1.md + prompt_templates_v1.md

### Complex (6+ files, 25-30 min)

```
Generate a Claude Project for: multi-agent research pipeline with web scraping, data analysis, and automated report generation with citations
```

**Output:** + research_skill_v1.md + tool_configuration.json (MCP tools)

---

## Common Issues & Solutions

### Issue: "File upload failed"

**Solution:**
- Check file size (each should be < 32 MB)
- Ensure files are .md format
- Try uploading one at a time

### Issue: "Custom instructions too long"

**Solution:**
- Verify you copied `comet_system_prompt.txt` (1,442 chars)
- Check you didn't accidentally copy extra content
- Limit is 3,000 characters - you have room!

### Issue: "Generated output has placeholders"

**Solution:**
- This means your prompt was too vague
- Add more details about your concept
- Specify the domain, use case, and key features

**Example:**
- ❌ Vague: "Create a chatbot"
- ✅ Specific: "Create a customer support chatbot for an e-commerce site that handles order tracking, returns, and product questions"

### Issue: "Output doesn't match my needs"

**Solution:**
- Regenerate with a more detailed prompt
- Specify exact features you need
- Mention any tools/integrations required

---

## Next Steps

### 1. Explore Examples

Check the `examples/` directory in the repository to see:
- Simple project example
- Medium project example
- Complex project example

Each shows what Comet generates for that complexity level.

### 2. Read Best Practices

See `claude_best_practices_2025.md` to understand:
- XML structuring standards
- Progressive disclosure principles
- Optimization techniques

### 3. Customize Templates

Advanced users can:
- Edit `comet_templates_v1.md` to customize output formats
- Add domain-specific knowledge bases
- Create custom shortcuts

### 4. Share Your Success

Generated a great project with Comet?
- Share it in GitHub Discussions
- Submit it as an example (see CONTRIBUTING.md)
- Star the repository to show support!

---

## Quick Reference

### Essential Files

| File | Purpose | When Used |
|------|---------|-----------|
| CLAUDE.md | Project overview | Auto-loaded with every query |
| comet_system_prompt.txt | Core behavior | Every query (via Custom Instructions) |
| comet_templates_v1.md | Output formats | When generating any config |
| claude_best_practices_2025.md | Standards | When validating outputs |
| skill_architecture_patterns.md | Patterns | When creating SKILL.md files |
| shortcuts_reference.md | Guidance | Reference as needed |

### Prompt Formula

```
Generate a Claude Project for: [CONCEPT]

Optional details:
- Domain: [industry/field]
- Features: [key capabilities]
- Tools: [integrations needed]
- Scale: [simple/medium/complex]
```

### Complexity Indicators

Comet chooses complexity based on:
- **Simple:** Single clear task, no tools, basic workflow
- **Medium:** Multiple related tasks, domain knowledge needed
- **Complex:** Multi-step workflows, tool integrations, agent skills

---

## Success Checklist

After setup, verify:

- [ ] All 5 knowledge base files uploaded to Comet project
- [ ] Custom instructions pasted and saved (1,442 chars)
- [ ] Test prompt generates output successfully
- [ ] Generated files have real examples (no placeholders)
- [ ] Output follows Anthropic 2025 standards (XML tags, etc.)

---

## Help & Support

- **Questions:** [GitHub Discussions](https://github.com/promptaholic/comet-claude-generator/discussions)
- **Bugs:** [GitHub Issues](https://github.com/promptaholic/comet-claude-generator/issues)
- **Documentation:** [README.md](README.md)
- **Examples:** [examples/](examples/)

---

**🎉 Congratulations!** You're ready to transform any concept into a production-ready Claude Project in minutes!

**Estimated setup time:** 5 minutes
**Estimated generation time:** 1-30 minutes (depending on complexity)
**Success rate:** 95%+ first-try

Happy building! 🚀
