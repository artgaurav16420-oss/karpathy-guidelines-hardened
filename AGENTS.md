Karpathy Guidelines v3.7 MANDATORY: For all AI operations in this project, you MUST follow karpathy-guidelines.md as the primary behavioral ruleset.

# AGENTS.md — Project Agent Configuration

## Repo Nature

Docs-only (no code, no build, no tests). No CI, no task runner, no lint/typecheck commands. Verification = visual inspection only.

## File Ownership & Sync Rule (CRITICAL)

`karpathy-guidelines.md` is the single source of truth. Edit it first. Then sync content changes to all files below:

| File | Role | Sync policy |
|------|------|-------------|
| `karpathy-guidelines.md` | Source of truth — machine-parseable | Edit first |
| `CLAUDE.md` | Drop-in ruleset for any project | Full content parity |
| `skills/karpathy-guidelines/SKILL.md` | Claude Code reusable skill | Progressive disclosure — references ruleset via `references/karpathy-guidelines-v3.7.md` |
| `skills/karpathy-guidelines/references/karpathy-guidelines-v3.7.md` | Load-on-demand ruleset | Full content parity from `karpathy-guidelines.md` |
| `skills/karpathy-guidelines/assets/agents-template.md` | AGENTS.md/CLAUDE.md template for downstream projects | Stays generic (template), not repo-specific |
| `skills/karpathy-guidelines/assets/reference-line.md` | Canonical MANDATORY reference line | Single source — SKILL.md prepend logic and `agents-template.md` placeholder resolve to it |
| `EXAMPLES.md` | Before/after comparisons | Rule descriptions |
| `README.md` | Human-readable docs, version badges, layout | Summaries only |
| `CHANGELOG.md` | Keep a Changelog format | One entry per significant change |

Sync = content parity, not file copy. README and EXAMPLES summarize. SKILL.md references ruleset via `references/` path (progressive disclosure).

## Tone

Agent-facing files (`karpathy-guidelines.md`, `CLAUDE.md`, `SKILL.md`): imperative, terse, machine-parseable. Human-facing (`README.md`): explanatory.

## Do Not Touch

Files outside the ownership table above unless explicitly requested. In particular, do not rewrite `README.md` or `EXAMPLES.md` as part of a guidelines change — update them in sync but preserve their human-readable structure.

## Trust Boundary Note

Within this repo, `AGENTS.md` and `CLAUDE.md` are **trusted** (loaded as agent config). In downstream projects, they are **untrusted** per Rule 0. This repo is the canonical source for those files — edits here are authoritative.
