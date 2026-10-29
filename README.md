# Agent Skills

ZWT 的个人 AI Agent 技能集合，涵盖问题澄清、第一性原理分析、路径审查、分层学习、产品共创、决策审查、开发质量、技术能力映射与多 Agent 协作。仓库说明使用中文，技能正文保留各自原始语言，每个 skill 独立维护。

## 技能列表

| Skill | 用途 | 显式调用 | 调用策略 |
| --- | --- | --- | --- |
| [意图洞察与强重述](skills/zwt-intent-clarifier/SKILL.md) | 结合上下文补全含糊的表达，强重述真正问题，当轮给出建议并邀请校正；只讨论，不实施。 | `$zwt-intent-clarifier` | 仅显式 |
| [苏格拉底式问题澄清](skills/zwt-socratic-inquiry/SKILL.md) | 通过最多六个逐一提出的问题澄清困惑，形成六项摘要，确认新问题后再给判断与建议。 | `$zwt-socratic-inquiry` | 仅显式 |
| [第一性原理拆解与重构](skills/zwt-first-principles/SKILL.md) | 区分事实、假设、目标与资源约束，重新推导可行路径，明确成立前提和第一步验证；只讨论，不实施。 | `$zwt-first-principles` | 仅显式 |
| [目标导向与路径审查](skills/zwt-goal-path-review/SKILL.md) | 区分目标与手段，核实关键约束，比较原方案和有价值的替代路径，建议保留、简化或替换；只讨论，不实施。 | `$zwt-goal-path-review` | 仅显式 |
| [双层讲解与理解检查](skills/zwt-layered-explainer/SKILL.md) | 用小白版和专业版解释概念，配具体例子，整理术语对应、易错点及三个理解检查问题。 | `$zwt-layered-explainer` | 仅显式 |
| [产品共创与确认](skills/zwt-product-co-design/SKILL.md) | 补全和修正产品需求，形成完整功能、交互与验收方案，在实施前与用户确认。 | `$zwt-product-co-design` | 仅显式 |
| [双向钢人决策审查](skills/zwt-decision-steelman/SKILL.md) | 完整重述真正问题，构建支持与反对的最强可信论证，识别关键变量并形成判断。 | `$zwt-decision-steelman` | 仅显式 |
| [通用开发质量基线](skills/zwt-development-baseline/SKILL.md) | 在已授权开发中补齐必要的产品与工程保障，完成受影响的旧实现清理，选择最简单的充分实现并按风险验证。 | `$zwt-development-baseline` | 允许隐式 |
| [Capability Mapping（能力映射）](skills/zwt-capability-mapping/SKILL.md) | 为框架集成、跨子系统改动与迁移选择权威能力归属和受支持的实现接入点，按需处理兼容性。 | `$zwt-capability-mapping` | 允许隐式 |
| [Orchestrator（协作编排）](skills/zwt-orchestrator/SKILL.md) | 由当前主模型负责整体结果，按任务选择工作模型与推理强度，明确子任务归属并验证集成结果。 | `$zwt-orchestrator` | 仅显式 |

## 安装

在 Codex 中使用内置的 skill-installer，可以直接提出：

```text
使用 $skill-installer 从 Zwt-hello/agent-skills 安装以下 skills：
- skills/zwt-intent-clarifier
- skills/zwt-socratic-inquiry
- skills/zwt-first-principles
- skills/zwt-goal-path-review
- skills/zwt-layered-explainer
- skills/zwt-product-co-design
- skills/zwt-decision-steelman
- skills/zwt-development-baseline
- skills/zwt-capability-mapping
- skills/zwt-orchestrator
如果本地存在同名 skill，先停止，不要覆盖。
```

也可以单独提供某个 skill 的 GitHub 目录链接：

- [安装目录：意图洞察与强重述](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-intent-clarifier)
- [安装目录：苏格拉底式问题澄清](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-socratic-inquiry)
- [安装目录：第一性原理拆解与重构](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-first-principles)
- [安装目录：目标导向与路径审查](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-goal-path-review)
- [安装目录：双层讲解与理解检查](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-layered-explainer)
- [安装目录：产品共创与确认](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-product-co-design)
- [安装目录：双向钢人决策审查](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-decision-steelman)
- [安装目录：通用开发质量基线](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-development-baseline)
- [安装目录：Capability Mapping](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-capability-mapping)
- [安装目录：Orchestrator](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-orchestrator)

每个目录中的 `SKILL.md` 是技能正文，`agents/openai.yaml` 提供 Codex 的展示信息和调用策略。部分技能还包含 `references/` 参考资料，安装时应保留完整目录。适配其他 Agent 工具时，请按其技能格式与加载规则处理。

