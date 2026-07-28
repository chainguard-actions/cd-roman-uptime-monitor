<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.8

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.8** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference external actions using mutable tag refs instead of full 40-character SHA commit hashes. This exposes the workflow to supply-chain attacks if the tag is moved or the upstream repository is compromised.

- `.github/workflows/pre-built-test.yml`: `uses: actions/checkout@v7` (line 16)
- `.github/workflows/smoke-test.yml`: `uses: actions/checkout@v7` (line 16), `uses: actions/setup-node@v6` (line 18)

All three should be pinned to their full commit SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/pre-built-test.yml:16`
- `.github/workflows/smoke-test.yml:16`
- `.github/workflows/smoke-test.yml:18`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references to full 40-character commit SHAs:
- actions/checkout@v7 → @3d3c42e5aac5ba805825da76410c181273ba90b1 # v7 (in both workflow files)
- actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38 # v6 (in smoke-test.yml)
Original tag names preserved as inline comments for readability.

