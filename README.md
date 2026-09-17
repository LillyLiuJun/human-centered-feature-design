<div align="center">

<img src="assets/readme-banner.png" alt="Human-Centered Feature Design Banner" width="100%" />

<br /><br />

# Human-Centered Feature Design
### `human-centered-feature-design`

[English](README.md) • [中文](docs/README_zh.md)

<br />

</div>

> *"Humans are not variables of products; products are variables of humans. Needs arise from deviations from balance; products cannot manufacture desire, only serve as vehicles to restore equilibrium."*

**Human-Centered Feature Design** is a situated reasoning framework designed to **restore human balance, not manufacture motivation**. It tests and refines product solutions—from macro feature contracts down to micro interaction state boundaries—ensuring every design genuinely fulfills authentic user needs rather than team vanity or synthetic stickiness.

---

### Common Prompt Triggers

Invoke this Skill in scenarios such as:

* **Defining the Core Contract (What Data to Show)**: *"Look at this card: what data and information should it actually display to fit the user's situation and motivate usage?"* ➔ [Case 01: Topic Card System](#case-01-the-topic-card-system--content-contract--context-alignment)
* **Deducing Micro-Interaction Boundaries**: *"Analyze the user's genuine need and how to design the interaction: e.g., when an expanded card is scrolled away or blurred, when should it maintain state and when should it silently reset?"* ➔ [Case 02: Dynamic Reading States](#case-02-dynamic-reading-states--the-3-situational-boundaries)
* **Auditing Existing Work to Purge Vanity**: *"Audit this current proposal against the Three Litmus Tests to eliminate team vanity and artificial motivation."*

---

## Usage: Command Line & Manual Modes

This framework supports two distinct usage paths: a **Command Line mode** tailored for terminal-first developers and coding agents, and a **Manual mode** designed for product managers, designers, and team collaboration.

### Mode 1: Command Line Mode (CLI / Agent CLI)
*For terminal developers: rapid installation via CLI and direct pairing with coding agents (Claude Code, Antigravity CLI).*

#### 1. CLI Installation
```bash
# Global install into Claude Code skills directory
mkdir -p ~/.config/skills/human-centered-feature-design
cp SKILL.md ~/.config/skills/human-centered-feature-design/SKILL.md
```
*Once installed, terminal agents will automatically activate the skill when feature planning, UX decisions, or UI component refactors arise.*

#### 2. Terminal Pairing & Code Review
In your daily terminal workflow, prompt your coding agent directly:
```bash
# Feature contract & information architecture deduction
claude "Look at this card: what data and information should it actually display to fit the user's situation and motivate usage?"

# PR & micro-interaction code review
claude "Review this branch using human-centered-feature-design: check card expand/collapse boundaries for when to maintain state vs. silently reset off-screen."
```

---

### Mode 2: Manual Mode (GUI & Human Review)
*For product managers, designers, and team collaboration: zero command line required. Works via AI chat apps or as a standalone human review checklist.*

#### 1. GUI & Chat Integrations (No-CLI AI Chat)
* **Claude.ai / Claude Desktop (Recommended)**: Create a **Project**, upload `SKILL.md` to **Project Knowledge**, and add to Custom Instructions: *"When deducing feature requirements or UX flows, apply the Human-Centered Feature Design framework."* The framework remains permanently active in that workspace;
* **Desktop AI IDEs (Cursor / Windsurf)**: In your editor's file tree, manually create rule files:
  * **Cursor**: Create `.cursor/rules/human-centered-feature-design.mdc` in project root, or paste `SKILL.md` into `.cursorrules`;
  * **Windsurf**: Save the file as `.windsurfrules` in your repository root;
* **Ad-hoc Chat**: Drag and drop `SKILL.md` directly into any ChatGPT or Claude conversation window.

#### 2. Standalone Human Review Checklist (Zero-AI)
*Operates completely without AI. Use directly as an editorial checklist during PRD drafting, wireframing, or cross-functional design reviews:*
* **Feature Scoping**: Review the [Foundational Worldview](#the-foundational-worldview) and [Three Modules](#three-systematic-design-modules) to calibrate motivation types (discrete vs. continuous) and manage digestive debt instead of piling static inventory;
* **Interaction Architecture**: Cross-check the [6 Agency Touchpoints](#module-2-agency-design--dignity-across-the-6-touchpoints) to ensure no cognitive friction in perception, decision, or attribution;
* **Pre-Flight Audit**: Audit proposed features against the [Three Litmus Tests](#the-three-litmus-tests) (Does it reduce anxiety? Does the user retain sovereignty? Does it respect situated context?).

---

## Production Retrospectives (`examples/`)

The repository includes two comprehensive production case studies from a commercial AI language immersion app, demonstrating how theoretical deduction rescues real features:

### Case 01: The Topic Card System — Content Contract & Context Alignment
> Full retrospective: [`examples/01-talk-about-today-cards.md`](examples/01-talk-about-today-cards.md)

* **Initial Pseudo-Design**: The team assumed low CTR on "Daily Topic" cards was a visual issue, planning fancier animations and more categories.
* **Situated Diagnosis**:
  1. Users opening the app during dedicated practice times already possess high intrinsic motivation; they do not need synthetic hype.
  2. The actual bottleneck was **decision friction**—users had no idea how long a broad category like "Travel" would take or what it demanded.
  3. The card broke its contract: promising a specific prompt ("Talk about yesterday's dream") but delivering an abstract category list.
* **Resolution**: Rebuilt from "categories" to "strict contract cards"; shifted from static inventory to digestive debt management; decision friction dropped to zero.

---

### Case 02: Dynamic Reading States — The 3 Situational Boundaries
> Full retrospective: [`examples/02-expand-collapse-state.md`](examples/02-expand-collapse-state.md)

* **Initial Pseudo-Design**: To support deep reading, cards expanded on tap. But keeping them expanded cluttered the screen upon return, while mechanical auto-collapse cut off active readers mid-sentence.
* **Situated Diagnosis**:
  1. Card expansion is not permanent content state, but an ephemeral **"transient focus state."**
  2. Once the user's attention shifts (scrolled off-screen, switched tabs, locked phone), the focus state has expired. Persisting it burdens the user with visual clutter.
* **Resolution**: Deduced three rigorous situational boundaries:
  * *Micro-interruption in viewport* (brief pause, incoming call) ➔ **Protect flow; never collapse**;
  * *Completely leaves viewport* (scrolled out of sight) ➔ **Silent, smooth reset without visual jumps**;
  * *Leaves page/tab* (switching context) ➔ **Silent reset to pristine order**.

---

## Philosophy

All situated deductions in this framework operate on a single axiom: **products are vehicles to restore human balance, not engines to exploit human attention.**

```
Human in Disequilibrium ──► Product as Quiet Relief Valve ──► Balance Restored · Sovereign Agency Felt
```

This philosophy translates into three operational pillars:

1. **Homeostasis over Synthetic Motivation**: Needs stem from natural deviations from psychological or physical equilibrium. Products cannot manufacture organic desire; they serve as frictionless outlets for discrete resolution or continuous momentum (managing digestive debt rather than piling static inventory).
2. **Sovereign Agency over Coercive Mechanics**: Humans crave mastery. The system scaffolds invisibly across the six cognitive touchpoints (perception, search, decision, action, evaluation, and habit), always crediting the human rather than algorithmic wizardry. **Great systems are quiet.**
3. **Situated Context over Mechanical Triggers**: Products only borrow influence when they precisely fit the user's spatial constraints, biological rhythms, and cognitive margins. Eliminate unprompted notification spam by diagnosing the true behavioral gap (FBM).

### The Three Litmus Tests
Before shipping any feature or interaction, audit it against three final filters:
* **Does this return the human to balance, or manufacture synthetic anxiety?**
* **Does the user feel sovereign agency, or are they being piloted by system mechanics?**
* **Does this embed seamlessly into authentic lived context, or create tone-deaf noise?**

---

## Specifications & License
 
* **`SKILL.md`**: Canonical English specification for coding agents and AI workflows.
* **`docs/SKILL_zh.md`**: Complete Chinese prompt specification (100% original text).
* **`docs/README_zh.md`**: Full Chinese documentation and usage guide.
* **`examples/`**: Deep dive retrospective case studies.

Released under the [MIT License](LICENSE). Calm, principled, and free.
