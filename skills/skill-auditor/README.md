# /skill-auditor Skill Documentation

## Overview
`/skill-auditor` is a process-compliance testing engine for other Claude skills. It doesn't judge a skill holistically ("does this feel right") — it derives a scoring rubric directly from the target skill's own stated rules (gates, dormancy conditions, required formats, "never" statements), builds a two-sided test set of positive and adversarial cases, runs each case in an isolated rollout, and applies exactly one bounded, validated edit per round to fix the most severe failure — without ever regressing a hard rule.

Use it before publishing, sharing, or relying on any Claude skill in production.

## Command Interface & Subcommands
- `/skill-auditor [path to SKILL.md]` — Runs the full audit and optimization loop against the specified skill file.
- `/skill-auditor status` — Reports current round, rubric, and remaining known issues.
- `/skill-auditor stop` — Freezes the current state of the target skill file and produces the final summary immediately, without running remaining rounds.

## The 8-Phase Lifecycle
1. **Phase 0 — Derive the rubric.** Determines invocation mode (installed skill vs. pasted file), scans for dependencies, runs a mandatory category scan plus a line-by-line imperative audit, and classifies every rule as a hard rule (PASS/FAIL) or a judgment call (0–2).
2. **Phase 0d — Applicability check.** Halts and asks before running a process-compliance rubric against a skill whose real value is a single deterministically-checkable outcome (e.g. code that compiles) rather than behavioral rules.
3. **Phase 1 — Build a two-sided test set.** 6–10 cases: dormancy/boundary cases, one case per hard rule, one per classification track, an ambiguity case, and realistic cases spanning multiple domains.
4. **Phase 1.5 — Cost estimate and commitment checkpoint.** States rollout count, cost class (plain text vs. artifact-generating), and an approximate token range, then waits for explicit go-ahead before spending anything.
5. **Phase 2 — Run isolated rollouts.** Every test case runs in its own fresh context, with visible per-rollout progress output.
6. **Phase 3 — Score.** Every case is scored against the Phase 0 rubric only — never by vague comparison.
7. **Phase 4–6 — Reflect, edit, validate.** One failure pattern identified per round, one bounded edit applied, then a regression check against every hard-rule case before accepting it.
8. **Phase 7 — Repeat and stop.** Up to 4 rounds, with a progress check-in after round 2, stopping early once a full rollout shows no remaining failures.

## Output
A single, consistently-shaped report: verdict, what was tested, the rubric in plain English, findings (with both a plain-English and technical explanation for each), what wasn't fixed and why, and a jargon-free bottom line — scannable in under a minute.

## Non-Negotiable Constraints
- Never batches multiple fixes into one edit
- Never scores by holistic/vague comparison — only against the numbered Phase 0 rubric
- Hard-rule dimensions always win: an edit that helps elsewhere but breaks a hard rule is rejected
- Every test case runs in a fresh, isolated context
- The rubric and test set are always stated explicitly before any rollout runs
