# 03 · 批次裁决：双镜头 RICE 与冲刺建议

返回：[PRD](02-cn-ai-ops-prd.md) · [GTM](04-gtm-launch-plan-cn.md) · [证据账本](01-evidence-base.md)

**前置条件**：北极星指标 VTC/W 与领先指标「首周任务完成率」已在 PRD 中锁定；未锁定则不打分。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-portfolio-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]

**批次来源**：PRD 的 R-01 至 R-10，以及评审中追加的两个候选。每条请求保留原始意图 gist，并重新分配稳定 ID `REQ-CN-nn`，不复用需求编号。

## 1. 请求表与双镜头打分

RICE = (Reach × Impact × Confidence) ÷ Effort；Reach 为 0–10 的周度受影响场景份额，Impact 取 0.25/0.5/1/2/3，Effort 以人周计，Confidence 按证据强度映射：FOUND 1.0、INFERRED/CALCULATED 0.8、CONSTRUCTED/HYPOTHESIS 0.5、任一维度存在开放待确认项则上限 0.2。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/references/evidence-tags.md] [L5: 上游 evidence-tags.md, 2026-11-25 读取]

<!-- tag-lint:allow-multi start -->

| ID | 原始诉求 gist | 类型 | 产品镜头 | 战略镜头 | R / I / C / E | RICE | 分档 |
|---|---|---|---|---|---|---|---|
| REQ-CN-01 | "发布前必须有评测门禁，不然效果说不清" | feature | 减少上线返工，保护 VTC/W | 把评估变成产品能力，对应 Eval-First | 9 [INFERRED: 岗位研究称约六成涉及评估] / 3 [INFERRED: 直接约束 NSM] / 0.8 / 3 | 7.20 | P0 |
| REQ-CN-02 | "生成内容要能自动标识，合规不能事后补" | feature | 上线不被合规卡住 | 国内落地的准入条件，不是加分项 | 8 [INFERRED: 覆盖全部生成类场景] / 3 [FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] / 0.8 / 3 | 6.40 | P0 |
| REQ-CN-03 | "用户要转人工时别拦着，钱的事必须人工确认" | feature | 直接降低投诉与信任损失 | 与国标要求一致，影响品牌与续约 | 9 [FOUND: https://www.china.com.cn/txt/2026-09/11/content_118690907.shtml] / 2 [INFERRED: 主要作用于护栏指标] / 0.8 / 2 | 7.20 | P0 |
| REQ-CN-04 | "Bad Case 要能回流成回归用例" | feature | 形成数据闭环，减少重复缺陷 | 让模型迭代可审计 | 7 [INFERRED: JD 明确要求反馈回流] / 2 [INFERRED: 间接提升完成率] / 0.8 / 3 | 3.73 | P1 |
| REQ-CN-05 | "按周看到效果、成本、延迟" | feature | 让运营有可行动的指标 | 把 AI 从成本项变成经营项 | 6 [INFERRED: 办公场景使用翻倍] / 2 [INFERRED: 支撑决策但不直接产出任务] / 0.8 / 3 | 3.20 | P1 |
| REQ-CN-06 | "场景模板要能快速接入" | feature | 实施效率明显 | 同质化能力，难以形成差异化 | 8 [CONSTRUCTED: 由场景集中结论推导] / 1 [INFERRED: 间接作用] / 0.5 / 4 | 1.00 | P2 |
| REQ-CN-07 | "计费方式要能按调用量和按任务量切换" | feature | 商业化必备 | 与"按价值收费"方向一致但未验证 | 4 [CONSTRUCTED: 由 JD 商业化要求推导] / 2 [INFERRED: 影响收入但覆盖面窄] / 0.5 / 4 | 1.00 | P2 |
| REQ-CN-08 | "多模型路由失败要能降级" | feature | 稳定性提升 | 平台型能力，非本轮重点 | 5 [CONSTRUCTED: 由规模化运行要求推导] / 1 [INFERRED: 减少中断] / 0.5 / 4 | 0.62 | P3 |
| REQ-CN-09 | "要不要做拟人化陪伴场景" | epic | 产品镜头低：与控制台主线弱相关 | 战略镜头高：新市场，法规适用不同 | 3 [CONSTRUCTED: 由 E11 的适用范围推导] / 1 [INFERRED: 潜在新场景] / 0.2 / 5 | 0.12 | P3 + STRATEGIC-BET |
| REQ-CN-10 | "客户要求私有化部署" | feature | 产品镜头中：交付形态差异大 | 战略镜头低：拖慢产品化节奏 | 4 [CONSTRUCTED: 由金融场景数据不出域推导] / 1 [INFERRED: 单客户价值高] / 0.5 / 5 | 0.40 | P3 |

<!-- tag-lint:allow-multi end -->

**镜头分歧必须暴露，不取平均**：

- REQ-CN-09：产品镜头 P3，战略镜头高。按规则标 `STRATEGIC-BET`，交业主裁决，不用平均分掩盖。[INFERRED: 两个镜头分别指向「与主线弱相关」与「新市场」，是决策而非算术]
- REQ-CN-06：产品镜头认为实施效率有价值，战略镜头认为模板容易被复制；仍保留在 P2，不因为「大家都做」而升档。[INFERRED: 由 E07 的场景集中与 E15 的差异化要求共同推导]
- REQ-CN-03：RICE 已到 P0，但即使分数下降也不应降级——合规与关键事项人工确认属于硬约束，不能被分数软化。[FOUND: https://www.china.com.cn/txt/2026-09/11/content_118690907.shtml] [L5: china.com.cn, 2026-09-11]

## 2. 数值复核

| ID | 算式 | 结果 |
|---|---|---|
| REQ-CN-01 | 9 × 3 × 0.8 ÷ 3 | [CALCULATED: 21.6 ÷ 3 = 7.20] |
| REQ-CN-02 | 8 × 3 × 0.8 ÷ 3 | [CALCULATED: 19.2 ÷ 3 = 6.40] |
| REQ-CN-03 | 9 × 2 × 0.8 ÷ 2 | [CALCULATED: 14.4 ÷ 2 = 7.20] |
| REQ-CN-04 | 7 × 2 × 0.8 ÷ 3 | [CALCULATED: 11.2 ÷ 3 ≈ 3.73] |
| REQ-CN-05 | 6 × 2 × 0.8 ÷ 3 | [CALCULATED: 9.6 ÷ 3 = 3.20] |
| REQ-CN-06 | 8 × 1 × 0.5 ÷ 4 | [CALCULATED: 4 ÷ 4 = 1.00] |
| REQ-CN-07 | 4 × 2 × 0.5 ÷ 4 | [CALCULATED: 4 ÷ 4 = 1.00] |
| REQ-CN-08 | 5 × 1 × 0.5 ÷ 4 | [CALCULATED: 2.5 ÷ 4 = 0.625 ≈ 0.62] |
| REQ-CN-09 | 3 × 1 × 0.2 ÷ 5 | [CALCULATED: 0.6 ÷ 5 = 0.12] |
| REQ-CN-10 | 4 × 1 × 0.5 ÷ 5 | [CALCULATED: 2 ÷ 5 = 0.40] |

## 3. 冲刺建议

**主推荐：两周冲刺 S1 只做 REQ-CN-01、02、03、04**，即「评测门禁 + 合规标识 + 转人工 + 反馈回流」。

- 为什么不是「先做模板快速铺场景」：E05 显示规模化应用已经不稀缺，稀缺的是显著回报；先铺场景会放大没有门禁的产出。[INFERRED: 由 46%/9% 落差推导]
- 为什么不是「先做计费」：本轮没有真实定价与成本基线，Q1 未关闭；在缺基线时定价属于把待确认项包装成数字。[NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断计费方案的正式评审]
- 主推荐的下一步：把四条 P0 需求送进 `pm-requirements-v1` 的 P4 交接包，并按 SC-01 至 SC-07 预声明验收场景。

**版本说明**：本批次只产生裁决文档与机器可读摘要，不产出工作表——所选 pack 未声明 workbook form， inventing 一套列序比交付一张可自行改造的表更糟。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/docs/outputs.md] [L5: 上游 outputs.md, 2026-11-25 读取]

## 4. 批次级待确认项

| ID | 事项 | 确认人 | 阻断 |
|---|---|---|---|
| BQ1 | Reach 与 Impact 的真实取值（当前为案例演示值） | [NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断 RICE 用于真实排期] | 优先级可信度 |
| BQ2 | Effort 的人周估算是否按目标团队产能校准 | [NEEDS-CONFIRMATION → 目标企业研发负责人: 阻断交付承诺] | 冲刺容量 |
| BQ3 | 合规闸门在地方网信办口径下是否有附加材料 | [NEEDS-CONFIRMATION → 目标企业合规负责人: 阻断 REQ-CN-02 的完成定义] | P0 需求验收 |
