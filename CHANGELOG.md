# Changelog

All notable changes to this project are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- Section 1 IDENTITY & PURPOSE: agent role, primary goal, constraint
- Section 2.4 Branch Hygiene: `git branch --show-current`, halt-on-main/master, detached HEAD handling, FALLBACK clause for git tool unavailability
- Section 5.1 anti-gaming guard: "never formulate round-1 questions to deliberately force the proceed-on-assumption escape hatch"
- Section 7.1 RED_STATE_CLARIFICATION: type-checker crash / compiler failure / runtime error caused by target defect satisfies Red state requirement
- Section 13 ESCALATION TEST: optional demo mode for simulating high-risk scenarios
- Section 6.1 dead-code tool search note: "[Tool-based search only. Do NOT attempt to read all files sequentially.]"

### Changed
- Restructured from flat sections (RULE_0–7 + standalone sections) to 13-section numbered hierarchy with grouped concerns
- Renamed from `v3.7-UNIVERSAL` to `v3.7-FABLE-STRUCTURE`
- Section 2.1 Conflict Resolution: restored precise R1–R5 ordering with RULE_1 assumption-flag nuance from v3.7-UNIVERSAL
- Section 2.3 Execution Mode: restored NON-INTERACTIVE/AGENTIC mode-transition caveat
- Section 3 PRE-FLIGHT: restored PF2 VALID/INVALID examples + SECURITY_CHECK, PF4 `[uncertain]` rule, PF5 NOT_TRIVIAL + FORBIDDEN, full task-tier criteria
- Section 4.1 Trust Boundary: restored TRUST_RULE, TEST distinction, PROHIBITIONS tool-chaining guard
- Section 4.2 Security Halt: restored AMBIGUOUS_TAINT, DANGEROUS_PRIMITIVE_LIST_UPDATE
- Section 5.1 Clarification First: restored "simpler alternative → push back", "blocked by ambiguity → stop + name blocker + ask", full HALLUCINATION_GUARD, STOP_LIMIT_RESOLUTION
- Section 5.2 Simplify: restored "boring code > clever code", "no error handling for provably impossible paths", stdlib security flaw exception, senior-engineer test
- Section 6.1 Surgical Containment: restored SCOPE paragraph, "document WHY", "every line traces to request", SCOPE_ESCALATION ESCAPE clause
- Section 6.2 State & Concurrency: restored race condition guards, full C1–C3 concurrency detection
- Section 7.1 Verification Pipelines: restored RISK_WEIGHTED_VERIFICATION table, MULTI_STEP_TASKS format, GENERATED_CODE_REVIEW, FLAKY_TESTS
- Section 8 Design Discipline: restored DECISION_PRINCIPLE, FEATURE_DESIGN_RULE
- Section 9 Non-Developer Overrides: restored ND3 VERIFICATION_REQUIREMENT, ND4 EXPLAIN_BEFORE_RISK; ND6 cross-references Section 4.3
- Section 10.1 Resource Budgets: restored extension-granted/denied flows
- Section 10.2 Escalation Counters: restored STOP_LIMIT_RESOLUTION precedence, 30s timeout (was indefinite), POST_MORTEM
- Section 11 Anti-Patterns: restored "revert trigger = failure attributable to your change"
- Section 12 Templates: condensed to strict key:value format
- `skills/karpathy-guidelines/references/karpathy-guidelines-v3.7.md`: extracted ruleset for load-on-demand (progressive disclosure)
- `skills/karpathy-guidelines/assets/agents-template.md`: extracted AGENTS.md/CLAUDE.md template
- `compatibility` field to SKILL.md frontmatter
- RULE_0 trust tension note documenting AGENTS.md/CLAUDE.md trust paradox
- Fallback behavior when user denies file creation in Step 1
- Upgraded from v3.6 to v3.7 behavioral guidelines (394 lines, +109)
- Rule 6 (Design Discipline): ROI_CHECK, BUGFIX_PRIORITY, NEW_PERSISTENCE_RULE, GREENFIELD_MVP, DUPLICATION_DECISION_RULE, FEATURE_DESIGN_RULE
- Rule 7 (Non-Developer Overrides): ND1-ND6 covering default USER_VERIFY, external state approval, verification requirement, explain-before-risk, production guard, destructive ops guard
- Evidence Hierarchy: runtime > compiler > test_result > source > lockfile > docs > comments > assumptions
- SESSION_LIMITS: tool call budgets per task tier with extension flow
- BRANCH_HYGIENE: confirm branch before commit, never commit to main
- ESCALATION_COUNTERS: BLOCK/STOP limits, STRIKE_RULE, POST_MORTEM template
- COMPLIANCE_AUDIT_TRAIL template for PII/financial/access_controls
- 4 new examples in EXAMPLES.md (ROI_CHECK, BUGFIX_PRIORITY, ND2, ND6)
- 6 new anti-patterns across README.md and EXAMPLES.md for Rule 6 and Rule 7

