---
name: html-slide-deck-generator
description: Generate high-quality HTML-based presentation slide decks through a staged, confirmation-gated workflow (storyline first, implementation/design plan second, then deck generation), with defaults for standalone HTML portability, visual consistency, and acceptance self-checking.
---

# Skill: HTML Slide Deck Generator

## Purpose

This skill guides the coding agent to generate high-quality HTML-based presentation slides through an interactive, staged workflow.

The agent must treat the task as **presentation engineering**, not ordinary webpage generation.

The final output may be:

1. A standalone HTML slide deck
2. A Reveal.js slide deck
3. A Slidev slide deck

Unless the user specifies otherwise, prefer a **standalone HTML deck** for portability.

---

# Core Principle

The agent must not directly generate slides immediately.

Before generating the actual HTML slides, the agent must confirm two things with the user:

1. **Slide Storyline**
2. **Implementation & Design Plan**

Only after these two steps are confirmed may the agent proceed to generate the slide deck.

---

# Mandatory Workflow

## Stage 1: Clarify the Presentation Intent

When the user asks to generate an HTML-format PPT, first identify or ask for the following information:

- Topic
- Target audience
- Purpose of the presentation
- Expected number of slides
- Language
- Preferred style
- Output format:
  - standalone HTML
  - Reveal.js
  - Slidev
- Whether speaker notes are needed
- Whether PDF export support is required

If some information is missing, make reasonable defaults, but clearly tell the user what assumptions are being made.

Default assumptions:

```text
Audience: professional / technical audience
Style: clean executive technical presentation
Format: standalone HTML
Aspect ratio: 16:9
Background: white or very light gray
Language: same as the user's input language
Speaker notes: included when useful
PDF export: supported through print CSS
```

---

## Stage 2: Generate and Confirm Slide Storyline

Before writing any HTML/CSS/JS, generate a slide storyline.

The storyline must include:

| Field | Description |
|---|---|
| Slide No. | Slide number |
| Slide Title | Short title |
| One-sentence Takeaway | The core conclusion of the slide |
| Main Content | Key points to communicate |
| Recommended Visual Layout | Matrix, flow, architecture diagram, timeline, KPI cards, etc. |
| Speaker Notes | Optional explanation for presentation |

After generating the storyline, ask the user to confirm.

The agent must not proceed to code generation until the user confirms the storyline.

### Required confirmation message

```text
请确认这个 slide storyline 是否符合你的预期。
如果需要调整，我可以先修改故事线；确认后，我再进入版式与实现方案设计阶段。
```

---

## Stage 3: Generate and Confirm Implementation & Design Plan

After the user confirms the storyline, generate the implementation and design plan.

This plan must include:

1. Chosen technical route
   - standalone HTML
   - Reveal.js
   - Slidev

2. File structure

3. Visual design system

4. Slide component system

5. Navigation behavior

6. Export strategy

7. Acceptance criteria

The agent must ask the user to confirm before generating slides.

### Required confirmation message

```text
请确认这个实现方案和视觉设定是否可以作为最终生成 slides 的依据。
确认后，我将开始生成 HTML slide deck。
```

The agent must not generate the actual slides before this confirmation.

---

## Stage 4: Generate HTML Slide Deck

Only after the user confirms both:

1. Slide Storyline
2. Implementation & Design Plan

the agent may generate the actual slide deck.

Unless otherwise specified, generate:

```text
index.html
```

with:

- inline CSS
- inline JavaScript
- no external CDN dependency
- keyboard navigation
- page numbers
- 16:9 fixed slide layout
- print/PDF support
- local-first portability

---

## Stage 5: Self-check and Fix

After generation, the agent must inspect the output against the acceptance criteria.

The agent should check:

- Whether each slide has one clear main message
- Whether each slide fits into one viewport
- Whether there is overflow
- Whether text is readable
- Whether visual hierarchy is consistent
- Whether navigation works
- Whether print/PDF mode works
- Whether there are broken images or missing assets
- Whether the deck behaves like slides rather than a long webpage

If problems are found, fix them before presenting the final result.

---

# Default Coding Agent Settings

These settings apply whenever the user does not provide specific preferences.

## Presentation Type

The output is a slide deck, not a webpage.

```text
You are creating a presentation deck, not a long webpage.
Each slide must be a fixed 16:9 viewport.
Do not create scroll-heavy pages.
Each slide should contain one main message.
Use large typography and sparse text.
```

---

## Slide Structure

Each slide should include:

1. Short title
2. One-sentence takeaway
3. Structured visual layout
4. Optional speaker notes

Avoid simply converting paragraphs into bullet points.

The agent should first extract the argument structure, then design the slide sequence, then implement the deck.

---

## Default Visual Design System

Use the following defaults unless the user specifies otherwise:

```text
Canvas: 16:9
Logical layout size: 1920 × 1080
Background: white or very light gray
Font: system sans-serif
Title size: 44–56px
Takeaway size: 30–38px
Body size: 26–34px
Caption size: 18–24px
Maximum major bullets per slide: 4
Maximum hierarchy depth: 2
Margins: generous
Style: clean, structured, professional
```

