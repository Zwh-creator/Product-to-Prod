# spec.md · CN-AI-Ops Console v0.1（FIXTURE）

## 1. Scope

发布前评测门禁、生成内容标识、转人工与关键事项人工确认、Bad Case 回流、效果成本看板、场景模板与计费配置。[CONSTRUCTED: 由 PRD R-01 至 R-08 汇总]

## 2. Out of scope

模型训练与微调、生产部署、CI/合并、真实用户数据、广告平台执行、拟人化陪伴、私有化交付。[NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断 R-09/R-10 是否移入后续版本]

## 3. Users affected

AI 产品负责人、AI 产品运营/实施顾问、客服主管、企业数字化负责人、商业化负责人。[CONSTRUCTED: 由 E14/E15 的岗位画像综合构造]

## 4. Change in behaviour

从「先上线再补材料、凭调用量看效果」变为「无评测集不得发布、生成内容默认带标识、关键事项人工确认、按周看通过业务校验的任务数」。[INFERRED: 由 E05 的回报落差与 E10 的强制标识推导]

## 5. Data touched

任务事件、评测集与回执、场景与知识库版本、Bad Case 与回归用例、生成内容标识元数据、会话转人工事件、成本与延迟日志。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]

## 6. Interfaces touched

Web 控制台、评测执行器、合规门禁、指标看板、通知中心；列表未与任何表面注册表核对。[NEEDS-CONFIRMATION → 目标企业架构负责人: 阻断接口契约定稿]

## 7. Risks

- 合规口径随地方变化，材料清单可能不是单一版本。[NEEDS-CONFIRMATION → 目标企业合规负责人: 阻断合规闸门清单]
- 任务级埋点缺失会使 M1/M2 无法执行。[NEEDS-CONFIRMATION → 目标企业数据负责人: 阻断度量计划]
- 门禁可能被视为发版阻力而被绕过。[INFERRED: 由 E06 的高取消率与价值不清推导]

## 8. Rollout notes

按 `docs/cn/04-gtm-launch-plan-cn.md` 的 P0→P3 阶段推进；红闸门所在渠道不得放量；每次扩量重新取闸门快照。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-gtm-v1/SKILL.md] [L5: 上游 SKILL.md, 2026-11-25 读取]

## 9. Open items

Q1–Q7、BQ1–BQ3 见 PRD 与批次裁决；全部在 `inference-confirmed.json` 中显式接受为开放，真实运行需关闭。

## Acceptance scenarios

每条格式：`id · 分类 · 观察方式 · Trace`。

| ID | 场景与观察方式 | 分类 | Trace |
|---|---|---|---|
| R-01.1 | 未挂载评测集时点击发布，系统拒绝并列出缺失项；观察发布接口返回与页面提示 | risk RED / money no / analytics yes | R-01 → SC-01 → SL-01 |
| R-01.2 | 评测通过后生成回执，字段含数据集版本、四项指标、执行时间、执行人 | risk RED / money no / analytics yes | R-01 → SC-02 → SL-01 |
| R-02.1 | 生成文本或图片，输出带显式标识且元数据含隐式标识 | risk RED / money no / analytics yes | R-02 → SC-03 → SL-02 |
| R-02.2 | 用户申请无显式标识内容，仅在协议确认后提供且留存对象日志不少于六个月 | risk RED / money no / analytics yes | R-02 → SC-04 → SL-02 |
| R-03.1 | 用户明确要求转人工或命中资金争议，人工入口首屏可见、触发后转接且会话记录完整传递 | risk RED / money yes / analytics yes | R-03 → SC-05 → SL-02 |
| R-03.2 | 价格/退款/赔偿类答复必须经人工最终确认后才发出 | risk RED / money yes / analytics yes | R-03 → SC-06 → SL-02 |
| R-04.1 | 用户标记 Bad Case 后自动生成回归用例进入待评测队列，线上提示词不被直接修改 | risk AMBER / money no / analytics yes | R-04 → SC-07 → SL-03 |
| R-05.1 | 看板按周展示 VTC/W 并可下钻到场景与任务 ID，成功判定规则可见 | risk AMBER / money yes / analytics yes | R-05 → SC-08 → SL-04 |
| R-05.2 | 单次成本或 P95 延迟越界时触发护栏告警并阻止自动扩量 | risk AMBER / money yes / analytics yes | R-05 → SC-09 → SL-04 |
| R-06.1 | 用模板新建场景，知识库与评测集绑定成功；失败时提示具体缺失项 | risk GREEN / money yes / analytics no | R-06 → SC-10 → SL-05 |
| R-07.1 | 切换计费方式后按同一批任务试算，差异可解释 | risk AMBER / money yes / analytics yes | R-07 → SC-11 → SL-06 |
| R-08.1 | 主模型调用失败时降级到备用模型并在回执标记原因 | risk AMBER / money no / analytics yes | R-08 → SC-12 → SL-06 |
| R-02.3 | 未备案生成式服务尝试上线，系统阻塞并提示备案材料清单 | risk RED / money no / analytics yes | R-02 → SC-13 → SL-02 |

测试标识、提交引用与保真记录由构建方填写，本包不预置。[FOUND: https://github.com/naderelewa/Product-to-Prod/blob/main/skills/pm-requirements-v1/references/handoff-package.md] [L5: 上游 handoff-package.md, 2026-11-25 读取]
