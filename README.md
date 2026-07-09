# metrics-kit-docs

Content source for the [nestjs-metrics](https://nestjs-metrics.readme.io) hosted documentation site, powered by [readme.io](https://readme.com).

## What this is

This repo holds the Markdown files that readme.io reads to render the public docs at **https://nestjs-metrics.readme.io**.  
It is **not** the source of truth for the API — that lives in [metrics-kit](https://github.com/PedroPCardoso/metrics-kit). When the API docs change there, this repo is updated to reflect them.

## Branch structure

| Branch | Purpose |
|--------|---------|
| `v1.0` | Active content — what readme.io syncs from |
| `main`  | Meta / tooling only (this README, scripts) |

## File layout (v1.0)

```
docs/
  Getting Started/
    getting-started.md   ← mirrors metrics-kit docs/GUIA-NESTJS.md (English)
    _order.yaml
  _order.yaml
reference/
  ReadMeConfig/          ← readme.io reference pages
```

Each Markdown file starts with a readme.io frontmatter block:

```yaml
---
title: <page title>
excerpt: <short description>
hidden: false
---
```

## How to update

After merging doc changes into **metrics-kit**, run the sync script to push the updated content here:

```bash
# 1. Get the current SHA of the file to update
gh api "repos/PedroPCardoso/metrics-kit-docs/contents/docs/Getting%20Started/getting-started.md?ref=v1.0" \
  | python3 -c "import json,sys; print(json.load(sys.stdin)['sha'])"

# 2. Push the new content (see metrics-kit skill: document-new-feature, Step 4)
```

The full sync procedure — including the frontmatter format and the Python/gh API command — is documented in the [`document-new-feature` skill](https://github.com/PedroPCardoso/metrics-kit/blob/master/.claude/skills/document-new-feature/SKILL.md) in the main repo.

## Related

- [metrics-kit](https://github.com/PedroPCardoso/metrics-kit) — monorepo (nestjs-metrics + nextjs-metrics + core)
- [nestjs-metrics.readme.io](https://nestjs-metrics.readme.io) — live docs site
