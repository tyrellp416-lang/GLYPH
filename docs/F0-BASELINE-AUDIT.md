# F0 | Baseline audit

Status: OPEN / evidence pending. Target: b39f448652450c00fdda80346c4e799f48710bae (Expanda v0.3.2).
This is an audit specification, not an audit result. Scope is read-only with respect to product code.

## Objective
Establish the actual condition of the inherited application before proposing implementation. Verify rather than assume README claims, previous brainstorming, issue reports, or code comments.

## Required investigation
1. Provenance: confirm upstream tag/commit, fork ancestry, GPLv3 and third-party notices, dependency versions, manifest permissions, build configuration, SDK requirements, application ID and signing setup.
2. Build/test baseline: inventory modules and tests; record JDK, Gradle, SDK and environment; run supported local build and test tasks when available. Record exact commands, exit codes and failures. Do not incur hosted CI costs without approval.
3. Storage: map Room/SQLite, YAML and other stores, import/export and synchronization authority, transactions, startup/reload behavior, concurrency, migrations, delete semantics, backup and recovery. Identify every persistence writer. Investigate upstream issue https://github.com/diegomarzaa/expanda/issues/18 as a reported defect, not a confirmed root cause. Use synthetic CSV fixtures including approximately 344 unique snippets, edit one, restart, verify every record and exact content across relevant stores. Test failure, duplicate, malformed and interrupted imports. Never use a personal snippet library.
4. Accessibility: map event handling, trigger detection, editor identity, selection, cursor, replacement paths, undo, asynchronous work and service lifecycle. Test rapid typing, app switching, nested input, multiline, Unicode, emoji, composition/IME, concurrent edits, focus change, duplicate events and self-trigger loops. Inspect API 33+ input connection feasibility without changing runtime.
5. Security/privacy: examine protected/password fields, app exclusions, logs, clipboard, exported components, intent handling, file providers, backups, import trust boundaries, recursion/regex resource exhaustion, dependency and permission risks. Never bypass secure editor restrictions or capture real secrets.
6. Compatibility/performance: enumerate current supported editor paths and Android versions; identify representative test cases on Galaxy S24 (ChatGPT, browser, notes, messaging and alternate keyboards where installed), with synthetic text only. Measure baseline latency, memory and battery when physical device available; mark untested paths explicitly.
7. Existing capabilities: map nested snippets, regex, forms, suggestion popup, tags, aliases, actions, undo, import/export and Espanso compatibility. Identify configuration-only options and reusable code for the future command engine; avoid duplicating existing functionality.

## Evidence contract
For every finding: ID, severity, status (confirmed / suspected / not reproduced / unknown), exact revision, source path and line references, reproduction or reasoning, expected vs actual, impact, confidence, proposed minimal fix and regression test. Separate observable facts from hypotheses. Include commands and outputs, test totals, failures, skipped tests, environment and blockers. Do not claim tests or device verification that did not occur.

## Deliverables
- Baseline architecture and data-flow map
- Build/test evidence and coverage gaps
- Prioritized defect/security register
- Reproduction evidence for issue #18 or a precise blocker
- Compatibility and benchmark plan
- Minimal F1 fix proposals, dependency/order and acceptance criteria
- Independent review disposition and remaining risks

## Constraints / gate
No changes to runtime code, upstream repository, real user data, main branch, or release artifacts during F0. No unapproved remote writes, dependency upgrades or CI runs. Use read-only inspection and local disposable fixtures; submit documentation for review on a separate branch. A reviewer must independently challenge material findings and scope before F1. If tooling or device access is missing, report it; do not silently waive the gate. Owner retains final authorization for releases.
