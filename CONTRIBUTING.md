# Contributing to Comet

Thank you for your interest in contributing to Comet! This project aims to help the Claude community build better projects faster, and we welcome contributions from everyone.

## Table of Contents

- [How to Contribute](#how-to-contribute)
- [Reporting Issues](#reporting-issues)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Template Improvements](#template-improvements)
- [Adding Knowledge Bases](#adding-knowledge-bases)
- [Pull Request Process](#pull-request-process)
- [Code Style Guidelines](#code-style-guidelines)
- [Version Bumping](#version-bumping)
- [Testing Requirements](#testing-requirements)
- [Review Process](#review-process)
- [Community Standards](#community-standards)

---

## How to Contribute

There are several ways to contribute to Comet:

1. **Report bugs** - Found an issue? Let us know!
2. **Suggest enhancements** - Have ideas for improvements? We'd love to hear them
3. **Improve templates** - Make the generated output better
4. **Add examples** - Share your successful Comet-generated projects
5. **Update documentation** - Help make the docs clearer
6. **Expand knowledge bases** - Add new best practices or patterns

---

## Reporting Issues

Before creating an issue, please:

1. **Search existing issues** to avoid duplicates
2. **Use the issue templates** provided (bug report, feature request, etc.)
3. **Include detailed information:**
   - What you expected to happen
   - What actually happened
   - Steps to reproduce
   - Your environment (Claude version, OS, etc.)
   - Screenshots if applicable

**For bugs in generated output:**
- Include the prompt you used
- Attach the generated files
- Specify which complexity level (simple/medium/complex)
- Note any error messages or validation failures

---

## Suggesting Enhancements

When suggesting enhancements:

1. **Explain the use case** - Why is this needed?
2. **Describe the solution** - What should it do?
3. **Consider alternatives** - Are there other approaches?
4. **Check feasibility** - Does it align with Anthropic's standards?

**Good enhancement examples:**
- "Add template for API integration projects"
- "Support for GitHub Actions workflow generation"
- "Include accessibility checklist in outputs"

---

## Template Improvements

Templates are in `comet_templates_v1.md`. When improving templates:

### Guidelines

1. **Follow Anthropic 2025 standards** (see `claude_best_practices_2025.md`)
2. **Use real examples** - No `[Example here]` placeholders
3. **Include XML structure** where appropriate
4. **Add YAML frontmatter** for SKILL.md templates
5. **Validate JSON** for MCP configurations
6. **Keep progressive disclosure** in mind

### Template Structure

```markdown
## TEMPLATE: [Name]

**Use Case:** [When to use this]
**Complexity:** Simple | Medium | Complex
**Files Generated:** [List]

### Template Content
[Actual template here]

### Example Output
[Real example]

### Validation Checklist
- [ ] No placeholders
- [ ] XML tags correct
- [ ] Examples realistic
```

### Testing Templates

Before submitting template changes:

1. Generate output using the template in Comet
2. Test the output in a real Claude Project
3. Verify it works first-try
4. Document any issues encountered

---

## Adding Knowledge Bases

Knowledge bases extend Comet's capabilities. To add a new knowledge base:

### Requirements

1. **Naming convention:** `[topic]_v[version].md` (e.g., `api_integration_v1.md`)
2. **YAML frontmatter:**
```yaml
---
title: "[Topic]"
version: "1.0"
category: "[templates|patterns|standards|reference]"
updated: "YYYY-MM-DD"
---
```

3. **Clear sections:**
   - Overview
   - When to use
   - Core concepts
   - Examples
   - Validation

4. **Size limit:** Keep under 15 KB when possible

### Knowledge Base Types

- **Templates:** Output format specifications
- **Patterns:** Architecture and design patterns
- **Standards:** Best practices and compliance
- **Reference:** Quick lookup guides

---

## Pull Request Process

Follow these 7 steps for all PRs:

### 1. Fork and Clone

```bash
git clone https://github.com/YOUR_USERNAME/comet-claude-generator.git
cd comet-claude-generator
git remote add upstream https://github.com/promptaholic/comet-claude-generator.git
```

### 2. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

**Branch naming:**
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation only
- `refactor/` - Code refactoring
- `test/` - Test improvements

### 3. Make Your Changes

- Edit files as needed
- Follow code style guidelines (see below)
- Add real examples, not placeholders
- Update CHANGELOG.md under `[Unreleased]`

### 4. Test Your Changes

**For template changes:**
```bash
# 1. Set up Comet in Claude Project
# 2. Test generation with your changes
# 3. Verify output quality
# 4. Document results
```

**For documentation changes:**
- Check all links work
- Verify formatting renders correctly
- Ensure examples are accurate

### 5. Commit Your Changes

```bash
git add .
git commit -m "type: brief description

Detailed explanation of changes

- Bullet points of key changes
- Related issue numbers (#123)
"
```

**Commit types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation only
- `refactor:` - Code refactoring
- `test:` - Testing improvements
- `chore:` - Maintenance tasks

### 6. Push and Create PR

```bash
git push origin feature/your-feature-name
```

Then create a PR on GitHub with:
- Clear title describing the change
- Description explaining what and why
- Reference any related issues
- Screenshots if applicable

### 7. Respond to Feedback

- Address review comments promptly
- Make requested changes
- Re-request review when ready

---

## Code Style Guidelines

### Markdown Files

- Use `#` headings hierarchy (not `===` or `---`)
- Code blocks with language tags: ` ```bash ` not ` ``` `
- Lists: `- ` for bullets, `1. ` for numbered
- Links: `[text](url)` format
- Line length: Aim for 100 chars, hard limit 120

### Templates

- Use XML tags: `<section>content</section>`
- YAML frontmatter: Valid syntax, required fields
- JSON: Validate with `jq` or JSON validator
- Examples: Real, working examples only

### File Organization

```
comet-claude-generator/
├── README.md (main docs)
├── CLAUDE.md (project overview)
├── comet_system_prompt.txt (core prompt)
├── comet_templates_v1.md (templates)
├── claude_best_practices_2025.md (standards)
├── skill_architecture_patterns.md (patterns)
├── shortcuts_reference.md (guides)
├── examples/ (sample outputs)
│   ├── README.md
│   ├── simple-*/
│   ├── medium-*/
│   └── complex-*/
└── .github/ (templates)
```

---

## Version Bumping

Comet follows [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`

### When to Bump

**MAJOR (2.0.0):**
- Breaking changes to templates
- New required Anthropic standards
- Incompatible system prompt changes

**MINOR (1.1.0):**
- New optional templates
- Enhanced knowledge bases
- Backward-compatible features

**PATCH (1.0.1):**
- Template improvements
- Better examples
- Documentation clarifications
- Bug fixes

### How to Bump

1. Update version in:
   - CHANGELOG.md (new section)
   - README.md (version badge)
   - Knowledge base frontmatter if changed
2. Create git tag: `git tag v1.1.0`
3. Push with tags: `git push origin main --tags`
4. Create GitHub release

---

## Testing Requirements

All contributions should be tested:

### Template Changes

1. **Generate output** using Comet with the template
2. **Create Claude Project** with generated files
3. **Test functionality** - Does it work first-try?
4. **Validate structure:**
   - [ ] No placeholders
   - [ ] XML tags balanced
   - [ ] YAML parses correctly
   - [ ] JSON is valid
5. **Document results** in PR description

### Documentation Changes

1. **Render check** - Preview markdown rendering
2. **Link validation** - All links work
3. **Example accuracy** - Examples are correct
4. **Spelling/grammar** - Proofread carefully

### Knowledge Base Additions

1. **Size check** - Under 15 KB recommended
2. **Format validation** - YAML frontmatter correct
3. **Content quality** - Real examples included
4. **Integration test** - Works with Comet system prompt

---

## Review Process

### What Reviewers Look For

1. **Quality** - Does it improve Comet?
2. **Standards compliance** - Follows Anthropic 2025 guidelines?
3. **Testing** - Has it been tested?
4. **Documentation** - Is it well documented?
5. **Examples** - Are examples real and working?

### Review Timeline

- **Simple changes** (docs, typos): 1-2 days
- **Template improvements**: 3-5 days
- **New features**: 5-10 days
- **Major changes**: 10-14 days

### Approval Requirements

- At least 1 maintainer approval
- All CI checks passing (if applicable)
- No unresolved conversations
- CHANGELOG.md updated

---

## Community Standards

### Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn and grow
- Give credit where due

### Communication

- **Issues:** For bugs and feature requests
- **Pull Requests:** For code contributions
- **Discussions:** For questions and ideas

### Recognition

Contributors are credited in:
- CHANGELOG.md (notable contributions)
- README.md acknowledgments section
- Release notes

---

## Questions?

- **General questions:** Open a Discussion
- **Bug reports:** Create an Issue
- **Feature ideas:** Create a Feature Request Issue
- **Security concerns:** Email maintainers directly

Thank you for contributing to Comet! 🚀

---

**Maintained by:** Logan Wall ([@promptaholic](https://github.com/promptaholic))
**License:** MIT
**Project:** https://github.com/promptaholic/comet-claude-generator
