<div align="center">

# Human-Centered Feature Design
### `human-centered-feature-design`

**A calm, principled framework for continuous feature engagement and situated retention.**  
*Rooted in human homeostasis, a sense of agency, and situated context.*

[English](README.md) • [中文说明](README_zh.md) • [Skill Prompt (EN)](SKILL.md) • [Skill Prompt (ZH)](SKILL_zh.md) • [Examples](examples/) • [HTML Preview](preview.html)

---

### *"Humans are not variables of products; products are variables of humans."*

---

</div>

## Overview

**Human-Centered Feature Design** is a standalone, general-purpose framework and AI coding agent skill for designing sustainable product features.

In modern software development, feature iterations often stall not from lack of effort, but from misaligned premises: attempting to manufacture artificial motivation where it is not needed, while overlooking the quiet sense of agency users actually require.

This framework grounds feature decisions in human psychology rather than arbitrary conversion funnels. It can be used independently by product teams, designers, indie makers, or loaded directly into AI coding environments (Claude Code, Antigravity, Cursor) to guide feature architecture, UX flows, and retention mechanisms.

---

## The Foundational Worldview

Every decision in this framework stems from three core postulates about human nature:

```
                    ┌────────────────────────────────────────┐
                    │          Human in Situated Context     │
                    │  (Attention Bandwidth & Daily Rhythms) │
                    └───────────────────┬────────────────────┘
                                        │
                       Deviation from Natural Equilibrium
                                        │
                                        ▼
                    ┌────────────────────────────────────────┐
                    │            The Calm Product            │
                    ├────────────────────────────────────────┤
                    │  • Motivation: Match Need Topology     │
                    │  • Sense of Agency: The 6 Touchpoints  │
                    │  • Trigger: Diagnose Situational Gaps  │
                    └───────────────────┬────────────────────┘
                                        │
                                        ▼
                   Restored Balance · User Feels in Control
```

1. **Humans are Self-Regulating Systems (Homeostasis)**  
   Needs arise when an individual deviates from internal equilibrium (deficiency or overflow). A product cannot manufacture genuine human desire; it can only serve as a friction-free outlet through which existing tension resolves.
2. **Humans are Cognitively Fragile, yet Crave a Sense of Agency**  
   The highest responsibility of a system is to scaffold the user quietly while returning all credit and feeling of capability back to them. **A truly great system is invisible.**
3. **Humans Always Live in Situated Contexts**  
   Whether any feature signal or prompt takes effect depends entirely on its fit with the user's immediate space, time, and mental headroom. **Product influence is borrowed from context, never owned.**

---

## Core Architecture

The framework guides feature design across three distinct architectural layers:

### 1. Motivation Architecture: Aligning with Need Topology

| Need Type | Characteristic | Examples | Retention Principle |
|---|---|---|---|
| **Discrete** | Completion is objectively verifiable; motivation terminates upon resolution. | Weather lookup, translation, routing | **Trade Outcomes for Trust**: Exceed expectations in outcome precision so the tool becomes a reflexive first recall next time. |
| **Continuous** | No external benchmark marks completion; motivation surfaces and ebbs organically. | Curiosity, expression, quiet companionship | **Trade Continuity for Stickiness**: Satisfy the immediate moment while subtly planting an unfinished momentum before hedonic adaptation sets in. |
| **Hybrid** | Grounded in objective milestones, yet the ceiling extends indefinitely. | Learning, writing, fitness | Combine precise outcome delivery with healthy conversational/digestive debt (Debt vs. Inert Inventory). |

### 2. Sense of Agency: The 6 Interaction Touchpoints
A genuine sense of agency is earned through quiet dignity at every stage of the flow:
1. **Perception**: Help users recognize immediately: *"Yes, this is an outlet for what I need right now."*
2. **Search & Association**: Align the system layout with pre-existing mental models to minimize cognitive expenditure.
3. **Decision**: Keep primary paths effortless; provide clear reassurances and fallbacks whenever actions involve perceived cost, uncertainty, or irreversibility.
4. **Action**: Deliver zero-latency status acknowledgement to prevent continuity fractures.
5. **Result Evaluation**: **Upstream alignment** (never promise a specific item on a preview card and deliver a broad category upon tap); attribute the achievement to the user rather than flaunting algorithmic mechanics.
6. **Habit Formation**: Polish and subtract along the Golden Path; prepare secondary depth pathways before adaptation sets in.

### 3. Trigger Design: Situated Activation
* **Deconstruct Real Context**: Physical space (constraints), temporal moment (biological rhythms), and psychological state (available cognitive bandwidth).
* **Diagnose via FBM**: Pinpoint whether the behavioral gap lies in *Motivation*, *Perceived Ability (Cognitive Friction)*, or *Timing*.
* **Contextual Scaffolding**: Manipulate only what the product legitimately controls (information density, pacing, atmosphere) to bridge the diagnosed gap without generating unsolicited noise.

---

## Pre-Ship Evaluation: The Three Golden Questions

Before committing any feature specification, review every decision against these three questions:

1. **Is this design helping the user restore balance, or is it engineering artificial anxiety?**
2. **Does this design leave the user feeling sovereign and in control, or dragged along by system mechanics?**
3. **Is this design embedded naturally in the user's real-world context, or is it introducing intrusive noise?**

*Only when all three questions can be answered in favor of the former is the design validated as human-centered.*

---

## Real-World Reference Implementations (`examples/`)

To demonstrate how this independent framework applies to concrete product decisions, the repository includes two design retrospectives from an AI English learning application:

* **[Case 01: Topic Card Redesign — Content Contract and Context Alignment](examples/01-talk-about-today-cards.md)**  
  *Context*: Topic discovery cards initially felt awkward and were assumed to be a layout styling issue.  
  *Application*: Diagnosing a content contract fracture (promising a vivid sentence while delivering an abstract category) and recognizing that during a deliberate practice session, the missing gap was decision agency rather than motivation.
* **[Case 02: Dynamic Reading State — The 3 Situational Boundaries](examples/02-expand-collapse-state.md)**  
  *Context*: Defining when an expanded long-form reading card should auto-collapse.  
  *Application*: Treating card expansion as a temporary attentional state rather than persistent document state, establishing three distinct boundaries: viewport exit, page exit, and transient interruptions.

---

## Usage & Agent Integration

### Skill File Format
The complete prompt specification is available in both English and Chinese:
- **`SKILL.md`**: Canonical English specification for international AI workflows.
- **`SKILL_zh.md`**: Canonical Chinese specification preserving the author's original phrasing and nuances.

### Integration with AI Coding Environments

#### Claude Code / Antigravity
```bash
# Install globally for Claude Code or Antigravity CLI
mkdir -p ~/.config/skills/human-centered-feature-design
cp SKILL.md ~/.config/skills/human-centered-feature-design/SKILL.md
```

#### Cursor / Local Project Setup
Copy `SKILL.md` into your repository's `.cursor/rules/` or `.skills/human-centered-feature-design/SKILL.md`.

#### Triggering in Conversation
Invoke the skill naturally during product discussions:
> *"Help me design the interaction flow for this feature..."*  
> *"Why might users abandon this flow after the first session?"*  
> *"Evaluate this screen using human-centered-feature-design."*

---

## License

Released under the [MIT License](LICENSE). Open, principled, and free for creators everywhere.
