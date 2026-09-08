# Agent Skills

ZWT 的个人 AI Agent 技能集合，用于产品共创、需求确认、决策审查与技术能力映射。仓库说明使用中文，技能正文保留各自原始语言，每个 skill 独立维护。

## 技能列表

| Skill | 用途 | 显式调用 |
| --- | --- | --- |
| [产品共创与确认](skills/zwt-product-co-design/SKILL.md) | 补全和修正产品需求，形成完整功能、交互与验收方案，在实施前与用户确认。 | `$zwt-product-co-design` |
| [双向钢人决策审查](skills/zwt-decision-steelman/SKILL.md) | 完整重述真正问题，构建支持与反对的最强可信论证，识别关键变量并形成判断。 | `$zwt-decision-steelman` |
| [Capability Mapping（能力映射）](skills/zwt-capability-mapping/SKILL.md) | 为框架集成、跨子系统改动与迁移选择权威能力归属和受支持的实现接入点，按需处理兼容性。 | `$zwt-capability-mapping` |

## 安装

在 Codex 中使用内置的 skill-installer，可以直接提出：

```text
使用 $skill-installer 从 Zwt-hello/agent-skills 安装以下 skills：
- skills/zwt-product-co-design
- skills/zwt-decision-steelman
- skills/zwt-capability-mapping
如果本地存在同名 skill，先停止，不要覆盖。
```

也可以单独提供某个 skill 的 GitHub 目录链接：

- [安装目录：产品共创与确认](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-product-co-design)
- [安装目录：双向钢人决策审查](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-decision-steelman)
- [安装目录：Capability Mapping](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-capability-mapping)

每个目录中的 `SKILL.md` 是技能正文，`agents/openai.yaml` 提供 Codex 的展示信息和调用策略。部分技能还包含 `references/` 参考资料，安装时应保留完整目录。适配其他 Agent 工具时，请按其技能格式与加载规则处理。

## 使用示例

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

### Capability Mapping（能力映射）

```text
使用 $zwt-capability-mapping，检查当前项目的上传能力应由哪个现有模块或框架能力负责，选择受支持的实现接入点，按需处理兼容性，并在已授权范围内实现和验证。
```

该技能允许按任务上下文隐式调用，也可以显式调用。简单改动沿用既有模式；涉及框架能力、跨子系统职责或迁移时，按任务规模核实能力归属与实现方式。兼容性决策的补充规则见 [Compatibility and Breaking Evolution](skills/zwt-capability-mapping/references/compatibility.md)。

## 目录结构

```text
skills/
├── zwt-product-co-design/
│   ├── SKILL.md
│   └── agents/openai.yaml
├── zwt-decision-steelman/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── zwt-capability-mapping/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/compatibility.md
```

新增技能时，在 `skills/` 下创建独立目录并更新本页列表。每个技能的具体约束以其 `SKILL.md` 为准。

## 许可证

[MIT](LICENSE) · Copyright (c) 2026 Zwt-hello
