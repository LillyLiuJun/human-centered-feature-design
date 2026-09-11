# Case 02: Dynamic Reading State — Situational Expand/Collapse Lifecycle
# 案例二：交互状态生命周期——从粗糙重置到三重处境边界

> **Product Domain**: AI English Learning App  
> **Target Surface**: Tab1 Today Reading Stream (Passage Cards)  
> **Core Theme**: Designing subtle interaction state lifecycles by honoring human attention spans and invisible system boundaries.  
> **业务领域**：AI 英语学习 App  
> **目标界面**：Tab1 今日阅读流中的长文卡片（Passage Card）展开与收起交互  
> **核心主题**：基于人类真实注意力流与“隐形系统”哲学，拆解细微交互状态的处境化生命周期。

---

## 1. The Challenge & Initial Naive Approach / 需求背景与初期粗糙方案

### 🇨🇳 中文
在英语阅读流中，用户可以点击展开（Expand）一张卡片以阅读深度解析。产品提出了一个需求：“离开当前内容时，自动收起并恢复默认状态”。

**未经 Skill 介入的初版工程师方案**：
1. 在顶层将 Tab1 是否激活的状态传递给子视图；
2. 用户切换离开 Tab1 时，派发一个重置标记；
3. 卡片接收标记并将 `passageExpanded` 重置为 `false`；
4. 仅仅在 Tab1 内上下滚动时，卡片离开屏幕不自动收起（理由是担心“用户滚回来时发现状态突然改变会错愕”）。

**局限性**：工程师把“离开当前内容”简单偷换成了“离开页面（Tab1）”。在同页面上下滑动时，展开的长卡片会一直撑开列表，导致阅读流冗长杂乱，违背了用户“离开当前内容即收起”的真实本意。

---

### 🇺🇸 English
In a language learning reading feed, users can expand a Passage card to inspect deep linguistic explanations. The product owner proposed a refinement: *"When the user leaves the current piece of content, automatically collapse it and restore the default state."*

**The Initial (Pre-Skill) Engineering Implementation**:
1. Pass the active status of Tab1 down to the child view.
2. Fire a reset flag when navigating away from Tab1.
3. Reset `passageExpanded` to `false` upon receiving the event.
4. If the user merely scrolls up or down within Tab1 and the card leaves the viewport, do *not* auto-collapse (justified by fearing the user would feel disoriented if the card reset upon scrolling back).

**The Flaw**: The engineering mindset conflated *"leaving the current content"* with *"leaving the entire Tab"*. When scrolling within the feed, previously opened long cards remained expanded forever, cluttering the scroll stream and failing the original user expectation.

---

## 2. Reframing via the Skill / 运用 Skill 进行的深层重构

通过引入 **Human-Centered Feature Design**，AI 重新审视了状态的本体论与处境边界：

### 🇨🇳 中文哲学洞察与处境拆解

#### 核心认知：状态的本体论
> **Passage 的展开是一种临时的阅读注意力状态，而不是需要永久保留的内容状态。**  
> 当用户结束对该卡片的注意力阅读后，系统应安静地恢复默认稳态。

#### 三重处境的精确解构（Situational Boundaries）

```
                     用户行为与交互处境
                            │
       ┌────────────────────┼────────────────────┐
       ▼                    ▼                    ▼
【处境 1：离开视口】     【处境 2：离开 Tab】     【处境 3：短暂中断】
 完全滑出屏幕外           切至 Library/全屏       内部滚动 / 弹窗 / 键盘
       │                    │                    │
 屏幕外无动画静默收起    静默重置默认结构        坚决保持展开保护心流
 回来时呈现清爽稳态      不触发滚动对齐          不打断当前注意力
```

1. **处境一：卡片完全离开视口（Viewport Exit）**
   - **行为**：用户继续向上或向下滑动，Passage 卡片 100% 离开可视区域。
   - **洞察**：用户的注意力已经彻底脱离当前内容。
   - **系统行为**：**在屏幕外无动画静默收起**。当用户未来再次滑回时，卡片呈现干净利落的默认稳态结构，无需用户手动做家务。
