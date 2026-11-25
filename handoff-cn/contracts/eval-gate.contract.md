# Contract · 评测门禁（FIXTURE）

| 项 | 定义 |
|---|---|
| 请求 | `{release_id, eval_set_version, metric_values, executed_by, executed_at}` |
| 响应 | `{decision: BLOCK|ALLOW, missing_items[], receipt_id}` |
| 必填指标 | 任务完成率、幻觉率、P95 延迟、单次任务成本；四项缺一即 BLOCK |
| 通过条件 | 四项均有值且均在已批准阈值内；未批准阈值时一律 BLOCK |
| 审计回执 | 记录评测集版本、四项指标、执行时间、执行人与决策 |
| 禁止行为 | 系统自动生成审批通过；以历史版本评测集替代当前冻结版本 |
| 不变量 | 无冻结评测集不得发布；BLOCK 不得被静默改为 ALLOW |

依据：岗位研究显示约六成 AI 产品经理岗位涉及指标、评估或实验；评估先行被纳入产品开发核心。[FOUND: https://www.pm.sh.cn/2026%E5%B9%B4%EF%BC%8Cai%E4%BA%A7%E5%93%81%E7%BB%8F%E7%90%86%E6%8B%9B%E8%81%98%E8%A6%80%E6%B1%82%E6%9C%89%E4%BD%95%E5%8F%98%E5%8C%96%EF%BC%9F/] [L5: pm.sh.cn, 2026-11 检索]

阈值批准人：[NEEDS-CONFIRMATION → 目标企业业务负责人: 阻断门禁阈值生效]
