# Comet: Concept to Claude Project Generator

**Version:** 1.0 | **Purpose:** Transform any concept into production-ready Claude Project configurations | **User:** Developers, AI engineers, teams building Claude Projects

## Overview

Comet is a specialized AI system that converts ANY concept into complete, production-ready Claude Project configurations following Anthropic's 2025 standards. Instead of spending hours manually creating CLAUDE.md files, custom instructions, skills, and knowledge bases, Comet generates the entire stack in minutes with proper XML structuring, progressive disclosure, and real examples.

The system intelligently detects complexity levels and recommends appropriate configuration depth - from minimal 5-minute setups for simple concepts to comprehensive production stacks with multi-agent workflows, MCP tool integrations, and full documentation for complex systems.

Comet follows Anthropic's latest best practices including XML tag standards, semantic versioning, few-shot learning, and progressive disclosure principles to ensure generated configurations work immediately without iteration.

## Core Capabilities

1. **Intelligent Complexity Detection** - Analyzes concepts and recommends minimal, standard, or complete configuration sets based on scope, workflow complexity, and tool requirements

2. **Template-Driven Generation** - Produces consistent, standardized files (CLAUDE.md, custom instructions, SKILL.md, knowledge bases, prompt templates, MCP configs) following established patterns

3. **2025 Standards Compliance** - Ensures all outputs use proper XML structure, valid YAML frontmatter, progressive disclosure, real examples, and semantic versioning

## Workflow

When you provide a concept:

1. **Analysis Phase** - Comet evaluates the concept's complexity, identifies required components, determines if tools/integrations are needed, and estimates setup time

2. **Design Phase** - Selects appropriate template set (minimal/standard/complete), plans file structure, identifies domain knowledge requirements, and maps workflow steps

3. **Generation Phase** - Creates complete file set with real examples, XML-structured instructions, proper versioning, setup guides, and success metrics

4. **Validation Phase** - Ensures 2025 standards compliance, verifies no placeholders remain, confirms all files are copy-paste installable

## Success Metrics

- ✓ Generated configs work first-try without iteration (95%+ success rate)
- ✓ Setup time reduced from hours to minutes (10-30x faster)
- ✓ All outputs include real examples (zero placeholder content)
- ✓ 100% compliance with Anthropic 2025 standards (XML, versioning, progressive disclosure)

## Usage Examples

**Example 1: Simple Concept**
```
Input: "automated email responder for customer support"
Output: CLAUDE.md + custom_instructions.txt (minimal config, <5 min setup)
Complexity: Simple → Suggests /quick-claude or generates minimal config
```

**Example 2: Medium Concept**
```
Input: "content repurposing engine that converts blogs to social posts"
Output: CLAUDE.md + custom_instructions + knowledge_v1.md + prompt_templates_v1.md
Complexity: Medium → Standard config (4 files, ~15 min setup)
```

**Example 3: Complex Concept**
```
Input: "multi-agent research pipeline with web scraping, analysis, and reporting"
Output: Complete stack - all 6 files including SKILL.md + tool_configuration.json
Complexity: Complex → Suggests /full-claude or generates production stack
```

## Knowledge Base Files

This project includes four specialized knowledge bases:

- **comet_templates_v1.md** - All output templates (CLAUDE.md, custom instructions, SKILL.md, knowledge bases, prompts, tool configs)
- **claude_best_practices_2025.md** - Anthropic 2025 standards (XML tags, frontmatter format, progressive disclosure, optimization)
- **skill_architecture_patterns.md** - Skill design patterns (categories, composition, state management, tool integration)
- **shortcuts_reference.md** - Guidance on /quick-claude and /full-claude shortcuts (when to recommend, limitations)

## Maintenance

Update triggers:
- Anthropic releases new Claude API features or Agent Skills updates
- New template patterns emerge from usage
- MCP tool ecosystem expands requiring new integration patterns
- User feedback identifies gaps in generated configurations

Version bumps:
- Patch (1.0.1): Template improvements, better examples, clarifications
- Minor (1.1): New optional components, enhanced knowledge bases
- Major (2.0): Changed core templates, new required standards, breaking changes

---

**Last Updated:** November 15, 2025
**Maintained By:** AI Systems Architecture Team
**License:** MIT
