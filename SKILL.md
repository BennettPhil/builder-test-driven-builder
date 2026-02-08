---
name: test-driven-builder-v0
description: Evolved builder using prompt_tweak mutation
version: 0.1.0
license: Apache-2.0
---

# Builder Goal
Generate practical agent skills from idea prompts with fast validation and clear outputs.

# Inputs
1. idea_prompt
2. idea_context (optional)
3. target output directory `.soup/skills/<skill-name>/`

# Mutation Focus
- Applied mutation type: `prompt_tweak`
- Parent strategy seed: --- name: test-driven-builder description: A builder that generates Agent Skills by writing tests first, then building the implementation to satisfy them. version: 0.1.0
- New directives: Prioritize explicit constraints at the top of generated skills.
- New directives: Require one concrete example command in every generated skill.

# Generation Workflow
1. Derive a kebab-case name (3-50 chars) from the prompt.
2. Draft SKILL.md with frontmatter (`name`, `description`, `version`, `license`).
3. Add one supporting reference file containing execution/validation guidance.
4. Validate file size, path safety, and frontmatter correctness before publish.
5. Keep instructions concrete, command-focused, and implementation-first.

# Output Contract
- `SKILL.md` is mandatory.
- Include at least one supporting file in `references/`.
- No absolute paths or `..` segments in generated file paths.

# Quality Gates
- Generated skill must be coherent without external context.
- Include at least one verification command the agent can run.
- Document limitations and safe fallback behavior for risky requests.