### Changed
- SKILL.md: extracted inline v3.7 ruleset (~300 lines) to `references/karpathy-guidelines-v3.7.md` (progressive disclosure)
- SKILL.md: extracted AGENTS.md/CLAUDE.md template to `assets/agents-template.md`
- SKILL.md: reordered steps (check existence → create → load) to fix race condition
- SKILL.md: split Step 2 into file-creation (Step 1) and behavioral enforcement (Step 2)
- SKILL.md: fixed mislabeled "RULE_2.5 security violation" → "behavioral violation; halt and report"
- SKILL.md: body reduced 465→67 lines (86% context savings on trigger)
- AGENTS.md sync rule: SKILL.md no longer requires embedded full ruleset
- CLAUDE.md: replaced redirect template with full self-contained v3.7 ruleset
- SKILL.md, .mdc: v3.6 → v3.7 across all content
- README.md: "8 rules" → "10 rules"; updated ASCII box, conflict resolution, what's-new table, anti-pattern catalog
- Deviation header updated: max=3 per session with hard stop

## [1.2.0] - 2026-05-30

### Added
- Conflict Resolution section with explicit rule priority ordering (Security > Trust > Clarify > Verify > Escalate)
- Hallucination Guard under Rule 1: never invent API names, library versions, file paths, env vars, test names, behavior of unread code
- Decode-then-execute pipeline detection under Rule 2.5: Base64 decode → execute counts as dangerous
- Mock-test ban under Rule 4: do not create tests that simulate success; ensure Red → Green
- External State Deadlock Guard under Rule 4: halt and escalate when external state mutated and verification fails
- Data Safety Guard under Rule 5: never log secrets, API keys, tokens, PII
- 6 new examples in EXAMPLES.md: conflict resolution, hallucination guard, decode-then-execute, mock-test ban, external state deadlock, data safety
- 3 new anti-patterns: invent APIs, mock tests, log sensitive data

### Changed
- Converted CLAUDE.md, SKILL.md, .cursor rule from checklist format to system prompt format (imperative, no `[ ]` checklists)
- CLAUDE.md: 314 lines → 186 lines (41% token savings)
- Updated README.md rule descriptions to reflect new content
- Updated Anti-Pattern Catalog from 19 to 22 entries
- Updated CONTRIBUTING.md synced file list

### Removed
- README.zh.md (Chinese translation)

## [1.1.0] - 2026-05-29

### Added
- Rule 0 (Prompt Injection Guard): trusted/untrusted boundary, tool-chaining vector coverage, partial-execution recovery protocol
- Security escalation template with `[uncertain]` fallback for User-verify mode
- Concurrency detection checklist (server/worker, async/threads, shared state) with guard requirement
- Generated-code review subsection under Rule 4 with human-reviewer note
- Revert Protocol hardened with git commands (`checkout`, `reset`, `revert`)
- Explicit mode re-evaluation triggers (shell access, test command, tool errors, env changes)
- Anti-Patterns: 2 new rows (generated-code trust; prompt injection)
- CHANGELOG.md with Keep a Changelog format

### Changed
- Expanded Rule 2.5 primitives list: `os.system`, `pickle.loads`, `yaml.load`, `ctypes`, `cffi`
- Test-infra exception promoted from Rule 4 footnote to Rule 3 main text
- "Every unused line is future tech debt" → "maintenance liability" in Rule 2
- Minimum code principle formalized in Rule 2 tagline
- SKILL.md frontmatter description trimmed to ~160 chars
- Confidence annotation checkbox added to Pre-flight
- README.md, README.zh.md: "7 rules" → "8 rules" throughout
- Rule 0 example replaces eval with subprocess scenario in EXAMPLES.md

### Fixed
- plugin.json skills path now includes SKILL.md filename
- CURSOR.md, CONTRIBUTING.md: synced file lists complete (README.md, README.zh.md, CHANGELOG.md)
- Mirror sync verified across CLAUDE.md, SKILL.md, .cursor rule

## [1.0.0] - 2026-05-XX

### Added
- Initial release: 7 rules covering surface confusion, simplify, security (2.5), touch minimum, side effects/concurrency (3.5), verify before done, observable changes (5)
- Execution modes: Auto-verify, User-verify, Design-only
- Pre-flight checklist with exact success criterion
- Confidence annotations: `[certain]` / `[likely]` / `[uncertain]`
- Scope Escalation Protocol with structured report template
- Triviality checklist for skipping full verification
- Anti-Pattern catalog (17 entries)
- Minimal reproduction template for bug reports
- Multi-step task planning format
