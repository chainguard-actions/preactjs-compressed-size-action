<!-- markdownlint-disable -->

# Hardening Report: preactjs--compressed-size-action/2.8.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **preactjs--compressed-size-action/2.8.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses mutable tag refs instead of pinned SHA digests, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Specifically: `uses: actions/checkout@v3` and `uses: actions/setup-node@v4` should each be pinned to a full 40-character commit SHA (e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v3`).

Locations:

- `.github/workflows/ci.yml:10`
- `.github/workflows/ci.yml:11`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and the only job (`build_test`) also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g. `write` access to contents and pull-requests). A minimal permissions block such as `permissions: read-all` or specific scopes (e.g. `contents: read`) should be added.

Locations:

- `.github/workflows/ci.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned actions/checkout@v3 to SHA f43a0e5ff2bd294095638e18286ca9a3d1956744 and actions/setup-node@v4 to SHA 49933ea5288caeca8642d1e84afbd3f7d6820020. Added top-level `permissions: contents: read` block to restrict the workflow token to the minimum required scope.

