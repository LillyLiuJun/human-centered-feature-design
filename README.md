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

## Usage

This is a concise, self-contained skill. You can integrate it in three simple ways:

### 1. Manual
Download [`SKILL.md`](SKILL.md) and upload it to Claude.ai Project Knowledge, Cursor/Windsurf rules (`.cursorrules`), or directly into any AI conversation.

### 2. Install to Shared Skills Directory
Clone directly into your local coding agent's shared skills path:
```bash
git clone https://github.com/LillyLiuJun/human-centered-feature-design.git ~/.config/skills/human-centered-feature-design
```

### 3. Let Your Agent Install It
Send this prompt to your coding agent:
```text
Install and enable this skill in my environment: https://github.com/LillyLiuJun/human-centered-feature-design
```

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

## License

Released under the [MIT License](LICENSE).

