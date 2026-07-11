# Self Exploration Skill

这是一个用于中文长期自我探索与成长陪伴的编排型 skill。

它不再把所有逻辑堆在一个超大 `SKILL.md` 里，而是拆成“一个总控 skill + 多个单一职责小 skill”的结构。这样更符合以下约束：

- 单一职责：每个小 skill 只处理一个阶段或一种分析任务。
- 触发清晰：总控 skill 负责路由，小 skill 负责明确场景。
- 结构固定：每个小 skill 都使用 `Description + Rule + Steps + Examples + FAQ`。
- 易于维护：新增或修改某个探索模块时，不需要重写整个 skill。

## 适用场景

- 想开始一轮长期自我探索
- 想先建立基础档案，再逐步推进
- 想只聚焦某个主题，例如天赋、关系、理想生活、行动实验
- 想生成阶段性成长地图并保存为 Markdown
- 想根据真实使用体验继续改进该 skill

## 目录结构

```text
self-exploration/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── skills/
    ├── foundation-intake/
    ├── exploration-routing/
    ├── current-state-scan/
    ├── talent-archaeology/
    ├── shadow-patterns/
    ├── ideal-life-prototype/
    ├── evidence-integration/
    ├── action-experiments/
    ├── growth-archive/
    ├── stage-map-writer/
    └── skill-improvement/
```

## 模块分层

- 入口层：`foundation-intake`、`exploration-routing`
- 洞察层：`current-state-scan`、`talent-archaeology`、`shadow-patterns`、`ideal-life-prototype`、`evidence-integration`
- 推进层：`action-experiments`
- 沉淀层：`growth-archive`、`stage-map-writer`
- 演化层：`skill-improvement`

## 设计原则

- 真实经历优先于标签、测评和命盘。
- 一轮只推进一个主要问题。
- 所有判断都用假设表达，而不是定论。
- 阶段性总结必须落地为 Markdown 文件。
- 允许用户跳过不想提供的资料，也允许只使用单个模块。

## 使用方式

直接调用：

```text
使用 self-exploration 帮我开始一轮自我探索。
```

或提出符合场景的请求：

```text
帮我梳理我到底擅长什么，以及什么事情会让我回血。
```

```text
帮我做最近一个月的阶段性成长总结。
```

## 维护建议

- 调整阶段边界时，优先改对应小 skill，而不是把补丁继续堆回总控文件。
- 新增模块时，先确认它是否真的只解决一个明确痛点。
- 如果一个模块开始承担多个目标，应继续拆分。
- 多轮状态字段建议复用 `references/session-state-schema.md`。
- 阶段总结建议复用 `references/stage-map-template.md`。
