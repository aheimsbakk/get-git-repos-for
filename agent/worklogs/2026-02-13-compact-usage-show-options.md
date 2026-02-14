---
date: 2026-02-13T20:50:00Z
who: assistant@openai
why: make compact usage more useful
what: include commonly used options (e.g. `-d DIR`) in the compact usage message
model: github-copilot/gpt-5-mini
tags: [scripts,docs]
---

Updated the compact usage printed when the script is run without arguments to include the most-used options (`-d DIR`, `--use-https`, `-v`) so it's immediately actionable in CLI contexts. File changed: `sync-github-repos.sh`.
