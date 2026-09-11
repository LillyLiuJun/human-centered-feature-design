# Case 01: Topic Card Redesign — Aligning Content Contract with Practice Context
# 案例一：话题卡内容重构——对齐内容契约与练习处境

> **Product Domain**: AI English Learning App  
> **Target Surface**: "Talk about today" & "More to talk about" Topic Library Screen  
> **Core Theme**: Why visual polish fails when the underlying content contract and situational context are misdiagnosed.  
> **业务领域**：AI 英语口语学习 App  
> **目标界面**：Library 中的 "Talk about today"（今日话题 Hero 卡）与 "More to talk about"（更多话题卡片）  
> **核心主题**：当底层内容契约与处境错配时，任何表面视觉装修都是徒劳。

---

## 1. The Surface Symptom / 表面表象

### 🇨🇳 中文
团队最初感觉这一屏“怎么改都别扭、不顺手”，以为只是卡片排版、圆角、字体粗细或者信息层级的设计问题。页面包含一张巨大的主推卡片（Hero）和若干小卡片（More to talk about），展示照片、大号加粗句子以及数字（如 `46 pops`、`+12 more moments`）。

### 🇺🇸 English
The team initially felt this screen felt "awkward and disjointed," assuming it was merely a cosmetic UI issue—typography, border-radii, card padding, or visual hierarchy. The screen presented a large Hero card alongside category cards featuring user photos, bold headlines, and numeric counters (e.g., `46 pops`, `+12 more moments`).

---

## 2. Deep Diagnosis via the Skill / 运用 Skill 的深度诊断

### 🇨🇳 中文深度诊断

#### 诊断一：内容契约违背（环节 5 结果评价）——承诺一句话，交付一个类别
- **代码实现**：点击卡片时，代码仅传递了类别名：`onTalk: { onTalk(hero.sceneCategory) }`。卡片上那句引人入胜的加粗句子和泡面照片被完全丢弃。
- **失调效应**：卡片用一个具体生动、带有情绪画面的瞬间把用户勾引进来，点击后却变成泛泛的“我们来聊聊日常起居吧”。感知阶段的承诺与实际交付彻底撕裂。用户第一次错愕，第三次就意识到“这句话只是装饰假象”，卡片自此彻底丧失说服力。

#### 诊断二：槽位体裁失控——六张卡塞了四种不同性质的文本
检查六张卡片的主句内容，发现体裁严重撕裂：
1. `Daily routines` (Hero): *"Don't touch it! Mind your hands, it's hot."* → ✅ 一句真正能说出口的人话。
2. `Food`: *"A simple meal is laid out, featuring stir-fried..."* → ❌ 纯客观图片描述。
3. `Work & study`: *"Let's interpret the stock trends in the image."* → ❌ 给 AI 下达的 prompt 指令。
4. `Social`: *"The footprints you left in my memory."* → ❌ 截图中偶然拍到的歌曲名字。
5. `Tech & gadgets`: *"This app screen provides guidelines..."* → ❌ 手机截图的描述。
6. `Other`: *"The background of this card is a light purple..."* → ❌ 描述卡片背景颜色。

**根因**：数据层读取 `featured.targetExpression ?? userOriginal`。用户自制句子是真话；纯场景照片则降级为图片描述模型生成的说明文。在一个承诺“这是今天可以聊的一句话”的黄金位置，用户读到的 5/6 是毫无沟通欲的机器说明书。

#### 诊断三：处境错配与过度制造动机（处境与 FBM 缺口分析）
通过 Skill 提问用户所处处境：
- **用户心智需求**：“给我个能聊的东西”（匮乏型，连续需求）。
- **用户典型处境**：“固定练习时段”（每天抽出专门的 15 分钟坐下来练口语）。
- **FBM 模型缺口诊断**：
  - **动机 (Motivation)**：✅ 极其充沛——用户是专门坐下来练习的。
  - **时机 (Prompt)**：✅ 完全正确——用户主动打开了页面。
  - **能力感 (Ability / Agency)**：❌ **真正的短板在这里！** 用户坐下来之后卡的不是“想不想练”，而是：
    > *“我该选哪个？选了会发生什么？要聊多久？聊完我能得到什么？”*

**致命设计偏差**：当前设计把 90% 的资源花在了“制造动机”上（大照片、加粗煽情大句、酷炫的 pops 数字），在给一个根本不缺动机的用户拼命灌输动机；而对于用户真正需要的能力感决策支撑，页面上**一个字都没有回答**。

#### 诊断四：库存与欠账——未完成感的重构
- 卡片上的 `+12 more moments` 和 `46 pops` 是恒定接近的数字，属于“静态库存”。
- **库存不产生行动张力，欠账才会产生张力**。连续型需求留住用户的关键在于“满足当下的同时，埋下未完成感”。

---

### 🇺🇸 English In-Depth Diagnosis

