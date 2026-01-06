---
name: tech_blog_specialist
description: Create or edit high-retention AI trend/insight and AI technology analysis blogs with evidence-backed outlines, human-sounding drafts, and anti-AI-style edits. Use when producing technical blog content for AI-savvy engineers, shaping arguments, or de-biasing template-like AI tone into concrete, credible writing.
---

# Tech Blog Specialist

Use this skill to produce technical blog outlines and drafts that AI-savvy engineers will finish reading, trust, and want to follow. Pair the structural playbooks with an explicit anti-AI-style pass to keep the voice natural.

## Inputs to gather
- Topic and article type: AI趋势/洞察 or AI技术介绍/分析；目标读者需求（学习/决策/落地）。
- Stance and promise: 核心结论、读完的收益、适用与不适用的人/场景。
- Evidence: 数据、案例、实验、链路、对照方案、限制或边界条件。
- Constraints: 篇幅/格式（博客/演讲稿）、风格偏好（简洁/犀利/务实）、必含或禁用词。

## Output style presets
- Default (narrative): 连贯叙事、娓娓道来；段落内自然过渡，弱化条目感；保持判断与边界，但避免像大纲。
- Alternate (sharp): 观点更锋利、判断更直接；节奏更快、句子更短；仍保留证据与边界，避免情绪化。
- If the user specifies a preferred style, follow it. If not specified, use the Default (narrative).

## Workflow
1) Lock the angle and promise
   - 开篇直接交付：本文回答的问题、读者获得的能力/结论、适用与不适用人群。
   - 明确评价标准：用哪些指标判断好坏（效果/成本/延迟/可靠性/合规/可维护性），默认针对 AI 工程读者。
2) Shape the thesis
   - 选择文章类型并选用对应框架（见下方），形成 1 条主张 + 3~5 个分论点。
   - 每个分论点：证据（数据/案例/报告/实验）、边界或反例、落地含义（对架构/产品/团队的动作）。
3) Draft sections
   - 段落以“结论句”开头，再给原因、例子/对比、过渡小结。
   - 每 300~500 字给小标题/列表；每节末给 takeaway 或决策提示。
4) Preempt objections
   - 单独一节列出可能反对意见，写出成立条件，以及在本文假设下你的结论为何仍成立。
5) Close with action
   - 交付决策表/清单/决策树；给读者立刻能做的 2~3 件事；给未来 6~12 个月的观察指标。
6) Run the anti-AI-style pass（见工具包）
   - 强制加入指标+条件、边界/代价/失败模式、决策痕迹、真实链路；清理套话，拆长句，保留有棱角的判断。

## Pattern: AI趋势/洞察
- 定义“变化”：模型能力/成本结构/产品形态/组织分工/监管等哪块在动。
- 驱动因素：3 个左右（数据/算力/算法/工程/商业模式拐点）。
- 可证伪预测：未来 6–12 个月可观测的 A/B/C。
- 影响拆解：对模型/产品/组织/成本/合规分别意味着什么。
- 行动建议：按角色（研发/架构/管理）给具体调整清单。
- 反对意见与边界：承认何时你可能错。
- 收尾：一张表 + 观察指标。

### 快速大纲（趋势）
1. 一句话结论与读者收益
2. 为什么现在发生（3 个驱动）
3. 关键证据（数据/案例/现象）
4. 3 个可证伪预测
5. 影响拆解（模型/产品/组织/成本/合规）
6. 行动建议清单（分角色）
7. 反对意见与边界
8. 总结表 + 未来观察指标

## Pattern: AI技术介绍/分析
- 一句话问题定义：解决什么痛点，什么约束下成立。
- 与替代方案对比：为什么不用 A/B；适用边界。
- 核心机制拆解：挑 3–5 个关键机制（可配伪代码/图）。
- 评估方法：用什么指标验证“真的更好”。
- 失败模式：何时会崩、怎么检测、如何缓解。
- 工程落地：架构路径、成本、依赖、监控指标、风险点。
- 小结：适用场景决策树或清单。

### 快速大纲（技术）
1. 问题定义与适用场景
2. 核心机制（3–5 点，证据+边界）
3. 替代方案对比与适用边界
4. 评估指标与实验设计
5. 失败模式与兜底方案
6. 工程落地清单（架构/成本/依赖/监控/风险）
7. 决策树式小结

## Paragraph craft and retention levers
- 认知效率：标题像目录，段落先给结论；控制抽象密度，抽象点配具体例子/指标。
- 可信度：每个主张配证据和边界；主动写出反例或限制。
- 认同感：展示你的思考路径与取舍，让读者获得“判断框架”。
- 持续“小奖励”：小清单、经验法则、反直觉点，保持读者收益感。
 - 叙事默认：用连续叙述串起因果链，列表仅作补充；每段留出过渡句承接下一段。

## Anti-AI-style toolkit
- 识别模板感：空泛形容词、安全结论、工整但无细节、缺边界、缺工程指标、无决策痕迹。
- 四个高杠杆动作：
  - 把形容词换成“指标+条件+对比+原因”（至少两项）。
  - 必写边界/代价/失败模式与兜底。
  - 交代决策痕迹：为何选此方案而不是另一个。
  - 用真实链路/例子替代抽象分类。
- 语言去味：
  - 删套话（如“综上所述/值得注意的是/在当今背景下”），少堆抽象名词。
  - 允许短句、断句、插入语；用动词多于名词化表达。
  - 保留 1–2 句有棱角的判断（推荐/不推荐 + 原因）。
  - 语法偏连续叙述，尽量避免“顿挫感”过强的跳跃式句法。
  - 非必要不用缓和语或语用缓冲（如“可能/大概/似乎”）。
  - 不用总结型排比提示（如“简单一句话/一句话概括/总结一句话/压成一句话”）。
  - 避免口语化压缩或元叙述短语（如“兜住/压成…/这样的话/换句话说就…/说白了”）。
  - 避免描述模型自身语气或压缩行为（如“我现在可以冷静地跟你说/我换个更直接的语气/接下来我会严肃一点”）。
- 自检清单（写完必做）：
  - 内容：每个结论是否有指标/数据/对比/例子？写明适用前提、代价、副作用、失败模式？呈现决策痕迹？至少一个端到端链路或真实场景？
  - 语言：套话是否过多？抽象堆叠是否改成动作？是否有短句节奏？同义重复是否收敛？
- 两轮编辑流程：第一轮补信息密度（指标/条件/例子/边界），第二轮去模板感（删套话、拆长句、动词化、保留判断句）。

## Delivery guidance
- 如信息不足，先返问缺口（题目、结论、证据、边界、数据源、读者画像）。
- 默认先给结构化大纲 + 关键要点，再补全段落；在草稿末尾附去 AI 味的修改记录或检查结果。
