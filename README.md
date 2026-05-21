# meridian-docs

Context repository for Meridian Field Command project. Claude fetches files from here on demand rather than loading everything into every session.

---

## File Index

| File | Purpose | Fetch when... |
|---|---|---|
| PROJECT-STATUS.md | Current priorities, links, build status | Loaded every session (lives in Claude project) |
| BUSINESS-CONTEXT.md | Entities, pricing, strategy, positioning | Discussing portfolio, pitch, pricing |
| PHASE-3-BUILDOUT.md | Full Phase 3 module specs | Planning or building Phase 3 features |
| INVESTOR-OUTREACH.md | Email templates, platform guide, objections | Investor outreach sessions |
| WEFUNDER-CHECKLIST.md | Campaign checklist and status | Wefunder-specific work |
| TEASER-STRATEGY.md | Teaser inventory, launch stages | Social media / content sessions |
| PRODUCT-SPEC.md | Detailed module specs (future) | Deep product build sessions |

---

## How This Works

1. Claude project only contains the slim PROJECT-STATUS.md
2. At session start, Claude reads PROJECT-STATUS.md to orient
3. When a task requires deeper context, Claude fetches the relevant file from this repo
4. Files here are never auto-loaded — only pulled when needed
5. This keeps the Claude project context window lean every session

---

## Updating These Files

When something changes significantly (new product, pricing shift, strategy pivot), update the relevant file here and note it in PROJECT-STATUS.md under "Recently Completed."
