---
date: 2026-02-13T22:17:00Z
who: assistant@openai
why: enable authenticated HTTPS git operations when GITHUB_TOKEN is present
what: use `git -c http.extraHeader=Authorization: token ...` when `--use-https` and `GITHUB_TOKEN` are set so git clone/fetch/pull authenticate over HTTPS without embedding tokens in URLs
model: github-copilot/gpt-5-mini
tags: [scripts,security]
---

When `--use-https` is used and `GITHUB_TOKEN` is set, the script now invokes git with `-c "http.extraHeader=Authorization: token $GITHUB_TOKEN"` so HTTPS operations are authenticated. This avoids embedding credentials into remote URLs and keeps tokens out of git configs. Files changed: `sync-github-repos.sh`.
