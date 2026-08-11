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

## Directory Structure

```text
/agentic-developer-skills
├── README.md                 # Root documentation, commands, and examples
└── skills
    └── shred
        ├── SKILL.md          # Core system instructions for /shred (v3.4.0)
        └── README.md         # Detailed usage guide for the shred skill