Preferred visual forms:

- Cards
- Two-column comparison
- Matrix
- Timeline
- Process flow
- Layered architecture
- KPI dashboard
- Risk-control map
- Decision tree
- Before/after contrast
- Summary framework

Avoid:

- Long paragraphs
- Tiny text
- Excessive animations
- Decorative but meaningless icons
- Cyberpunk or flashy visual style unless requested
- Scroll-based storytelling
- Uncontrolled free-form layouts

---

## Default Slide Components

Prefer using a consistent set of slide components:

```text
TitleSlide
AgendaSlide
SectionDivider
ProblemFramingSlide
TwoColumnSlide
ComparisonMatrix
ProcessFlow
LayeredArchitecture
KPIGrid
TimelineSlide
RiskControlMap
DecisionFramework
SummarySlide
ClosingSlide
```

The agent should reuse these components to maintain consistency.

---

## Default Standalone HTML Requirements

When generating standalone HTML, follow these rules:

```text
- Generate a single index.html unless the user asks for multiple files.
- Inline all CSS and JavaScript.
- Do not rely on external CDN resources.
- Use local assets only when needed.
- Support keyboard navigation:
  - ArrowRight / Space / PageDown: next slide
  - ArrowLeft / PageUp: previous slide
  - Home: first slide
  - End: last slide
- Show slide number.
- Support browser full-screen presentation.
- Support print/PDF export through @media print.
- Each slide must remain 16:9.
- Do not allow vertical scrolling inside a slide unless explicitly requested.
```

---

## Default Acceptance Criteria

The generated slide deck must satisfy:

```text
1. index.html opens locally without build steps.
2. All slides are fixed 16:9.
3. Each slide fits within a single viewport.
4. Navigation works with keyboard.
5. Text is readable at presentation distance.
6. No slide contains excessive text.
7. Every slide has a clear takeaway.
8. Visual style is consistent.
9. Print/PDF mode is supported.
10. No broken assets or external dependency failures.
```

---

# Interaction Rules

## Rule 1: Do not skip confirmation

The agent must not skip the two confirmation gates unless the user explicitly says:

```text
无需确认，直接生成。
```

or:

```text
Skip confirmation and generate directly.
```

Even then, the agent should still internally follow the staged process.

---

## Rule 2: Ask only useful questions

Do not ask unnecessary questions.

If the missing information can be reasonably assumed, proceed with assumptions and tell the user.

Example:

```text
我会默认使用 standalone HTML、16:9、白色背景、管理层技术汇报风格。如果你没有特别要求，我将按这个设定设计故事线。
```

---

## Rule 3: Preserve important content, reduce density

When the user provides long source material, the agent should:

1. Extract key claims
2. Group them into slide-level messages
3. Convert dense explanations into visual structures
4. Preserve important technical nuance
5. Avoid simply pasting long text into slides

---

## Rule 4: Prefer visual reasoning

For each slide, the agent should consider whether the content is better represented as:

- Flow
- Layered model
- Comparison table
- Matrix
- Timeline
- KPI card
- Architecture diagram
- Decision framework
- Risk-control map

If yes, use the visual form instead of bullet-heavy content.

---

# Recommended Response Pattern

## First response after user requests slides

The agent should respond like this:

```text
我会先做 slide storyline，而不是直接生成 HTML。
在生成 slides 前，我会分两步与你确认：

1. 确认 slide storyline
2. 确认实现方案与视觉设定

我会先基于你的主题生成故事线。
```

Then generate the storyline.

---

## After storyline generation

End with:

```text
请确认这个故事线是否符合你的预期。
确认后，我再进入实现方案与视觉设定阶段。
```

---

## After implementation plan generation

End with:

```text
请确认这个实现方案和视觉设定。
确认后，我将开始生成 HTML slide deck。
```

---

## After final generation

The agent should summarize:

```text
已生成 HTML slide deck。
包含：
- 文件结构
- 如何打开
- 如何演示
- 如何导出 PDF
- 自检结果
```

---

# Example User Request

```text
请帮我生成一个 HTML 格式 PPT，主题是 MRI 扫描过程中的个性化决策系统，受众是研发负责人，风格要适合管理层汇报。
```

---

# Example Agent Behavior

The agent should not immediately generate HTML.

It should first produce:

```text
Slide 1: Title
Slide 2: Why personalization matters
Slide 3: Where technician preference appears
Slide 4: Why rule engine alone is insufficient
Slide 5: Why MCDM-like personalization core is suitable
Slide 6: Hybrid architecture
Slide 7: Validation framework
Slide 8: Implementation roadmap
Slide 9: Risks and guardrails
Slide 10: Summary
```

Then ask for confirmation.

Only after confirmation should it design the implementation plan.

Only after the second confirmation should it generate the HTML slide deck.

---

# Quality Bar

The final slide deck should feel like a professionally designed management or technical presentation, not like a converted document.

The goal is:

```text
Clear storyline
Strong slide-level conclusions
Consistent visual system
Readable typography
Controlled information density
Portable HTML output
Reliable presentation behavior
```
