---
date: 2026-02-13T19:46:00Z
who: assistant@openai
why: fix runtime errors discovered while testing the script
what: handle curl header correctly and improve submodule HTTPS handling in sync-github-repos.sh
model: github-copilot/gpt-5-mini
tags: [scripts,automation]
---

Fixed two issues found during test runs: (1) ensure the curl auth header is an array to avoid passing an empty argument to curl, and (2) improve submodule initialization when `--use-https` is used by rewriting SSH/git:// submodule URLs to HTTPS, syncing, and updating submodules. Follow-up: update README to document submodule behavior and add a `--no-submodules` option if desired.
