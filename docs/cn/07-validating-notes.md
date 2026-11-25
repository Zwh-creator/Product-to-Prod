# 07 · 标签纪律自检与封印记录

返回：[总览](00-adaptation-overview.md) · [工作假设（非交付）](07-working-assumptions.md)

本页记录改造后的机械验证，验证对象是语法纪律，不是主张真伪；真伪仍由人查来源。

## 1. 上游 lint 的使用

```bash
# 在 fork 根目录（本机产物目录等价）
bash scripts/tag-lint.sh README.cn-adaptation.md docs/cn/00-adaptation-overview.md \
  docs/cn/01-evidence-base.md docs/cn/02-cn-ai-ops-prd.md \
  docs/cn/03-rice-backlog-cn.md docs/cn/04-gtm-launch-plan-cn.md \
  docs/cn/05-release-verification-cn.md docs/cn/06-portfolio-plan.md \
  docs/cn/07-validating-notes.md \
  handoff-cn/*.md handoff-cn/contracts/*.md --delivery-final
```

注意：`07-working-assumptions.md` 故意排除，因为它是 HYPOTHESIS 的合法残留处，不是交付正文。RICE 表与证据映射表用 `<!-- tag-lint:allow-multi -->` 标记，因为同一行合法列出多个证据状态。

## 2. 本地执行结果（2026-11-25）

用上游 `tag-lint.sh` 的规则副本对上述 17 个交付文件执行 `--delivery-final`：

```text
== TAG-LINT CLEAN: 0 violations across 17 file(s) ==
```

第一次运行发现 GTM「不可支持主张清单」同一行同时出现 FOUND 与 NEEDS-CONFIRMATION（T2），已用 `tag-lint:allow-multi` 标记为合法的映射表并复跑通过。`07-working-assumptions.md` 故意排除在交付检查之外，因为它是 HYPOTHESIS 的合法残留处。

说明：本目录内的 `tag-lint.sh` 只是本地验证副本（远端直连因 TLS 握手失败）；推送到 fork 后应改用它自带的 `scripts/tag-lint.sh` 复核同一组文件。

推送后在 PR 分支复核：17 个文件仍为 0 违规；交接包 8 个文件的哈希从 Git blob 重新计算，与 `.seal.txt` 全部一致。[FOUND: https://github.com/Zwh-creator/Product-to-Prod/pull/1] [L5: GitHub PR 页面, 2026-11-25 读取]

## 3. 完整性封印

封印覆盖 `HANDOFF.md`、`spec.md`、`plan.md`、`data-model.md`、`slices.json`、`case-contract.md` 与 `contracts/` 下全部文件。生成方式（绝不手算哈希）：

```bash
cd handoff-cn
for f in HANDOFF.md spec.md plan.md data-model.md slices.json case-contract.md contracts/*; do
  [ -f "$f" ] && sha256sum "$f"
done > .seal.txt
sha256sum -c .seal.txt
```

实际封印值（2026-11-25，`sha256sum -c .seal.txt` 全部 OK）：

| 文件 | sha256 |
|---|---|
| HANDOFF.md | 21c1a8d6fba6ddbc8fe81a064303f63f7720d2ae8e42cec07dcf8f0e30dd9c60 |
| spec.md | 0dbccf5e2f3a93195fd9fd3686ce7d262e58185c870aa1c86723c317946ebc8c |
| plan.md | 6ffad464df9ead2bf3022bd32058d773d0c56ddb0fbd4ff5222ed3fcdd7543c6 |
| data-model.md | b1496d53b9170b6c3e7d3affe6fa0b57e19dcb3cd3a3cf38b69a129e39e944ab |
| slices.json | 3a501a9449f48d41c2e4650a48d3aa413ed587a527429b071d52c30e44f7c074 |
| case-contract.md | 2f47583abbce3494a53a642c97688ad1253d1aeb9a34b3530b540c96b33eb2e9 |
| contracts/compliance-label.contract.md | 0585c8cec0b072468695a3ca8e8d8bf7ffe9dd3fd29640da7a9edfe863fc1643 |
| contracts/eval-gate.contract.md | 71377d09990b778ebd3a929b8ac9370242e60dbfa49f6f7b2b1ce4370f1ace46 |

哈希写入 `design-gate.json`、`.seal.txt` 与本页。这里**没有**把哈希回填到 `case-contract.md`：那会使该文件在封印后被改动、导致其自身哈希失效；人类可读副本放在本页，机器校验用 `.seal.txt`。这是一处刻意调整，不改变封印强度。`approved: false` 时封印一次；批准之后不得重新封印，改动应升微版本。

## 4. 允许的失败

`tag-lint` 的退出码：0 干净，1 有违规，2 无法读取。退出码 2 是失败而不是通过；无法运行的检查不能算通过。[FOUND: https://github.com/naderelewa/Product-to-Prod#tests-and-hygiene] [L5: 上游 README, 2026-11-25 读取]
