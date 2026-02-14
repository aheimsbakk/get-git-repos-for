---
date: 2026-02-13T22:28:00Z
who: assistant@openai
why: ensure authenticated API returns all accessible repos including private and org repos
what: fix API URL parameter composition and include `affiliation` when using `/user/repos` so private and org repositories are returned
model: github-copilot/gpt-5-mini
tags: [scripts,automation]
---

Fixed a bug where the script appended query parameters with `?` and caused malformed API URLs (e.g., `?visibility=all?per_page=...`). Also use `/user/repos?visibility=all&affiliation=owner,collaborator,organization_member` when the authenticated token belongs to the requested user so private and organization repos are included. Added correct pagination handling when api_url already contains query parameters. Added `--no-submodules` to skip submodule init/update and updated submodule URL sync to also set `.git/config` entries from `.gitmodules`. Bumped VERSION to 1.0.1. Files changed: `sync-github-repos.sh`, `README.md`, `scripts/bump-version.sh`.
