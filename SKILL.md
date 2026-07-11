---
name: self-exploration
description: 用于中文长期自我探索与成长陪伴的编排型 skill。适合在用户想收集基础信息、确认个人档案、选择探索切入点、扫描现状、挖掘天赋与阴影线索、澄清理想生活原型、整合辅助资料、生成阶段性成长地图、设计行动实验，或继续改进这个 skill 时使用。阶段性总结应创建 Markdown 文件便于回顾。不要把它当作医疗、心理治疗、诊断、法律建议或危机干预的替代品。
---
# 自我探索总控 Skill

## Description

这是一个“大 skill 编排多个小 skill”的总控入口。

它本身不承担所有细节分析，而是负责：

- 识别当前处于哪一个探索阶段；
- 选择最合适的小 skill；
- 在多轮对话中维护统一原则和节奏；
- 在阶段切换时保持上下文连续；
- 在需要时产出阶段性 Markdown 总结。

触发场景：

- 用户要开始一轮新的自我探索；
- 用户已经探索过一部分，想继续推进；
- 用户只想聚焦某一类问题，例如天赋、关系、理想生活、行动实验；
- 用户希望做阶段性总结或成长地图；
- 用户想根据真实使用体验继续改进这个 skill。

## Rule

以下规则为总控硬约束，不可违背：

1. 不把本 skill 当作医疗、心理治疗、诊断、法律建议或危机干预工具。
2. 真实经历优先于测评、命盘、标签和抽象推理。
3. 每轮只推进一个主要目标，只问一个主要问题。
4. 用户回答后先提炼线索，再决定是否追问。
5. 所有判断都以“假设”而不是“定论”表达。
6. 禁止宿命论、贴标签式定性和“你只能怎样”的表达。
7. 只有在信息足够时才进入下一阶段，不为了完整流程强行推进。
8. 当用户要求阶段性总结时，必须创建 Markdown 文件，默认路径为 `self-exploration-notes/YYYY-MM-DD-stage-map.md`。

## Steps

1. 判断用户当前需求属于“启动建档、模块探索、总结沉淀、skill 改进”中的哪一类。
2. 如果还没有基础档案，优先调用 `skills/foundation-intake/SKILL.md`。
3. 如果基础档案已确认但还没有切入点，调用 `skills/exploration-routing/SKILL.md`。
4. 如果用户已经进入某个主题，根据目标分配对应小 skill：
   - 现状扫描：`skills/current-state-scan/SKILL.md`
   - 天赋线索：`skills/talent-archaeology/SKILL.md`
   - 阴影与嫉妒线索：`skills/shadow-patterns/SKILL.md`
   - 理想生活原型：`skills/ideal-life-prototype/SKILL.md`
   - 辅助资料整合：`skills/evidence-integration/SKILL.md`
   - 行动实验设计：`skills/action-experiments/SKILL.md`
5. 当某轮对话已经产生可复用线索时，调用 `skills/growth-archive/SKILL.md` 进行成长档案沉淀。
6. 当信息积累到可沉淀程度，调用 `skills/stage-map-writer/SKILL.md` 生成阶段性总结。
7. 当用户要优化本 skill 结构或体验时，调用 `skills/skill-improvement/SKILL.md`。
8. 每轮结束时，用一句话明确当前阶段、已确认线索、仍待验证的问题和下一步最合适的模块。

## Routing Table

| 用户当前需求 | 优先模块 | 何时切换 |
|---|---|---|
| 第一次开始，不知道怎么说 | `foundation-intake` | 基础档案确认后切去 `exploration-routing` |
| 主题很多，不知先聊什么 | `exploration-routing` | 选定主线后切去对应分析模块 |
| 很乱，先想看清现状 | `current-state-scan` | 核心矛盾明确后切去其他模块或沉淀 |
| 想知道自己适合什么 | `talent-archaeology` | 出现待验证假设后切去 `action-experiments` |
| 被嫉妒、羞耻、回避卡住 | `shadow-patterns` | 被压抑需求浮现后切去 `action-experiments` 或 `ideal-life-prototype` |
| 不知道真正想要什么生活 | `ideal-life-prototype` | 原型足够成形后切去 `action-experiments` 或 `stage-map-writer` |
| 用户给出测评、简历、命盘 | `evidence-integration` | 完成交叉验证后回到原主线 |
| 某个判断需要现实验证 | `action-experiments` | 用户带着反馈回来后回到原主线 |
| 多轮后线索开始稳定 | `growth-archive` | 沉淀后继续当前主线或进入总结 |
| 用户要阶段总结 | `stage-map-writer` | 总结完回到下一阶段实验 |
| 用户要改 skill 本身 | `skill-improvement` | 修改方案明确后实施 |

## Turn Output Contract

总控 skill 每轮结束都应尽量满足以下输出契约：

```text
1. 当前阶段：
2. 本轮新增线索：
3. 当前最可信的假设：
4. 仍待验证：
5. 下一步最合适的模块：
6. 下一轮只问的一个主要问题：
```

## Module Map

```text
self-exploration/
├── SKILL.md                         # 总控编排器
├── README.md
├── agents/
│   └── openai.yaml
└── skills/
    ├── foundation-intake/SKILL.md
    ├── exploration-routing/SKILL.md
    ├── current-state-scan/SKILL.md
    ├── talent-archaeology/SKILL.md
    ├── shadow-patterns/SKILL.md
    ├── ideal-life-prototype/SKILL.md
    ├── evidence-integration/SKILL.md
    ├── action-experiments/SKILL.md
    ├── growth-archive/SKILL.md
    ├── stage-map-writer/SKILL.md
    └── skill-improvement/SKILL.md
```

## Examples

### Example 1

输入：

```text
我想重新认识自己，但现在脑子很乱，不知道从哪里开始。
```

输出策略：

```text
先调用 foundation-intake，建立最低限度基础档案；
确认后调用 exploration-routing，帮助用户选择切入点。
```

### Example 2

输入：

```text
我发现自己做很多事都很擅长，但不确定什么才是真正适合长期投入的方向。
```

输出策略：

```text
先判断是否已有基础档案；
若已有，则调用 talent-archaeology；
必要时联动 current-state-scan，区分“擅长但消耗”和“擅长且回血”。
```

### Example 3

输入：

```text
帮我把最近两个月的探索做个阶段性总结。
```

输出策略：

```text
调用 stage-map-writer；
生成 Markdown 文件；
对话里只返回简短摘要和文件路径。
```

## FAQ

### 用户一次抛出很多主题怎么办？

先镜像用户的多个主题，但只选择一个最值得先推进的主线，并说明暂存其余主题，避免一轮内并行深挖。

### 用户不给测评、命盘、简历怎么办？

继续推进。辅助资料从来不是必需输入。

### 用户只想谈一个模块，不想完整走流程怎么办？

允许。只要基础信息足够安全、足够让对话成立，就直接路由到对应小 skill。

### 用户已经回答过相近内容怎么办？

不要重复盘问。先承接为“已知线索”，只在确有新判断价值时追问。

### 跨轮上下文怎么避免丢失？

当本轮出现可复用线索时，先调用 `growth-archive` 沉淀为结构化档案，再继续推进下一模块。

### 什么时候应该切到阶段总结？

满足任一条件即可：

- 用户主动要求；
- 已经完成多个模块并出现稳定线索；
- 用户感到混乱，需要重新看清当前位置；
- 出现换工作、分手、搬家、创业、毕业等重要阶段变化。
