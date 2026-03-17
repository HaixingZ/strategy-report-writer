# strategy-report-writer

`strategy-report-writer` 是一个用于撰写战略报告的 Codex skill。它采用分阶段、带闸门的工作方式，先锁定故事线，再确认模块，最后通过真实 subagent 分角色完成撰写与审阅。

## 适用场景

当你需要把一个宽泛的商业或战略选题，整理成结构清晰、论证稳定、风格可控的报告时，可以使用这个 skill。

常见场景包括：

- 在写正文之前先确认核心判断、叙事主线和章节结构
- 将一份报告拆成多个模块，分别由不同角色推进
- 在事实、推断和风格之间建立更清晰的边界
- 先完成模块审阅，再统一输出最终交付稿

## 核心流程

这个 skill 的默认流程如下：

- 先澄清任务边界：主题、受众、目的、时间范围、地理范围、研究对象、必写公司或产品、必用来源、输出形式、写作风格来源
- 先产出 `Storyline Packet`，只确认主论点、叙事路径和章节设计，不提前写完整正文
- 在故事线确认后，再产出 `Module Confirmation`，锁定模块划分与责任归属
- 每个模块由对应 subagent 专家完成判断、发现、证据缺口和模块草稿
- 由 Partner 进行模块审阅，只允许有限轮次返工
- 所有模块通过后，才输出 `Final Delivery`

## 对外产物

这个 skill 公开输出 4 类 Markdown 产物：

- `Storyline Packet`
- `Module Confirmation`
- `Partner Review`
- `Final Delivery`

其中，只有 `Final Delivery` 阶段才会附加 Nano Banana prompts。

## 目录说明

- `SKILL.md`：主工作流、闸门规则和约束
- `references/workflow.md`：流程顺序、回退规则和阶段切换条件
- `references/output-contracts.md`：4 类对外产物的固定格式
- `references/subagents.md`：Partner、模块 subagent 专家与审阅约束
- `references/style-system.md`：写作风格的选择、覆盖和合并规则
- `references/style-profile.md`：通用、较中性的后备写法
- `references/style-presets/analytical-operator.md`：默认写作风格预设
- `agents/openai.yaml`：界面元数据

## 安装

将目录复制到 `$CODEX_HOME/skills/strategy-report-writer` 即可。

示例：

```bash
cp -R strategy-report-writer "$CODEX_HOME/skills/"
```

## 风格机制

默认情况下，这个 skill 会使用 `references/style-presets/analytical-operator.md` 作为写作风格参考。

如果用户在当前对话中提供了样文、语气要求或明确格式要求，skill 会优先吸收这些指令，并在默认风格之上进行覆盖或合并。

如果默认预设不适合当前任务，也可以回退到 `references/style-profile.md`，使用更中性的战略报告表达方式。

## 使用约束

为保证流程稳定，这个 skill 会遵守以下约束：

- 不会在故事线确认前直接写完整报告
- 不会在模块确认前启动模块专家写作
- skill 被调用后会直接走真实 subagent 路径，不再二次征求是否使用 subagent；如果环境阻止创建 subagent，会中止并说明阻塞
- 无论使用哪种 preset 或 fallback，都不会使用“不是……而是……”及近似变体
- 首轮 `Partner Review` 不会直接接受初稿，必须提出至少一条具体修改意见
- 不会编造证据、数据或确定性结论
- 会尽量区分事实依据与推断判断
- 对外输出保持为轻量 Markdown，而不是额外的结构化工件

## 维护建议

如果你想调整默认风格，建议按下面的顺序更新：

1. 在 `references/style-presets/` 下新增或修改预设
2. 在 `references/style-system.md` 中更新默认风格规则
3. 保持 `SKILL.md` 聚焦在流程本身，不把具体文风细节写死在主说明里

## 更新记录

### 2026-03-17

- 将模块执行路径改为默认且必须使用真实 subagent
- 去除单 agent 顺序模拟 fallback，改为在 subagent 受限时中止并显式报阻塞
- 同步更新主 skill 文案、角色说明、工作流说明和界面元数据

### 2026-03-16

- 新增系统级写作禁令：全局禁止使用“不是……而是……”及近似变体，不因 preset 切换而失效
- 强化 `Partner Review` 流程：首次审核不得直接通过初稿，必须输出具体修改意见与 `Rewrite Brief`
- 同步更新风格系统、默认 preset、fallback profile、流程规则、角色定义与输出契约，保证上述约束在各层一致生效
- 完成一次结构校验与一次最小行为 smoke test，确认规则已经生效
