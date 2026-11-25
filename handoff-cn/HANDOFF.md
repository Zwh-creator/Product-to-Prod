# HANDOFF · CN-AI-Ops Console v0.1（作品集案例）

本包是 **STANDALONE / FIXTURE：no downstream configured**。没有工程适配器，没有任何交接已经发生；接缝件用于暴露不变量与未决规则，不代表已交给研发。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/references/handoff-package.md] [L5: 上游 handoff-package.md, 2026-11-25 读取]

## 1 · 七部分任务记录

| 项 | 内容 |
|---|---|
| Requester | 案例发布负责人（角色标签；真实姓名待确认） |
| Desired outcome | 让 AI 产品运营团队在上线前能说清依据、上线后能只读复核结果 |
| Sources | `docs/cn/01-evidence-base.md`，15 行证据，4 行为转引 |
| Acceptance criteria | SC-01 至 SC-13，全部发布前预声明，结论留空 |
| Boundaries | 不做模型训练、不做部署、不做 CI/合并、不用真实用户数据 |
| Blocker rule | 一个阻断只问一个问题，在原会话线程问，不开平行线程 |
| Receipt | 本目录 + `docs/cn/`，见下方 done receipt |

## 2 · Done receipt

```text
changed: 新增国内 AI 产品运营/落地语境、15 行证据、PRD、RICE、GTM、验收模板与接缝件
output:  docs/cn/00–06 与 handoff-cn/
checked: 证据锚点、需求三元组、场景覆盖、双镜头分歧、闸门默认值
human:   Gate 1 上下文、Gate 2 规格、Gate 3 批准；以及 Q1–Q7 的裁决
```

## 3 · 假设与判断日志

| 判断 | 取值 | 依据 |
|---|---|---|
| 产品对象是控制台而非模型平台 | 控制台 | [INFERRED: E05 的回报落差指向运营层而非模型层] |
| 北极星用 VTC/W 而非调用量 | VTC/W | [INFERRED: 调用量通不过反向代理测试] |
| 合规需求进入本版本 P0 | 是 | [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] [L5: cac.gov.cn, 2025-03-14] |
| 决策形态默认 solo | solo | [NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断真实审批路径] |
| 平台表面列表未对接注册表 | unverified against a registry | [FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取] |

## 4 · 待确认复核队列

Q1–Q7 与 BQ1–BQ3 的完整内容见 `docs/cn/02-cn-ai-ops-prd.md` 与 `docs/cn/03-rice-backlog-cn.md`。每条都带确认角色、阻断对象与一个可关闭它的问题；`inference-confirmed.json` 记录作品集场景下的显式接受，真实运行必须逐条关闭。

## 5 · 已考虑且降级

- 自研模型：周期与资本不匹配，头部案例也是模型 + 流程组合。[INFERRED: E08/E09]
- 广告平台执行：GTM 动词禁止平台写入，需单独授权。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-gtm-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]
- 拟人化陪伴：适用另一套法规，本版本不碰。[FOUND: https://www.cac.gov.cn/2026-04/10/c_1777558395078289.htm] [L5: cac.gov.cn, 2026-04-10]
- 私有化部署：交付形态差异大，先做产品化。[NEEDS-CONFIRMATION → 目标企业架构负责人: 阻断 R-10 的路线图决策]

## 6 · 自评收尾

- 最强：证据账本与需求—场景—切片三元组，任何结论都能回查。
- 最弱：Reach/Impact/Effort 均为案例演示值，没有真实团队基线；[NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断优先级的可信度] 风险是排期看起来精确但不可用。
- 验证建议：先做一次 30 分钟基线访谈，只问场景分布、单任务成本、转人工率三项。
- 下一步：关闭 Q1 后重算 RICE，再决定 S1 是否仍由 R-01/02/03/04 组成。

## 7 · 引用地图与证据检查

| 编号 | 来源存在 | 备注 |
|---|---|---|
| E01–E04 | exists | 央视网 / 央广网，CNNIC 报告转述 |
| E05–E07 | exists | 澎湃同页转引，需回原文 |
| E08–E09 | exists | 新华网 / 光明网，企业公开披露 |
| E10–E12 | exists | 网信办原文与国标报道 |
| E13 | exists | 中国政府网 |
| E14–E15 | exists | 招聘 JD 与岗位研究转述 |
| 原始报告原文 | missing | 已登记 Q5，未补前不声称"据原报告" |

## 8 · 机器可执行成功度量

指标行 M1–M5 的工具、确切查询、窗口与评估日见 `docs/cn/02-cn-ai-ops-prd.md`「成功度量计划」。阈值列均为待确认或法规硬值，未确认前 `pm-verify-release-v1` 只能给 UNVERIFIED，不得把空数据集解释为 PASS。

## 接缝件状态

`spec.md`、`plan.md`、`data-model.md`、`contracts/`、`slices.json`、`case-contract.md`、`design-gate.json` 均为 FIXTURE，未连接下游工程系统。
