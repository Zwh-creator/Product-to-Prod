# 05 · 发布验收与度量计划：验收报告 v1 模板

返回：[GTM](04-gtm-launch-plan-cn.md) · [PRD](02-cn-ai-ops-prd.md)

**性质**：这是验收**准备**，不是验收结论。上游动词的硬边界：只读；对**已部署版本**而非仓库验收；不写任何闸门、不替业主接受；UNVERIFIED 是一等结论。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-verify-release-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]

## 1 · 运行坐标（未填，不允许凭空补全）

| 项 | 值 |
|---|---|
| spec 目录 | `handoff-cn/` |
| tier | [NEEDS-CONFIRMATION → 案例发布负责人: 阻断验收运行的 tier 选择] |
| build 标识 | [NEEDS-CONFIRMATION → 目标企业研发负责人: 阻断验收报告的构建戳] |
| 部署 URL / 坐标 | [NEEDS-CONFIRMATION → 目标企业平台负责人: 阻断行为探测] |
| 运行记录 | [NEEDS-CONFIRMATION → 目标企业研发负责人: 阻断 Trace 关联] |

**注意力头**：`held: weak source`。当前没有已部署版本，本报告**停在 failed check 之前**，不产出任何 PASS。

## 2 · 场景判定表（预声明，结论留空）

判定只允许 PASS / PARTIAL / GAP / UNVERIFIED；GAP 必须带原因类 `build-gap · flag-gap · data-gap · spec-gap`。

| 场景 ID | 界面 | 风险 / 钱路径 / 埋点 | 判定 | 证据锚点 | 原因类 |
|---|---|---|---|---|---|
| SC-01 | 发布门禁 | RED / no / yes | 待运行 | PRD §验收场景 | — |
| SC-02 | 发布回执 | RED / no / yes | 待运行 | PRD §验收场景 | — |
| SC-03 | 生成内容标识 | RED / no / yes | 待运行 | [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] | — |
| SC-04 | 无显式标识申请 | RED / no / yes | 待运行 | [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] | — |
| SC-05 | 转人工 | RED / yes / yes | 待运行 | [FOUND: https://www.china.com.cn/txt/2026-09/11/content_118690907.shtml] | — |
| SC-06 | 关键事项人工确认 | RED / yes / yes | 待运行 | [FOUND: https://www.china.com.cn/txt/2026-09/11/content_118690907.shtml] | — |
| SC-07 | Bad Case 回流 | AMBER / no / yes | 待运行 | PRD §验收场景 | — |
| SC-08 | 看板下钻 | AMBER / yes / yes | 待运行 | PRD §验收场景 | — |
| SC-09 | 成本/延迟护栏 | AMBER / yes / yes | 待运行 | [NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断阈值定稿与判定] | — |
| SC-10 | 模板新建场景 | GREEN / yes / no | 待运行 | [NEEDS-CONFIRMATION → 目标企业实施负责人: 阻断 10 分钟目标的可行性] | — |
| SC-11 | 计费试算 | AMBER / yes / yes | 待运行 | PRD §验收场景 | — |
| SC-12 | 多模型降级 | AMBER / no / yes | 待运行 | PRD §验收场景 | — |
| SC-13 | 未备案服务上线 | RED / no / yes | 待运行 | [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] | — |

**证据强度提醒**：行为探测结果高于「 inspected 」高于「 intent 」。仓库状态、绿色 CI 都不能替代对已部署版本的探测。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-verify-release-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]

## 3 · 度量计划执行回执（模板，未执行）

每条回执必须写清工具、确切查询、窗口、以及相对阈值的结果；未声明的查询只能算 INFERRED，不算验收依据。

| ID | 工具 | 确切查询 | 窗口 | 阈值 | 结果 |
|---|---|---|---|---|---|
| M1 | 事件仓（环境名待确认） | `SELECT date_trunc('week', completed_at) AS wk, count(DISTINCT task_id) FROM ai_ops.task_events WHERE validated = true AND rework = false AND completed_at >= '2026-12-07' GROUP BY 1` | 2026-12-07 至 2026-12-28 | [NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断 M1 阈值] | 未执行 |
| M2 | 事件仓（环境名待确认） | `SELECT count(*) FILTER (WHERE rework = false)::float / count(*) FROM ai_ops.task_events WHERE triggered_at >= '2026-12-07'` | 同 M1 | [NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断 M2 阈值] | 未执行 |
| M3 | 元数据扫描 | 扫描本周全部导出文件，统计显式+隐式标识齐备比例 | 发布后首周每日 | 100% [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] | 未执行 |
| M4 | 会话事件表 | 命中转人工条件且 30 秒内进入人工队列的比例 | 发布后首周 | [NEEDS-CONFIRMATION → 目标企业客服负责人: 阻断 M4 阈值] | 未执行 |
| M5 | 网关日志 | 按场景分组的 `cost/task` 与 `p95(latency)` | 发布后首周 | [NEEDS-CONFIRMATION → 目标企业平台负责人: 阻断 M5 阈值] | 未执行 |

**默认环境陷阱**：查询不点名项目/属性时会命中默认环境，数字看起来完全合理但属于错数。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-verify-release-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取] 因此 M1/M2 在 Q4 关闭前一律 UNVERIFIED，不用空数据集解释成 PASS。

## 4 · 阻断项与解除条件

| 阻断项 | 责任人 | 解除条件 | 状态 |
|---|---|---|---|
| 无已部署构建 | [NEEDS-CONFIRMATION → 目标企业平台负责人: 阻断行为探测] | 提供 tier、build 与可访问坐标 | 未解除 |
| 无任务级埋点 | [NEEDS-CONFIRMATION → 目标企业数据负责人: 阻断 M1/M2] | 字段字典 + 一条测试事件 | 未解除 |
| 标识方案未确认 | [NEEDS-CONFIRMATION → 目标企业合规负责人: 阻断 SC-03/SC-04] | 方案说明 + 样例输出文件 | 未解除 |
| 转人工能力未确认 | [NEEDS-CONFIRMATION → 目标企业客服负责人: 阻断 SC-05/SC-06] | 会话回放一次 | 未解除 |

## 5 · 反馈包骨架（下一轮需求循环的第一份阅读材料）

- **标签迁移**：本轮尚无新 FOUND；禁止把「计划中」写成 `INFERRED → FOUND`。
- **PARTIAL / GAP 登记**：待真实运行后按 `build-gap / flag-gap / data-gap / spec-gap` 分类；候选进入 `/pm-portfolio-v1`，不自动插入任何 backlog。
- **Gotchas**：默认环境、空生产数据集、staging 外推生产，三条均来自上游已警告的坑。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-verify-release-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]
- **闸门健康**：接受未修改 / 接受并修改 / 拒绝，由业主记录，不由执行者记录。

## 6 · 业主验收栏（必须留空，由业主填写）

```text
判定：________________________________
ACCEPT / ACCEPT-WITH-EDITS / REJECT
理由或命名修改：________________________
裁决人：________________  日期：____________
```

执行者不填这一栏；任何替业主写「通过」的行为都是这套方法明确禁止的。
