---
date: 2026-02-13T21:58:00Z
who: assistant@openai
why: simplify CLI by removing redundant long flag
what: remove `--dest-dir` alias from `get-git-repos-for.sh` and docs
model: github-copilot/gpt-5-mini
tags: [scripts,docs]
---

Removed the redundant `--dest-dir` long option in favor of `-d` and `--dest` only. Updated the script help and `README.md` to reflect this change. Files changed: `get-git-repos-for.sh`, `README.md`.
