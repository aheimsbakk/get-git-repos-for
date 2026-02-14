---
date: 2026-02-13T21:59:00Z
who: assistant@openai
why: remove obsolete long option from help output
what: remove `--dest-dir` from the detailed help text in `get-git-repos-for.sh`
model: github-copilot/gpt-5-mini
tags: [docs,workflow]
---

Updated the detailed `--help` text in `sync-github-repos.sh` to remove the redundant `--dest-dir` alias and reflect the current supported flags (`-d` and `--dest`). Files changed: `sync-github-repos.sh`.
