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

---

## Directory Structure

```text
/agentic-developer-skills
├── README.md                 # Root documentation and overview
└── skills
    └── shred
        ├── SKILL.md          # Core system instructions for /shred (v3.4.0)
        └── README.md         # Specific usage guide for the shred skill
