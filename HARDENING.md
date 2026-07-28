<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.7

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.7** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference third-party actions using mutable version tags instead of immutable 40-character commit SHAs. If a tag is moved (e.g. by a compromised upstream), the workflow will silently execute different code. Affected references:
- `actions/checkout@v6` in pre-built-test.yml (line 16) and smoke-test.yml (line 15)
- `actions/setup-node@v6` in smoke-test.yml (line 18)

Fix: pin each reference to a full SHA, e.g. `actions/checkout@<40-hex-sha> # v6`.

Locations:

- `.github/workflows/pre-built-test.yml:16`
- `.github/workflows/smoke-test.yml:15`
- `.github/workflows/smoke-test.yml:18`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references to immutable commit SHAs:
- `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6` in both pre-built-test.yml (line 16) and smoke-test.yml (line 15)
- `actions/setup-node@v6` → `actions/setup-node@249970729cb0ef3589644e2896645e5dc5ba9c38 # v6` in smoke-test.yml (line 18)
SHAs were resolved via the GitHub API using lookup_action_sha.

