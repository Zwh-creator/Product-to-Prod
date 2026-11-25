# case-contract.md · 锁定常量、不变量、终止条件

## 锁定常量

| 常量 | 值 |
|---|---|
| product | CN-AI-Ops Console |
| release | v0.1 内测版 |
| period / geography | 2026-12 / 中国大陆 |
| north-star | 每周通过业务校验的 AI 任务数（VTC/W） |
| leading metric | 首周任务完成率 |
| decision shape | solo（案例默认，真实运行待确认） |
| pack | none + cn-ai-ops 语境说明 |
| approval | `approved: false`，仅人可翻转 |

## 不变量

1. 无冻结评测集不得发布；
2. 生成内容默认带显式与隐式标识，去标识需协议确认与六个月日志；
3. 未备案生成式服务阻塞上线；
4. 资金、退款、赔偿等关键事项由人工最终确认；
5. Bad Case 不直接改线上提示词；
6. 原始调用量不得替代 VTC/W 成为北极星指标。

## 终止条件（什么结果应当停下）

- 任一合规闸门为 RED 却要求放量；[FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] [L5: cac.gov.cn, 2025-03-14]
- 任务级埋点缺失却要求给出 M1/M2 数值；[NEEDS-CONFIRMATION → 目标企业数据负责人: 阻断度量结论]
- 门禁被绕过且无法给出回执；
- 超过半数内测团队绕过门禁而 VTC/W 未下降，则战略赌注 S1 被证伪。[NEEDS-CONFIRMATION → 案例发布负责人: 阻断赌注判定口径]

## 模式

STANDALONE / FIXTURE：无下游工程系统连接，接缝件未被任何工具消费；不得声称已完成交接。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/references/handoff-package.md] [L5: 上游 handoff-package.md, 2026-11-25 读取]

## 完整性封印

封印值在最后内容编辑后写入 `design-gate.json`，并在本文件同步；生成方式见 `docs/cn/07-validating-notes.md`。本包 `approved: false`，因此封印只做一次，不重复封印已批准包。
