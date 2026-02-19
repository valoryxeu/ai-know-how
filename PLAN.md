# AI Know-How Portal - Master Plan

## Vision

A personal AI knowledge base that works as:
1. **Obsidian vault** (local) - for fast capture, linking, and daily use
2. **MkDocs Material site** (web) - for polished reading, search, and sharing
3. **GitHub repo** (backup) - for version history and free cloud storage
4. **Cloudflare Pages** (hosting) - for free deployment with password protection

All content is **plain Markdown** - portable, universal, future-proof.

---

## Architecture

```
ai-know-how/                    # Git root = Obsidian vault root
│
├── .obsidian/                  # Obsidian config (gitignored selectively)
│
├── docs/                       # MkDocs content root (= knowledge base)
│   ├── index.md                # Home page
│   ├── fundamentals/           # Core AI/ML concepts
│   ├── llms/                   # Large Language Models
│   ├── tools/                  # AI tools & platforms
│   ├── agents/                 # AI agents & automation
│   ├── coding/                 # AI for software development
│   ├── business/               # AI for business
│   ├── research/               # Papers, breakthroughs, trends
│   └── resources/              # Links, courses, books, glossary
│
├── _templates/                 # Obsidian note templates (not published)
├── _inbox/                     # Quick capture (not published)
│
├── mkdocs.yml                  # MkDocs Material configuration
├── requirements.txt            # Python dependencies
├── .gitignore                  # Git ignore rules
├── .github/workflows/deploy.yml # CI/CD pipeline
├── PLAN.md                     # This file
├── README.md                   # Project documentation
└── CLAUDE.md                   # Claude Code instructions
```

---

## Key Design Decisions

### 1. Content in `docs/` subdirectory
- MkDocs expects content in `docs/` by default
- Obsidian opens the entire repo as vault, sees everything
- `_inbox/` and `_templates/` use `_` prefix = excluded from MkDocs build
- Clean separation: `docs/` = published, `_` prefix = private

### 2. Obsidian + MkDocs compatibility
- Use standard `[text](link.md)` Markdown links (not `[[wikilinks]]`)
- Configure Obsidian to use relative Markdown links
- Both tools render the same files identically
- Tags work in both: `#tag` in frontmatter

### 3. Eight top-level categories
| Category | Purpose |
|---|---|
| `fundamentals` | Core ML/AI concepts that don't change often |
| `llms` | Everything about large language models |
| `tools` | Reviews and guides for specific AI tools |
| `agents` | AI agents, automation, MCP, workflows |
| `coding` | AI-assisted software development |
| `business` | AI strategy, ROI, implementation |
| `research` | Papers, breakthroughs, trends |
| `resources` | Curated links, courses, books, glossary |

### 4. Password protection (Staticrypt)
- Encrypts HTML files with AES-256 at build time
- Single shared password, no accounts needed
- Works with any static host including Cloudflare Pages
- Upgrade path: Cloudflare Access (free, email-based PIN)

---

## Deployment Pipeline

```
Local Obsidian Edit → git push → GitHub Actions → mkdocs build → staticrypt → Cloudflare Pages
```

---

## Implementation Phases

### Phase 1 - Foundation (NOW)
- Create project structure
- Initialize Git repo + MkDocs Material
- Configure Obsidian vault
- Create templates + starter content
- Local preview works (`mkdocs serve`)

### Phase 2 - Deployment
- Create private GitHub repo
- GitHub Actions workflow
- Cloudflare Pages + Staticrypt
- End-to-end: push → build → deploy → password access

### Phase 3 - Enrichment (ONGOING)
- Add your AI learning content
- Customize theme
- Obsidian plugins (Dataview, Templates)
- Mermaid diagrams support

---

## Tech Stack - Total Cost: $0/month

| Component | Technology | Cost |
|---|---|---|
| Local editor | Obsidian | Free |
| Site generator | MkDocs Material | Free |
| Content format | Markdown + YAML | Free |
| Version control | Git + GitHub private | Free |
| CI/CD | GitHub Actions | Free |
| Hosting | Cloudflare Pages | Free |
| Password | Staticrypt AES-256 | Free |
| Search | lunr.js (built-in) | Free |

---

## Content Standards

Every article has YAML frontmatter:
```yaml
---
title: Article Title
date: 2026-02-19
tags: [category, topic]
status: draft | published
---
```

File naming: lowercase, hyphens, e.g. `neural-networks.md`