<!-- 把本文件内容合并到 fork 的 README.md 顶部；保留上游 LICENSE、provenance 与全部脚本。 -->

# Product2Prod · 国内 AI 产品运营/落地改造版（CN-AI-Ops）

**一句话定位**：把上游 `naderelewa/Product-to-Prod` 的「证据标签 → PRD → RICE → GTM → 发布验收」方法，改造成一套可用于国内 AI 产品运营/落地岗位求职作品集的案例包。

**案例性质声明（先读这一条）**：本改造是一个**文档化案例（documented case study）**。外部行业数据、法规条款与招聘要求均来自可复查的公开来源，并在文中带标签与链接；产品指标、RICE 输入与发布验收阈值是**为案例设定的目标或待确认项**，不是已实现的业务结果。所有未确认项均以 `NEEDS-CONFIRMATION` 显式登记，不伪装成已验证事实。

## 与上游的关系

| 项 | 上游 | 本改造 |
|---|---|---|
| 方法骨架 | 5 阶段需求循环、双镜头 RICE、三闸门 GTM、只读发布验收 | **完全沿用**，不另造一套流程 |
| 语境 | 通用产品管理、 `{company}` 由 pack 注入 | 国内 AI 产品运营/落地，新增 `cn-ai-ops` 语境说明 |
| 证据 | 六标签 + L0–L5，强调「无锚点不主张」 | 增加 **15 行可复查的国内公开证据**（法规、行业报告、企业案例、招聘 JD） |
| 交付物 | 方法/脚本仓库 | 增加一个**完整可评审的产品案例**：PRD、RICE 批次裁决、GTM、验收计划、handoff 包 |
| 合规 | 通用「不可支持主张清单」 | 增加**国内专属合规门禁**：生成内容标识、备案材料、转人工与关键事项人工确认 |

## 交付目录

- `docs/cn/00-adaptation-overview.md` — 差异化改造总览与作品集叙事
- `docs/cn/01-evidence-base.md` — 业务证据账本与可见的缺口
- `docs/cn/02-cn-ai-ops-prd.md` — 带证据的 PRD（国内 AI 产品运营控制台）
- `docs/cn/03-rice-backlog-cn.md` — 双镜头 RICE 批次裁决与冲刺建议
- `docs/cn/04-gtm-launch-plan-cn.md` — 分阶段发布全流程（配置提案，不执行）
- `docs/cn/05-release-verification-cn.md` — 预声明验收场景与度量计划
- `docs/cn/06-portfolio-plan.md` — 求职作品集差异化方案与分步落地清单
- `docs/cn/07-validating-notes.md` — 标签纪律自检与密封结果
- `docs/cn/07-working-assumptions.md` — 非交付件：HYPOTHESIS 与验证触发器
- `handoff-cn/` — 按上游 P4 结构落盘的交接包（`approved: false`，含 `.seal.txt`）

## 快速复核

```bash
# 从 fork 根目录执行；验证新增文档没有破坏上游的证据标签语法
bash scripts/tag-lint.sh docs/cn/*.md handoff-cn/*.md
```

## 发布状态

- 本改造已推送到 `Zwh-creator/Product-to-Prod` 的 `cn-ai-ops-adaptation-pr` 分支，并开启 PR #1。[FOUND: https://github.com/Zwh-creator/Product-to-Prod/pull/1] [L5: GitHub PR 页面, 2026-11-25 读取]

## 来源

上游仓库：https://github.com/naderelewa/Product-to-Prod （MIT）。本改造文档同样按 MIT 使用；引用来源见 `docs/cn/01-evidence-base.md`。
