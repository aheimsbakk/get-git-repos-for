---
date: 2026-02-14T09:00:00Z
who: opencode@local
why: Rename main script for clarity; bump major version due to breaking change
what: Renamed executable to `sync-github-repos.sh` and bumped VERSION to 2.0.0
model: github-copilot/gpt-5-mini
tags: [rename,version,scripts]
---

Renamed the primary script to `sync-github-repos.sh` for clearer intent. Because the filename change is a breaking change for callers, updated `VERSION` to `2.0.0` in `sync-github-repos.sh`.

Files changed:

- `sync-github-repos.sh` (VERSION -> 2.0.0)
- `scripts/bump-version.sh` (help text updated to reference `sync-github-repos.sh`)

Callers must update invocations to use `sync-github-repos.sh` instead of the prior name.
