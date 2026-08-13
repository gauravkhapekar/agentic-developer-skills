# Agentic Developer Skills 🛠️🤖

A collection of custom modular skills designed to introduce friction, architectural rigor, and Spec-Driven Development (SDD) into prompt-driven engineering with tools like Cursor and Claude Code.

---

## Included Skills

### 1. `/shred` (Adversarial Idea & SDD Engine)
Most AI coding assistants act like cheerleaders—they validate every half-baked idea, encourage over-engineering, and write code without checking for long-term maintenance debt. 

`/shred` is an adversarial ideation skill that acts as a hostile principal engineer.
* **Phase 1 (Subtraction & Gating):** Evaluates surface area (UI vs. headless), checks intent tracks, and locks the gate until you provide empirical metrics.
* **Phase 2 (Destruction):** Stress-tests 12-month failure modes, maintenance tax, and operational blind spots.
* **Phase 3 (Reconstruction & SDD):** Strips away bloat and generates strict, copy-pasteable `FEATURE_SPEC.md`, `TECH_SPEC.md`, and conditional `UI_SPEC.md` files.

#### Quick Command Reference (`/shred`)
* `/shred [idea or file]` — Initializes Phase 1, detects intent tracks, checks interface requirements, and locks the gate.
* `/shred status` — Dumps current phase, intent track, interface mode, and remaining data gaps.
* `/shred veto` — Forces a sharper, opposing counter-argument.
* `/shred pivot` — Transitions from Phase 2 destruction to Phase 3.1 Pre-Flight Risk Resolution.
* `/shred reset` — Wipes session memory and resets state.

#### Testing Examples / Use Cases
Try pasting one of these prompts into your coding agent after loading the skill to see how the shredder reacts:

1. **Internal Tooling Track (Track B):**
   > `/shred I want to build a tool called Meeting IQ where I upload transcripts, get summaries, and manage open tasks across different teams.`
2. **Commercial SaaS Track (Track A):**
   > `/shred I want to build a B2B SaaS tool that automatically generates compliance documentation for SOC 2 by connecting to GitHub and AWS, priced at $99/month.`
3. **UI-Informed Prototype Test (Track C / UI):**
   > `/shred [attach your HTML prototype or describe a dashboard] I want to build a real-time analytics tracker for my local server logs.`

---

### 2. `/skill-auditor` (Universal Skill Testing & Hardening Engine)
Most skill authors ship a `SKILL.md` and hope it behaves — gates get skipped, "never" rules get quietly violated, and nobody notices until it's in someone else's hands.

`/skill-auditor` is a process-compliance tester for other skill files. It never judges holistically ("does this feel right") — it derives a scoring rubric from the target skill's own stated rules, builds a two-sided test set of positive and adversarial cases, runs each case in an isolated rollout, and applies exactly one bounded, validated edit per round to fix the most severe failure — without ever regressing a hard rule the original author wrote.
* **Phase 0 (Rubric Derivation):** Detects installed-skill vs. pasted-file mode, verifies referenced files exist, and runs a mandatory category scan plus line-by-line imperative audit to build a rubric of hard rules and judgment calls.
* **Phase 1–1.5 (Test Set & Cost Gate):** Builds 6–10 dormancy, hard-rule, classification, ambiguity, and realistic test cases, then states an explicit cost/rollout estimate and waits for go-ahead before spending anything.
* **Phase 2–6 (Isolated Rollouts, Score, Fix, Validate):** Runs every case in its own fresh context, scores strictly against the rubric, identifies one failure pattern per round, applies one bounded edit, and regression-checks every hard rule before accepting it.
* **Phase 7 (Repeat & Stop):** Up to 4 rounds, checking in after round 2, stopping early once a full rollout shows no remaining failures.

#### Quick Command Reference (`/skill-auditor`)
* `/skill-auditor [path to SKILL.md]` — Runs the full audit and optimization loop against the specified skill file.
* `/skill-auditor status` — Reports current round, rubric, and remaining known issues.
* `/skill-auditor stop` — Freezes the current state of the target skill file and produces the final summary immediately, without running remaining rounds.

#### Testing Examples / Use Cases
Try pointing `/skill-auditor` at any skill you've written or installed:

1. **Auditing an installed skill:**
   > `/skill-auditor ~/.claude/skills/my-skill/SKILL.md`
2. **Auditing a skill before publishing it:**
   > `/skill-auditor [paste your draft SKILL.md content here]`
3. **Checking progress mid-run:**
   > `/skill-auditor status`

---

## Directory Structure

```text
/agentic-developer-skills
├── README.md                 # Root documentation, commands, and examples
└── skills
    ├── shred
    │   ├── SKILL.md          # Core system instructions for /shred (v3.5.0)
    │   └── README.md         # Detailed usage guide for the shred skill
    └── skill-auditor
        ├── SKILL.md          # Core system instructions for /skill-auditor (v1.0.8)
        └── README.md         # Detailed usage guide for the skill-auditor skill
```

---

## Roadmap
- [ ] Publish an npm package (e.g. `npx agentic-developer-skills add <skill-name>`) so any skill in this repo can be installed into a project's `.claude/skills/` (or equivalent) directory in one command, instead of copy-pasting `SKILL.md` files by hand.