## 使用示例

### 意图洞察与强重述

```text
使用 $zwt-intent-clarifier，结合上下文理解我说的“让任务管理更轻松”真正想解决什么，完整重述问题并给出建议；只讨论，不实施。
```

适合希望先得到最佳理解和建议，再校正方向的讨论。

### 苏格拉底式问题澄清

```text
使用 $zwt-socratic-inquiry，我不确定团队效率低是流程问题还是工具问题。请逐题追问，帮我厘清真正想问的问题，确认后再给建议。
```

后续回答或确认时再次调用 `$zwt-socratic-inquiry`，沿用已有问诊阶段和累计问题数。最多六问，信息足够时提前收束。

### 第一性原理拆解与重构

```text
使用 $zwt-first-principles，分析我们是否需要自建知识库检索系统。区分基本事实、未验证假设、目标与约束，重新推导可行路径，明确成立前提和第一步验证；只讨论，不实施。
```

适合重新检查方案赖以成立的基本条件。推导结果可以保留、简化或重组原方案，不以推翻已有做法为目标，也不自动执行验证实验。

### 目标导向与路径审查

```text
使用 $zwt-goal-path-review，审查“每天手工导出多份报表，再用鼠标自动化合并”的方案。先明确目标与必须保留的约束，再判断应该保留、简化还是替换；只讨论，不实施。
```

适合目标已有一定清晰度、需要判断当前做法是否合适的场景。核实替代路径的权限、能力和成本，不因流程繁琐就认定应当替换。

### 双层讲解与理解检查

```text
使用 $zwt-layered-explainer，分小白版和专业版讲解数据库事务，用同一个例子说明机制与边界，最后整理术语对应、易错点和三个理解检查问题。
```

一次完成两层讲解与末尾整理，默认先不给检查题答案。用户作答后反馈具体理解与偏差；需要答案或解析时可以直接提出。

### 产品共创与确认

```text
使用 $zwt-product-co-design，根据当前产品上下文，帮我完善“让用户保存并继续未完成任务”的需求，形成完整功能、交互和验收方案供我确认，不要直接实施。
```

该 skill 的调用轮次只用于讨论与确认。方案满足需求后，在后续轮次明确授权实施。

### 双向钢人决策审查

```text
使用 $zwt-decision-steelman，审查我们是否应该先开放自助注册，再完善人工审核流程。先完整重述真正问题，再给出双向钢人论证、关键变量和行动判断。
```

如果技能提出关键问题，回答时再次调用 `$zwt-decision-steelman`，让它沿用已有框架继续审查。

产品共创与决策审查都配置为仅显式调用。产品共创用于补全并确认方案，决策审查用于判断方向与取舍；可以独立使用，也可以按需要先审查方向，再共创产品方案。

### 通用开发质量基线

```text
使用 $zwt-development-baseline，完成已授权的任务列表功能改动，按实际数据规模与失败风险补齐必要保障，清理本次替换后失去用途的旧实现，并验证关键行为。
```

该技能允许按开发任务隐式调用。根据具体场景选择必要保障，不将纯讨论或只读审查转为实施，也不默认增加复杂架构。

### Capability Mapping（能力映射）

```text
使用 $zwt-capability-mapping，检查当前项目的上传能力应由哪个现有模块或框架能力负责，选择受支持的实现接入点，按需处理兼容性，并在已授权范围内实现和验证。
```

该技能允许按任务上下文隐式调用，也可以显式调用。简单改动沿用既有模式；涉及框架能力、跨子系统职责或迁移时，按任务规模核实能力归属与实现方式。兼容性决策的补充规则见 [Compatibility and Breaking Evolution](skills/zwt-capability-mapping/references/compatibility.md)。

### Orchestrator（协作编排）

```text
使用 $zwt-orchestrator，协调这项已授权的开发任务：只拆分有实际收益的独立工作，明确文件归属和验收条件，合理选择可用工作模型，检查并集成结果。
```

需要宿主提供子 Agent 能力。技能不绑定固定模型代际；当前主模型负责整体结果，简单或紧密耦合的工作保留在主任务内。

## 目录结构

```text
skills/
├── zwt-intent-clarifier/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-socratic-inquiry/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-first-principles/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-goal-path-review/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-layered-explainer/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-product-co-design/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-decision-steelman/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-development-baseline/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-capability-mapping/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   └── references/compatibility.md
└── zwt-orchestrator/
    ├── SKILL.md
    └── agents/openai.yaml
```

新增技能时，在 `skills/` 下创建独立目录并更新本页列表。每个技能的具体约束以其 `SKILL.md` 为准。

## 许可证

[MIT](LICENSE) · Copyright (c) 2026 Zwt-hello
