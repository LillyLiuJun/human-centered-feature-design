<div align="center">

<img src="assets/readme-banner.png" alt="Human-Centered Feature Design Banner" width="100%" />

<br /><br />

# Human-Centered Feature Design
### `human-centered-feature-design`

**Restoring human balance, not manufacturing motivation.**  
*A calm, principled framework for genuine user agency and natural retention.*

[English](README.md) • [中文说明](docs/README_zh.md) • [Skill Prompt (EN)](SKILL.md) • [Skill Prompt (ZH)](docs/SKILL_zh.md) • [Examples](examples/)

---

### *"Humans are not variables of products; products are variables of humans."*  
Needs arise from deviations from balance; products serve as vehicles to restore balance. Products cannot manufacture needs; they can only serve as outlets.

---

</div>

## Core Purpose & Usage Scenarios

**Human-Centered Feature Design** is a reasoning framework designed to **test and refine features to ensure they genuinely fulfill authentic user needs**.

It deduces what users actually require in specific situations—from macro feature definitions down to micro interaction details—grounding product solutions in human psychology rather than team-centric vanity or synthetic stickiness.

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

## The Foundational Worldview

All situated deductions stem from three immutable assumptions regarding human psychology:

```
                    ┌────────────────────────────────────────┐
                    │            The Human in Situ           │
                    │ (Finite cognitive load, biological     │
                    │   rhythms, and environmental context)   │
                    └───────────────────┬────────────────────┘
                                        │
                               Deviates from balance
                                        │
                                        ▼
                    ┌────────────────────────────────────────┐
                    │       Product as Relief Valve          │
                    ├────────────────────────────────────────┤
                    │ • Motivation: Need topology alignment  │
                    │ • Sense of Agency: 6 Touchpoints        │
                    │ • Trigger: FBM contextual gap diagnosis │
                    └───────────────────┬────────────────────┘
                                        │
                                        ▼
                       Balance Restored · Sovereign Agency Felt
```

1. **Human Homeostasis**: Humans are self-regulating systems. Needs arise from disequilibrium. Products cannot manufacture organic desire; they can only serve as frictionless relief valves.
2. **Sense of Agency**: Humans are cognitively fragile yet crave sovereignty. The system's highest virtue is invisible scaffolding, crediting all achievement to the human. **Great systems are quiet.**
3. **Situated Context**: Humans live in concrete physical situations. Influence is borrowed from contextual fit, never permanently owned by the product.

---

## The 3-Part Architecture

### Module 1: Motivation Architecture — Products as Relief Valves
| Need Type | Dynamics | Examples | Retention Mechanism |
|---|---|---|---|
| **Discrete** | Clear, objective completion state. | Weather, dictionary, calculator | **Exchange results for trust**: Precise fulfillment builds subconscious recall for the next deviation. |
| **Continuous** | No objective finish line; fluctuates with state. | Curiosity, expression, companionship | **Exchange continuity for stickiness**: Leave gentle unfinished momentum; manage digestive debt over static inventory. |
| **Hybrid** | Measurable milestones with infinite horizons. | Language learning, writing, coding | Balance concrete results with sustainable progressive tension. |

### Module 2: Sense of Agency — The 6 Touchpoints
Agency is not empty praise; it is earned across six interlocking touchpoints:
1. **Perception**: Translate ambiguous impulses into tangible outlets ("Yes, this is my path forward").
2. **Search & Association**: Align architecture with existing mental models, minimizing needless cognitive overhead.
3. **Decision**: Eliminate decision friction along the Golden Path; provide undo mechanisms for irreversible actions.
4. **Action**: Immediate physical feedback; protect continuous execution.
5. **Result Evaluation**: **Strictly align entry promises with delivery**; attribute success to the user, not algorithm magic.
6. **Habit Formation**: Never break core muscle memory; ready subsequent pathways at moments of peak satisfaction.

### Module 3: Trigger Design — Situated Availability
* **Deconstruct the Real Situation**: Spatial constraints, temporal baselines, and cognitive bandwidth.
* **Diagnose the FBM Gap**: Is the user blocked by motivation, ability (cognitive friction), or poor timing?
* **Scaffold Without Noise**: Provide precise scaffolding at the gap; eliminate unprompted mechanical push notifications.

---

## The Three Litmus Tests

Before deploying any feature or interaction, audit it against these three filters:

1. **Does this return the human to equilibrium, or manufacture synthetic anxiety?**
2. **Does the user feel sovereign agency, or are they being piloted by system mechanics?**
3. **Does this embed into the user's authentic situation, or create tone-deaf noise?**

*A design only ships when all three answers are unequivocally the former.*

---

## Specifications & License
 
* **`SKILL.md`**: Canonical English specification for coding agents and AI workflows.
* **`docs/SKILL_zh.md`**: Complete Chinese prompt specification (100% original text).
* **`docs/README_zh.md`**: Full Chinese documentation and usage guide.
* **`examples/`**: Deep dive retrospective case studies.

Released under the [MIT License](LICENSE). Calm, principled, and free.
