---
name: stylize-image
description: Restyle source images with selectable art styles (single or multi-style), fidelity, optional mood/season overlay, title area (bottom/top/side/overlaid) and border. Total outputs M×K capped at 9. Use for 图片风格化, stylize-image, 封面风格化, or stylize-cover-image.
disable-model-invocation: true
---

# 图片风格化转换

把已有图片按选定画面风格重绘。本文件是**调度页**；细则在 `references/`，勿外链包外规范。

**图标**：📌 主流程；▶ 条件追问；🚪 门控；❗️ 红线。图标不进提问卡代码块。

## 文档权责

| 文件 | 独占写什么 | 不写 |
|------|------------|------|
| 本页 SKILL | 流程调度、读什么、产品约定（极短）、红线指针 | 默认值细则、题面、英文装配、表行 |
| [policy.md](references/policy.md) | 默认/回退/跨题策略、术语、画幅、输出目录、上限触发与 N、输出命名 | 题面 Options、G1/G2 收束步骤、prompt 模板、表行原文 |
| [question-cards.md](references/question-cards.md) | 题面、Options、记录字段、门控时点、G1/G2 收束步骤（仅该节） | 默认主表、画幅映射、输出命名/目录算法、英文提示词；其它处不写上限公式 |
| [prompts.md](references/prompts.md) | 占位符装配规则与生成模板 | 问答流程、默认值、表行原文 |
| 各表（`image-styles` / `font-styles` / `mood-styles` / `title-layouts` / `fidelity-levels`） | 选项行与生成用原文/短名 | 流程、回退、跨题策略 |

新约束只写入上表对应文件；其它处最多留指针。

## 产品约定

- 配置以问答记录为准；复述须写全再生成；整幅按所选风格**从头重现**（非滤镜、非贴图、非 LUT）
- 画面风格 × 忠实度 × 氛围正交：氛围只调光色与天气/环境感，不换画风
- 标题区有无与布局取值决定题字模板；默认与回退见 policy，装配见 prompts（读表时机见「读什么」）

## 读什么

| 何时 | 读哪些 |
|------|--------|
| 开始前 | [policy.md](references/policy.md) |
| 提问时 | [question-cards.md](references/question-cards.md)；Q2 前→[image-styles.md](references/image-styles.md)；Q6 前→[font-styles.md](references/font-styles.md)；Q9 前→[mood-styles.md](references/mood-styles.md) |
| 生成前 · 必读 | [prompts.md](references/prompts.md)、[image-styles.md](references/image-styles.md)、[fidelity-levels.md](references/fidelity-levels.md)（Q1=a/c 同样必读） |
| 生成前 · 按需 | 有标题区→[title-layouts.md](references/title-layouts.md)；需题字→[font-styles.md](references/font-styles.md)；氛围≠无→[mood-styles.md](references/mood-styles.md) |

只用包内 `references/`；提问照搬 question-cards；禁止未问代选；未到题不提前读表。

## 📌 总流程

顺序：**Q1 三选一 → 公共收尾**（分支只在 Q1；之后三条共用）。

1. **问 Q1**
   - **a 默认**：套用 policy 主表 + 布局分支（不问 Q2–Q11；单风格）→ 若 T>9 则 🚪 G1/G2
   - **b 自定义**：幕1 Q2→(超限则 G1/G2)→Q3→Q4；有标题区则 ▶ 幕2 Q5→Q6；幕3 Q7→Q8→(开则 ▶ Q9)→Q10→Q11（分批见 question-cards）
   - **c 所述**：policy「按所述配置」（标题意图按 Q3 记录）→ 风格解析后若 T>9 则 🚪 G1/G2 → 若需追问氛围则 ▶ Q9（不问 Q8；见该节氛围）→ 再进下一步
2. **画幅** → 按 policy「画幅比例」落定（含读不到源图）
3. **若**需 AI 拟标题 → policy「标题文字」
4. **复述**（写明 M'×K'=T' 与画幅结果）
5. **读**「读什么」生成前 · 必读/按需 → `GenerateImage`（可并行；policy「多风格共用」；`aspect_ratio`←画幅；每源仅一张 reference）
6. **落盘** → policy「输出目录」（含移动到位、不留临时副本、同名处理）；列出最终路径（多风格分组）

## ❗️ 红线

- 未复述前，不得 `GenerateImage`
- 不覆盖源文件；同名输出冲突 → policy「输出目录」
- `T>9` 未经 G1/G2 收束不得生成 → policy「总出图上限」

## 易错指针

- 标题区回退 → question-cards Q3
- 禁止 `开` 且 `氛围=无` → policy「氛围」
- 题字/溶字/边框装配 → prompts