#### 1. Content Contract Fracture (Stage 5: Result Evaluation)
- **Code Reality**: Tapping the card only transmitted the broad category string: `onTalk: { onTalk(hero.sceneCategory) }`. The bold, evocative headline and the ambient photo were instantly discarded.
- **Cognitive Impact**: The card tempted the user with a vivid emotional moment, yet delivered an impersonal topic prompt ("Let's discuss daily routines"). The promise upon entry was completely decoupled from the delivery. After repeated disappointments, the user learns that the headline is mere decoration, destroying credibility.

#### 2. Slot Genre Chaos
Analyzing the headline text across cards revealed severe semantic incoherence:
- `Daily routines`: *"Don't touch it! Mind your hands..."* → ✅ A natural conversational phrase.
- `Food`: *"A simple meal is laid out, featuring..."* → ❌ Dry image caption.
- `Work & study`: *"Let's interpret the stock trends..."* → ❌ System prompt to the AI.
- `Social`: *"The footprints you left in my memory"* → ❌ Incidental song title captured in screenshot.
- `Other`: *"The background of this card is light purple"* → ❌ Machine description of UI background.

Only 1 out of 6 cards contained words a human would say. Tying a single headline slot to dual sources (`featured.targetExpression ?? userOriginal`) destroyed the communicative contract.

#### 3. Context Mismatch & Over-Engineered Motivation (FBM Gap Diagnosis)
- **Need Profile**: "Give me something concrete to talk about" (Continuous need, deficiency of prompt).
- **Situated Context**: Dedicated deliberate practice session (sitting down purposefully for a 15-minute drill).
- **FBM Gap Analysis**:
  - **Motivation**: ✅ High — user initiated the session intentionally.
  - **Prompt/Timing**: ✅ Optimal — deliberate session.
  - **Ability (Sense of Agency)**: ❌ **The actual bottleneck.**
    > The user is paralyzed not by lack of desire, but by uncertainty: *"Which one should I pick? What happens next? How long will it take? What will I walk away with?"*

The original design squandered real estate over-manufacturing motivation (oversized hero photos, loud typography, arbitrary pops numbers) while providing zero decision scaffolding.

#### 4. Inventory vs. Debt (Motivation Architecture)
- Static counts like `+12 more moments` represent inert **inventory**.
- Inventory creates no behavioral tension; **digestive debt** ("6 words you haven't spoken yet") generates organic momentum.

---

## 3. The Refactored Solution / 重构解决方案

| Dimension / 维度 | Before (Broken) / 重构前 | After (Human-Centered) / 重构后 | Rationale / 演进理由 |
|---|---|---|---|
| **Core Element** / 主内容 | Volatile sentence / 体裁失控的句子 | 3–4 preview words / 学习目标词簇 | Words are controllable, directly answering *"What vocabulary will I practice?"* / 词汇体裁稳定可控，直接回答“练什么” |
| **Hero Justification** / 推荐理由 | Size only / 仅尺寸放大，无理由 | Explicit trigger: *"6 new words, never talked"* | Explains sovereign reason for recommendation / 明确道出被推荐的真实依据（欠得最多） |
| **Top-Right Metric** / 右上角指标 | `46 pops` (arbitrary noise / 噪音) | `never talked` / `3 days ago` | Replaces vanity metric with actionable recency / 废弃虚荣指标，转为行动决策时间标尺 |
| **Bottom Signal** / 底部提示 | `+12 more moments` (inventory / 库存) | `6 new words you haven't said out loud` | Transforms static inventory into conversational debt / 从静态库存转为有待消化的开口欠账 |
| **Visual Photo** / 配图定位 | Primary stage / 承担主角舞台 | Grounding ambient evidence / 降为生活氛围证据 | Ambient evidence of personal life; text carries clarity / 照片负责真实画面感，文字负责严谨信息交付 |
| **Call To Action (CTA)** | `Start talking →` (opaque / 盲盒) | `Start talking · about 5 min` | Eliminates time investment uncertainty / 明确认知预期与时间成本，赋予从容掌控感 |

---

## 4. Evaluation via the 3 Golden Questions / 三条黄金检验回顾

1. **Restoring balance vs. manufacturing anxiety? / 帮用户回到平衡，还是制造新的焦虑？**
   - *Result*: Switching from vague counts to digestive debt carries a slight anxiety risk. Therefore, the system must incorporate an **"All caught up"** clean state, giving users psychological closure when all topics are digested.
2. **User sovereignty vs. system manipulation? / 用户在掌控，还是被牵着走？**
   - *Result*: By transparently displaying the target vocabulary (`previewWords`) and time commitment (`~5 min`), the user decides deliberately rather than clicking a deceptive visual mystery box.
3. **Situated embedding vs. noisy intrusion? / 嵌入真实处境，还是脱离处境的噪音？**
   - *Result*: Stripped away arbitrary `pops` numbers and replaced them with recency and readiness metrics calibrated specifically for deliberate practice sessions.
