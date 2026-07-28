<!-- markdownlint-disable -->

# Hardening Report: cd-roman--uptime-monitor/v1.0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **cd-roman--uptime-monitor/v1.0.4** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow steps reference external actions by mutable version tags instead of full 40-character commit SHAs. This exposes the workflow to supply-chain attacks: if the tag is moved (intentionally or by a compromised maintainer), a different — potentially malicious — commit would be executed. Failing references: `actions/checkout@v5` (line 16).

Locations:

- `.github/workflows/pre-built-test.yml:16`

### unpinned-uses (severity: high)

Workflow steps reference external actions by mutable version tags instead of full 40-character commit SHAs. This exposes the workflow to supply-chain attacks. Failing references: `actions/checkout@v5` (line 16), `actions/setup-node@v4` (line 19).

Locations:

- `.github/workflows/smoke-test.yml:16`
- `.github/workflows/smoke-test.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all unpinned action references to full 40-character commit SHAs:
- .github/workflows/pre-built-test.yml line 16: actions/checkout@v5 → actions/checkout@fbc6f3992d24b796d5a048ff273f7fcc4a7b6c09 # v5
- .github/workflows/smoke-test.yml line 16: actions/checkout@v5 → actions/checkout@fbc6f3992d24b796d5a048ff273f7fcc4a7b6c09 # v5
- .github/workflows/smoke-test.yml line 19: actions/setup-node@v4 → actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4
Original version tags preserved as inline comments for readability.

