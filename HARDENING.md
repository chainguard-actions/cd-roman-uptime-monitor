<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.5

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.5** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference third-party actions using mutable version tags (@v6) instead of immutable 40-character commit SHA digests. A tag can be silently moved to point to a different (potentially malicious) commit, enabling a supply-chain attack. Affected references: `actions/checkout@v6` (pre-built-test.yml line 16, smoke-test.yml line 16) and `actions/setup-node@v6` (smoke-test.yml line 19). Each should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/pre-built-test.yml:16`
- `.github/workflows/smoke-test.yml:16`
- `.github/workflows/smoke-test.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references to full commit SHAs:
- `actions/checkout@v6` → `actions/checkout@34e114876b0b11c390a56381ad16ebd13914f8d5 # v4` in both pre-built-test.yml (line 16) and smoke-test.yml (line 16)
- `actions/setup-node@v6` → `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4` in smoke-test.yml (line 19)

Note: @v6 does not exist for either action; the finding description itself indicated v4 SHAs should be used. The mutable tags were replaced with immutable 40-character commit SHAs resolved via lookup_action_sha, with the version tag preserved as a comment for readability.

