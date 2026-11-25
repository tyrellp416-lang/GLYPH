# GLYPH | Project charter

Status: Initial owner-authorized project direction; implementation and release gates remain pending. 2026-11-25.
Upstream: https://github.com/diegomarzaa/expanda
Pinned starting revision: b39f448652450c00fdda80346c4e799f48710bae (v0.3.2).
License: retain upstream GPLv3, notices and attribution.

## Mission
An offline, programmable text expansion and AI workflow companion for Android. Maximize capability, minimize friction, make every feature earn its place. Preserve the simplicity and supported functionality of Expanda.

## Product boundaries
- Native Kotlin and Compose; prioritize Galaxy S24 testing while preserving supported Android versions unless a documented decision changes them.
- No mandatory cloud, account, subscription, ads, telemetry, Internet permission, keyboard replacement or direct AI integration.
- Existing snippet formats and supported behavior must remain portable; migration must be explicit, reversible and verified.
- No passwords or private personal/project context in this public repository, test fixtures, logs or diagnostics.
- Respect secure fields, per-app exclusions and Android accessibility restrictions. No bypassing protections or automatically submitting prompts.
- Commands are globally consistent by default; explicit app overrides must be visible. Preserve ordinary instant triggers; composition must use a distinct invocation or explicit completion mechanism.
- Deterministic composition preserves instruction text; only deduplicate explicitly equivalent modules, flag declared conflicts, and preview before insertion where appropriate.

## Engineering roles
Owner controls product decisions. ChatGPT coordinates architecture and evidence. Claude is proposed primary implementer; Codex is proposed independent reviewer. These roles do not imply any agent has already started work. One active writer per overlapping scope; keep review independent. No merge or release until relevant evidence and review gates are satisfied.

## Dependency-ordered roadmap
| Stage | Scope | Exit gate |
|---|---|---|
| F0 Foundation | Baseline source/build/security/persistence/accessibility audit | Reproducible baseline and independently reviewed findings |
| F1 Reliability | Confirmed defect fixes, safe storage/import/export, backup/restore, privacy-safe diagnostics | Regression and migration evidence; independent review |
| F2 Command engine | Composition, modifiers, aliases, parameters and search | Deterministic behavior and backward compatibility |
| F3 Knowledge engine | Explicit context blocks, version history, project profiles and freshness warnings | No unintended context disclosure; reversible storage |
| F4 Productivity | Palette, local transformations, prompt builder and bounded chaining | Demonstrable usability and isolated safety tests |
| F5 Qualification | Security, regression, performance and S24 real-app validation | Evidence-backed owner release decision |

Stages are internal development gates, not required separate public releases. F2-F5 scope is directional, subject to audit and evidence. Scheduling, voice triggers, unrestricted scripting, integrated AI and general cross-app automation are out of initial scope.

## Release requirements
- Preserve original app installation and data; separate application ID and independently managed signing key before any distributed test build. Only one expansion service enabled at a time.
- Zero observed snippet loss or unintended text changes in defined regression/safety cases; exact backup restore and migration fidelity.
- 100% pass of defined deterministic compatibility cases; target >=99.9% successful eligible real-editor expansions, report denominator and confidence limitations. Unsupported/protected editors must fail safely.
- Compare latency and battery against upstream on equivalent workloads; set quantitative regression thresholds after baseline measurements.
- Verify offline operation and permission surface, dependency licenses, reproducible build instructions, and GPLv3 compliance for distributed builds.
- Report tests actually run, failures, skipped tests, environment, commit SHAs and unresolved risks. Never imply finite tests guarantee universal compatibility.

## Current status
F0 initiated. No runtime changes, APK, verified build, complete code audit, or independently reproduced upstream defects yet. Main branch remains upstream baseline until a reviewed change is merged.
