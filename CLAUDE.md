# AI Know-How - Claude Code Instructions

## Project Overview
Personal AI knowledge base using Obsidian (local) + MkDocs Material (web).

## Architecture
- `docs/` = published content (MkDocs content root)
- `_templates/` = Obsidian note templates (not published)
- `_inbox/` = quick capture (not published)
- `mkdocs.yml` = site configuration

## Content Rules
- All content is Markdown with YAML frontmatter
- Use standard Markdown links `[text](path.md)`, NOT Obsidian wikilinks `[[page]]`
- File names: lowercase, hyphens, e.g. `neural-networks.md`
- Every directory in `docs/` has an `index.md`
- Frontmatter must include: title, date, tags, status (draft/published)

## When Adding Content
1. Use appropriate template from `_templates/`
2. Place in correct `docs/` subfolder
3. Add to `nav:` in `mkdocs.yml` if new page
4. Verify with `mkdocs serve` before committing

## Categories
- `fundamentals/` - Core AI/ML concepts
- `llms/` - Large language models
- `tools/` - AI tools & platforms
- `agents/` - AI agents & automation
- `coding/` - AI for development
- `business/` - AI for business
- `research/` - Papers & trends
- `resources/` - Links, courses, glossary

## Build & Preview
```bash
mkdocs serve        # Local preview at http://127.0.0.1:8000
mkdocs build        # Build to site/ directory
```
