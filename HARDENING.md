<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.6

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.6** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference GitHub Actions using mutable version tags instead of full 40-character commit SHA digests. This exposes the workflow to supply-chain attacks: if the tag is moved (intentionally or by a compromised maintainer), the workflow will silently execute different code.

Failing references:
- `.github/workflows/pre-built-test.yml`: `uses: actions/checkout@v6` (line 16)
- `.github/workflows/smoke-test.yml`: `uses: actions/checkout@v6` (line 16)
- `.github/workflows/smoke-test.yml`: `uses: actions/setup-node@v6` (line 19)

Each should be pinned to a full SHA, e.g.:
  `uses: actions/checkout@<40-hex-char-sha>  # v6`

Locations:

- `.github/workflows/pre-built-test.yml:16`
- `.github/workflows/smoke-test.yml:16`
- `.github/workflows/smoke-test.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references to full commit SHAs:
- `.github/workflows/pre-built-test.yml` line 16: `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`
- `.github/workflows/smoke-test.yml` line 16: `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`
- `.github/workflows/smoke-test.yml` line 19: `actions/setup-node@v6` → `actions/setup-node@249970729cb0ef3589644e2896645e5dc5ba9c38 # v6`

SHAs were resolved via lookup_action_sha. The mutable version tags are preserved as inline comments for readability.

