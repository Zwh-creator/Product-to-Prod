# 06 · 求职作品集差异化改造方案与分步落地清单

返回：[总览](00-adaptation-overview.md) · [PRD](02-cn-ai-ops-prd.md) · [GTM](04-gtm-launch-plan-cn.md)

适用岗位：AI 产品经理、AI 产品运营、AI 解决方案/实施顾问。目标不是「展示我会写 PRD」，而是「展示我能把概率型 AI 能力变成可评估、可运营、可交接、可复核的国内落地方案」。国内 JD 已经把 BRD/PRD、指标体系、离线评测与线上监控、准确率/任务完成率、Prompt/RAG/Agent、SQL 与 A/B 测试写进职责。[FOUND: https://www.zhaopin.com/jobdetail/CC564580720J41015991504.htm] [L5: zhaopin.com, 2026-11 检索]

## 1. 三分钟评审叙事（决定作品集是否被翻开）

| 屏 | 展示 | 一句话 | 让评审点开的钩子 |
|---|---|---|---|
| 1 | `00-adaptation-overview.md` 的对比表 | "我没有换流程，只换了语境与证据" | 上游方法骨架完全保留，避免被质疑"自造方法论" |
| 2 | `01-evidence-base.md` 的证据账本 | "15 行证据，连转引和缺口都写在同一页" | 展示 37pp 落差、法规原文、美的折算值 |
| 3 | `02` + `03` + `05` 的关键片段 | "需求 → 优先级 → 发布验收，三元组可追" | 展示 R-01 → SC-01 → SL-01 的追踪链 |

**不要在首页放**：大段 PRD 正文、没有来源的收益数字、"我主导了某大厂项目"式表述。作品集的可信度来自可点开的锚点，不来自形容词。

## 2. 改造前后对比（面试时直接念这一张）

| 维度 | Fork 前的上游仓库 | 改造后 | 评审能验证什么 |
|---|---|---|---|
| 定位 | Agent 产品经理方法与插件 | 国内 AI 产品运营/落地案例包 | 你把通用方法落到具体市场 |
| 问题定义 | 由运行者自带策略陈述 | 用 46% vs 9% 定义"落地落差"问题 | 会抽象问题，不是堆功能 |
| 证据 | 六标签 + L 轴，来源由用户提供 | 15 行国内来源，转引与缺口显式登记 | 不编数字、不怕被查 |
| 合规 | 通用不可支持主张清单 | 标识、备案、转人工、人工确认成为需求与验收项 | 熟悉国内落地硬约束 |
| 指标 | 由运行者每轮 elicitation | VTC/W + 首周完成率 + 五项护栏，含反代理测试 | 会定义指标而非堆埋点 |
| 优先级 | 双镜头 RICE 方法 | 10 条带标签请求，分档 + 战略赌注不取平均 | 会做取舍并解释分歧 |
| 发布 | GTM 计划 + 验收动词 | 闸门快照、配置提案、预声明验收、留空验收栏 | 懂发布全流程与权责边界 |
| 交付 | 方法文档与脚本 | 额外产出可评审 handoff 包（闸门默认 false） | 懂工程交接与不自批闸门 |
| 诚实度 | 自陈弱点写在 README | 案例性质声明 + 未运行说明 + 待确认清单 | 有职业成熟度 |

## 3. 五个差异化点的面试说法

1. **证据纪律**：「我没有写'提升 80%'，我把它的出处、口径和局限写在同一行；转引的我就写转引。」锚点：`01-evidence-base.md` E05/E08。
2. **问题定义**：「46% 在规模化、9% 有显著回报，差 37 个百分点——所以我把产品重心放在运营与度量，而不是再接一个模型。」锚点：`01` D1 + `02` 战略赌注 S1。
3. **合规前置**：「生成内容标识 2025 年 9 月已强制，转人工与关键事项人工确认有国标要求；我把它们写成 P0 需求和验收场景，而不是上线前补材料。」锚点：E10/E12 + R-02/R-03。
4. **Eval-First**：「发布前必须挂评测集，Bad Case 自动变成回归用例；看板按周算通过业务校验的任务数，不算原始调用量。」锚点：R-01/R-04 + PRD 反代理测试。
5. **权责边界**：「我写的验收报告不替业主接受，闸门永远默认 false；GTM 只写配置提案，不碰平台。」锚点：`05` 第 6 节 + `handoff-cn/design-gate.json`。

## 4. 分步落地清单（按依赖顺序，不按版本号堆任务）

| 步 | 动作 | 产出 | 完成判据 | 闸门 |
|---|---|---|---|---|
| D0 | 手动 fork 上游仓库，并用一次性 PAT 推送改造分支 | `Zwh-creator/Product-to-Prod` + PR #1 | fork 可访问、PR 可合并 | 已完成，见第 6 节 [FOUND: https://github.com/Zwh-creator/Product-to-Prod/pull/1] [L5: GitHub PR 页面, 2026-11-25] |
| D1 | 把 `README.cn-adaptation.md` 合并到 fork README 顶部，保留 MIT 与 provenance | 可点开的仓库首页 | 上游 badge 与许可证未被删除 | 无 |
| D2 | 提交 `docs/cn/00`、`01`，核对每条 FOUND 的链接可打开 | 差异总览 + 证据账本 | 15 行证据全部有 URL 与日期；4 行转引被显式标注 | 自检 |
| D3 | 提交 `02`，请一位真实产品/运营人复核开放问题是否问对人 | PRD + 开放问题队列 | Q1–Q7 每条有确认角色与阻断对象 | Gate 1（人） |
| D4 | 提交 `03`，按真实团队产能重估 Effort 与 Reach | 批次裁决 + 冲刺建议 | 双镜头分歧未被平均；STRATEGIC-BET 单列 | Gate（业主） |
| D5 | 提交 `04`、`05`，把红闸门逐条转成责任人 | GTM 计划 + 验收模板 | 每条闸门有确认人；验收栏为空 | Gate 2 / 3（人） |
| D6 | 提交 `handoff-cn/`，运行上游标签 lint 与自测脚本 | 交接包 + 自检记录 | lint 0 违规；`approved: false` 未被改写 | Gate 3（人） |
| D7 | 输出一页作品集封面 + 三段讲述脚本，投 3 个岗位版本 | 作品集页 + 面试问答 | 每个版本都能在 3 分钟内讲到 D2–D5 的证据 | 投递前复查 |

**每步的失败处理**：验不过就停在当步并把失败原因写成一行记录，不靠改小检查范围换取"通过"。这与上游「A check that cannot run must fail」一致。[FOUND: https://github.com/naderelewa/Product-to-Prod#contributing] [L5: 上游 README, 2026-11-25 读取]

## 5. 面试高频问答准备

| 问题 | 回答骨架（不要背结论，讲证据链） |
|---|---|
| "这个 PRD 里哪个数字是真的？" | 区分三类：外部转引（E05，有链接但需回原文）、官方原文（E10 标识办法）、案例候选值（M1 阈值，待确认）。 |
| "你为什么把合规做成 P0？" | 标识自 2025-09-01 强制；转人工与关键事项确认有国标要求；它们是准入条件，不是收益优化。[FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] |
| "RICE 为什么这个分数？" | 展示算式与每个输入的证据标签，并说明 Reach/Impact 是案例演示值，真实排期需关闭 BQ1。 |
| "上线后效果不好你怎么处理？" | 回到预声明场景：先判 PASS/PARTIAL/GAP/UNVERIFIED，再按原因类路由到 spec 或 backlog；不临时改 rubric。 |
| "这和直接用 AI 写 PRD 有什么区别？" | plain chat 没有 lint、没有闸门、没有交接契约；这里每条主张可复查、审批权在人。[FOUND: https://github.com/naderelewa/Product-to-Prod#honest-comparison] |

## 6. 发布状态与复核入口

- Fork 已建立：`Zwh-creator/Product-to-Prod`，默认分支 `main` 可访问。[FOUND: https://github.com/Zwh-creator/Product-to-Prod] [L5: GitHub 仓库页面, 2026-11-25 读取]
- 改造分支：`cn-ai-ops-adaptation-pr`，从 `main` 派生，包含 23 个新增文件与 1 个提交。[FOUND: https://github.com/Zwh-creator/Product-to-Prod/tree/cn-ai-ops-adaptation-pr] [L5: GitHub 分支页面, 2026-11-25 读取]
- PR #1 已开启，状态 open、可合并（mergeable: true）。[FOUND: https://github.com/Zwh-creator/Product-to-Prod/pull/1] [L5: GitHub PR 页面, 2026-11-25 读取]
- 交接包 8 个文件的 sha256 封印从 Git blob 复核 8/8 一致，`approved: false` 未被改写。[FOUND: https://github.com/Zwh-creator/Product-to-Prod/blob/cn-ai-ops-adaptation-pr/handoff-cn/design-gate.json] [L5: GitHub 文件内容, 2026-11-25 读取]
- 一次性 PAT 已用于推送；账号所有者应在 GitHub 撤销该 token。[NEEDS-CONFIRMATION → 账号所有者: 撤销推送用 PAT，不影响已推送内容]

复核命令（在 fork 根目录、该分支下）：

```bash
bash scripts/tag-lint.sh docs/cn/*.md handoff-cn/*.md
bash tests/run-tests.sh
```

本案例选择个人 fork 内的 PR，便于保留案例专属文档与自定义 README；若要向上游贡献，需要另外开一个针对上游仓库的 PR。

## 7. 完成定义（Definition of Done）

- 仓库首页 3 分钟内能看懂「改了什么、为什么改」；
- 15 行证据全部可点开，转引与缺口未被抹平；
- PRD 的需求三元组完整，验收场景含失败路径；
- RICE 的每条分数有算式，两个镜头的分歧没有被平均；
- GTM 所有行是 `CONFIG-PLANNED`，没有虚构支出或投放结果；
- 验收报告的业主栏为空，闸门 `approved: false`；
- 标签 lint 0 违规；
- 有一句诚实的局限说明：这是文档化案例，不是已上线产品。
