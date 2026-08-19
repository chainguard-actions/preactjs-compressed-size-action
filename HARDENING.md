<!-- markdownlint-disable -->

# Hardening Report: preactjs--compressed-size-action/2.9.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **preactjs--compressed-size-action/2.9.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file .github/workflows/ci.yml references two actions using mutable tag refs instead of pinned 40-character commit SHAs. This exposes the workflow to supply-chain attacks if the upstream tag is moved or compromised. Failing references: `actions/checkout@v3` (line 10) and `actions/setup-node@v4` (line 11). These should be replaced with their full SHA digests, e.g. `actions/checkout@<40-char-sha> # v3`.

Locations:

- `.github/workflows/ci.yml:10`
- `.github/workflows/ci.yml:11`

### missing-permissions (severity: medium)

The workflow file .github/workflows/ci.yml has no top-level `permissions:` key and the only job (`build_test`) also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g. write access to contents). A minimal `permissions:` block should be added — for example `permissions: read-all` at the top level, or specific scopes such as `pull-requests: write` and `contents: read` at the job level.

Locations:

- `.github/workflows/ci.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed .github/workflows/ci.yml: (1) Pinned actions/checkout@v3 to full SHA a37ce9120846195fa4ece8f58b268e6043cb2f26 and actions/setup-node@v4 to full SHA 49933ea5288caeca8642d1e84afbd3f7d6820020, preserving the original tags in comments. (2) Added a top-level `permissions: contents: read` block to restrict the default GITHUB_TOKEN to the minimum required scope.

