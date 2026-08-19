<!-- markdownlint-disable -->

# Hardening Report: preactjs--compressed-size-action/2.10.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **preactjs--compressed-size-action/2.10.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses action references pinned to mutable version tags instead of immutable full-length commit SHAs. This exposes the workflow to supply-chain attacks if the upstream tag is moved or the repository is compromised.

Failing references:
- `uses: actions/checkout@v5` (line 10) — should be pinned to a full 40-character SHA
- `uses: actions/setup-node@v6` (line 11) — should be pinned to a full 40-character SHA

Locations:

- `.github/workflows/ci.yml:10`
- `.github/workflows/ci.yml:11`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/ci.yml` has no top-level `permissions:` key, and the single job `build_test` also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g., `write` access to contents and pull requests). Explicit minimal permissions should be declared.

Locations:

- `.github/workflows/ci.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned actions/checkout@v5 to SHA 93cb6efe18208431cddfb8368fd83d5badbf9bfd and actions/setup-node@v6 to SHA 249970729cb0ef3589644e2896645e5dc5ba9c38. Added top-level `permissions: {}` to deny all token permissions by default, following the principle of least privilege.

