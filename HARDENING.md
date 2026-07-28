<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow steps use mutable tag references (@v4) instead of pinned 40-character SHA commit digests. This exposes the workflow to supply-chain attacks where a compromised or updated tag could execute malicious code. Affected references:
- actions/checkout@v4 (pre-built-test.yml line 16)
- actions/checkout@v4 (smoke-test.yml line 16)
- actions/setup-node@v4 (smoke-test.yml line 19)
These should be replaced with their full SHA digests, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/pre-built-test.yml:16`
- `.github/workflows/smoke-test.yml:16`
- `.github/workflows/smoke-test.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references to full SHA digests:
- actions/checkout@v4 → actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4 (in both pre-built-test.yml and smoke-test.yml)
- actions/setup-node@v4 → actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4 (in smoke-test.yml)
Original tags preserved as inline comments for readability.

