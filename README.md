# Agent Skills

ZWT 的个人 AI Agent 技能集合，用于产品共创、需求确认与决策审查。主要说明使用中文，每个 skill 独立维护。

## 技能列表

| Skill | 用途 | 显式调用 |
| --- | --- | --- |
| [产品共创与确认](skills/zwt-product-co-design/SKILL.md) | 补全和修正产品需求，形成完整功能、交互与验收方案，在实施前与用户确认。 | `$zwt-product-co-design` |
| [双向钢人决策审查](skills/zwt-decision-steelman/SKILL.md) | 完整重述真正问题，构建支持与反对的最强可信论证，识别关键变量并形成判断。 | `$zwt-decision-steelman` |

## 安装

在 Codex 中使用内置的 skill-installer，可以直接提出：

```text
使用 $skill-installer 从 Zwt-hello/agent-skills 安装以下 skills：
- skills/zwt-product-co-design
- skills/zwt-decision-steelman
如果本地存在同名 skill，先停止，不要覆盖。
```

也可以单独提供某个 skill 的 GitHub 目录链接：

- [安装目录：产品共创与确认](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-product-co-design)
- [安装目录：双向钢人决策审查](https://github.com/Zwt-hello/agent-skills/tree/main/skills/zwt-decision-steelman)

每个目录中的 `SKILL.md` 是技能正文，`agents/openai.yaml` 提供 Codex 的展示信息和显式调用设置。适配其他 Agent 工具时，请按其技能格式与加载规则处理。

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

两个技能都配置为显式调用。产品共创用于补全并确认方案，决策审查用于判断方向与取舍；可以独立使用，也可以按需要先审查方向，再共创产品方案。

## 目录结构

```text
skills/
├── zwt-product-co-design/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── zwt-decision-steelman/
    ├── SKILL.md
    └── agents/openai.yaml
```

新增技能时，在 `skills/` 下创建独立目录并更新本页列表。每个技能的具体约束以其 `SKILL.md` 为准。

## 许可证

[MIT](LICENSE) · Copyright (c) 2026 Zwt-hello
