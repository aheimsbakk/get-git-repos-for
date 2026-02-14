# get-git-repos-for.sh

**Clone or update all GitHub repositories for a specific user.**

## Overview
`get-git-repos-for.sh` fetches all public repositories (and private ones via `GITHUB_TOKEN`) for a GitHub user. It clones new repositories or updates existing ones via fast-forward pulls.

## Requirements
* **bash** (4+)
* **git**, **curl**, **jq**

## Installation
```sh
chmod +x get-git-repos-for.sh
```

## Usage
```sh
./get-git-repos-for.sh [options] <github-username>
```

### Options
| Flag | Description |
| :--- | :--- |
| `-d`, `--dest <DIR>` | Destination directory (default: current directory `.` ). |
| `--use-https` | Use HTTPS clone URLs (default: SSH). |
| `--no-submodules` | Skip submodule initialization/updates. |
| `-v` | Increase verbosity. |
| `-h`, `--help` | Show help. |
| `-V`, `--version` | Show version. |

### Environment
* **`GITHUB_TOKEN`**: Set this environment variable to increase API rate limits or access private repositories.

## Examples

**Clone public repos (SSH default):**
```sh
./get-git-repos-for.sh octocat
```

**Clone via HTTPS to a specific folder:**
```sh
./get-git-repos-for.sh --use-https --dest ~/backups/github octocat
```

**Clone private repos (requires token):**
```sh
GITHUB_TOKEN=ghp_... ./get-git-repos-for.sh octocat
```

## Behavior Details

* **Directory Structure:** Repositories are cloned directly into the destination `DIR/<repo>`. The script creates `DIR` if missing.
* **Pagination:** Fetches repositories in batches of 100 via GitHub REST API.
* **Updates:** Existing repos undergo `git fetch --prune --tags`. A `git pull --ff-only` is attempted only if the working tree is clean and on a branch. Dirty or detached states are skipped to protect local changes.
* **Error Handling:**
    * Missing dependencies or API errors (e.g., 404, rate limit) cause immediate exit.
    * Individual clone failures are logged to stderr; the script continues to the next repository.

### Submodules
* **Auto-Update:** Recursively initializes and updates submodules by default.
* **HTTPS Rewriting:** If `--use-https` is set, the script locally rewrites SSH submodule URLs (e.g., `git@github.com:...`) to HTTPS in `.gitmodules` to ensure access without SSH keys. This change is not pushed to origin.

## Security
* **Tokens:** Never hardcode `GITHUB_TOKEN`. Use environment variables or CI secrets.
* **Protocols:** SSH is the default to prevent credential leakage in logs.

## Roadmap
1. Add unit/integration tests (mocking API).
2. Add CI pipeline.
3. Add Organization support (`--org`).

## License
MIT