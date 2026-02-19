# AI Know-How

Personal AI & ML knowledge base.

## Quick Start

### View locally (MkDocs)

```bash
pip install mkdocs-material
mkdocs serve
```
Open http://127.0.0.1:8000

### Edit locally (Obsidian)

1. Open Obsidian
2. "Open folder as vault" → select this repo folder
3. Start writing in `docs/` for published content, `_inbox/` for quick notes

### Add new content

1. Copy a template from `_templates/` into the appropriate `docs/` subfolder
2. Fill in the frontmatter and content
3. Commit and push — site deploys automatically

## Project Structure

```
docs/               Published knowledge base content
  fundamentals/     Core AI/ML concepts
  llms/             Large language models
  tools/            AI tools & platforms
  agents/           AI agents & automation
  coding/           AI for development
  business/         AI for business
  research/         Papers & trends
  resources/        Links, courses, glossary
_templates/         Note templates (not published)
_inbox/             Quick capture (not published)
mkdocs.yml          Site configuration
```

## Deployment

Push to `main` → GitHub Actions builds MkDocs → encrypts with Staticrypt → deploys to Cloudflare Pages.

### Required GitHub Secrets

| Secret | Description |
|---|---|
| `SITE_PASSWORD` | Password for Staticrypt encryption |
| `CLOUDFLARE_API_TOKEN` | Cloudflare API token with Pages permissions |
| `CLOUDFLARE_ACCOUNT_ID` | Your Cloudflare account ID |

### Setup Cloudflare Pages (one-time)

1. Go to https://dash.cloudflare.com → Pages
2. Create project "ai-know-how" (Direct Upload)
3. Create API token: My Profile → API Tokens → Create Token → "Cloudflare Pages Edit"
4. Add secrets to GitHub repo Settings → Secrets and variables → Actions
