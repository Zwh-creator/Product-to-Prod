# data-model.md · 实体、字段、状态、约束（FIXTURE）

| 实体 | 关键字段 | 状态 | 约束 |
|---|---|---|---|
| `Scenario` | scenario_id, name, owner_role, persona_track | DRAFT → ACTIVE → PAUSED | 未通过评测门禁不得为 ACTIVE |
| `EvalSet` | eval_set_id, version, metric_names, frozen_at | DRAFT → FROZEN → ARCHIVED | 发布回执必须引用 FROZEN 版本 |
| `EvalRun` | run_id, eval_set_id, metrics, executed_by, executed_at | RUNNING → PASS → FAIL | 四项指标缺一不可 |
| `ReleaseReceipt` | receipt_id, run_id, build_stamp, approver_role | PREPARED → APPROVED → REJECTED | 审批由人填写，系统不得自动置 APPROVED |
| `GeneratedAsset` | asset_id, explicit_mark, implicit_mark, file_meta | MARKED → UNMARKED-BY-REQUEST | 无显式标识必须存在协议确认与日志 |
| `HandoffLog` | log_id, task_id, condition, entered_queue_at | PENDING → ROUTED → CLOSED | 资金/退款/赔偿必须人工最终确认 |
| `TaskEvent` | task_id, scenario_id, validated, rework, cost, latency_p95 | TRIGGERED → COMPLETED → REWORKED | 成功判定必须同时满足 validated 且非 rework |
| `BadCase` | case_id, task_id, labelled_at, regression_case_id | OPEN → REGRESSION → CLOSED | 不得直接改线上提示词 |
| `ComplianceCheck` | check_id, scope, filing_ref, mark_method | UNPROBED → RED → GREEN | 备案引用缺失时为 RED |

**标识约束**来自强制法规：显式标识与文件元数据隐式标识，请求去标识须协议确认并留存对象日志不少于六个月。[FOUND: https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm] [L5: cac.gov.cn, 2025-03-14]

**人工确认约束**来自 2026 年 AI 客服国标报道：入口醒目、关键事项人工最终确认、切换完整传递记录。[FOUND: https://www.china.com.cn/txt/2026-09/11/content_118690907.shtml] [L5: china.com.cn, 2026-09-11]

**环境约束**：任务事件查询必须点名环境；未确认时任何指标值为 UNVERIFIED。[NEEDS-CONFIRMATION → 目标企业数据负责人: 阻断 M1/M2 可执行性]