2. **处境二：离开当前 Tab 页面（Page Exit）**
   - **行为**：切换到底部 Tab（如 Library）或其他二级页面。
   - **洞察**：上下文彻底发生范式转移。
   - **系统行为**：所有卡片静默收起；再次返回 Tab1 时呈现稳健基线结构；不播放收起动画，也不触发手动收起时的滚动对齐。
3. **处境三：短暂中断与局部交互（Transient Interruptions）**
   - **行为**：卡片内部的滚动、长卡片仅部分离开视口、软键盘升起/落下、收到系统推送通知、下拉控制中心、App 短暂退入后台。
   - **洞察**：用户的意图心流（Intent Flow）尚未结束，仍处于该卡片的处理中。
   - **系统行为**：**坚决保持展开状态**，绝对不触发自动收起，杜绝在用户思考或被打扰的瞬间破坏心流。

---

### 🇺🇸 English Conceptual Insights & Architectural Boundaries

#### Core Premise: The Ontology of State
> **Expansion is a transient attentional state during active reading, not a persistent document state.**  
> Once the reader's attention moves past the unit, the system should quietly restore internal equilibrium.

#### Precision Deconstruction of the 3 Situational Boundaries:

1. **Boundary 1: Viewport Exit (Attentional Shift)**
   - **Context**: The user continues scrolling until the Passage card 100% departs the active visible viewport.
   - **Diagnosis**: Focus has conclusively migrated to downstream content.
   - **Rule**: **Silently collapse off-screen without animation.** When the user eventually scrolls back, they are greeted by a tidy, predictable baseline list without needing to manually collapse clutter.
2. **Boundary 2: Tab / Page Exit (Contextual Shift)**
   - **Context**: The user switches to the Library or pushes into another full-screen view.
   - **Diagnosis**: The entire conversational modality has shifted.
   - **Rule**: Silently reset all cards to default collapsed states with zero animation; do not fire manual scroll alignment recalculations upon return.
3. **Boundary 3: Transient System & Spatial Interruptions (Attentional Preservation)**
   - **Context**: Scrolling within the card itself; partial card visibility; keyboard appearance; incoming push banners; Control Center swipe; brief app backgrounding.
   - **Diagnosis**: The user's active intent is ongoing; cognitive thread remains intact.
   - **Rule**: **Strictly preserve the expanded state.** Never trigger auto-collapse during micro-distractions.

---

## 3. Agency vs. Invisible System Scaffolding / 能力感与隐形系统

| Interaction Type / 交互类型 | Trigger / 触发机制 | Presentation / 呈现表现 | Psychological Rationale / 心理机制剖析 |
|---|---|---|---|
| **Manual Collapse** / 手动收起 | User deliberately taps collapse / 用户主动点击收起按钮 | Plays smooth collapse animation & aligns card position / 播放丝滑收起动画并智能对齐视口 | **Sense of Agency (能力感)**: User initiates the action; system gives crisp, clear spatial confirmation that *"I am in total control."* / 用户主动发起的行为，系统给予明确反馈，让用户体会到绝对掌控感。 |
| **Automated Reset** / 自动重置 | Card fully leaves viewport or Tab unmounts / 卡片完全滑出屏幕或离开页面 | Happens invisibly off-screen with 0ms animation / 屏幕外无声无息完成，0 毫秒无动画干扰 | **Invisible System (隐形系统)**: The system scaffolds the user without vanity. It never steals the spotlight or performs unprompted animations in front of the user's eyes. / 好的系统是隐形的。系统替用户收拾桌面，但绝不在用户眼前炫技耍花招。 |

---

## 4. Evaluation via the 3 Golden Questions / 三条黄金检验回顾

1. **Restoring balance vs. manufacturing anxiety? / 帮用户回到平衡，还是制造新的焦虑？**
   - *Result*: Avoided infinite expansion clutter in long lists while preventing sudden disruptive state changes right under the user's thumb. Returns the viewport to a peaceful equilibrium.
2. **User sovereign vs. system manipulation? / 用户在掌控，还是被牵着走？**
   - *Result*: Manual collapses provide complete visual mastery; automated resets operate off-screen without unsolicited jumps.
3. **Situated embedding vs. noisy intrusion? / 嵌入真实处境，还是脱离处境的噪音？**
   - *Result*: Precisely distinguished transient interruptions (notifications/keyboards) from genuine exits (scrolling completely away), respecting real-world human focus rhythms.
