---
name: stylize-image
description: Restyle source images with selectable art styles (single or multi-style 2–3), fidelity, optional mood/season overlay, title area (bottom/top/side/overlaid) and border. Use for 图片风格化, stylize-image, 封面风格化, or stylize-cover-image.
disable-model-invocation: true
---

# 图片风格化转换

把已有图片按选定画面风格重绘。本文件是**调度页**；细则在 `references/`，勿外链包外规范。

**图标**：📌 主流程；▶ 条件追问；🚪 门控；❗️ 红线。图标不进提问卡代码块。

## 产品约定

- 配置以用户确认为准；整幅按所选风格**从头重现**（非滤镜、非贴图、非 LUT）
- 画面风格 × 忠实度 × 氛围正交：贴合程度见 [fidelity-levels.md](references/fidelity-levels.md)；氛围只调光色与天气/环境感，不换画风
- 标题区：无 = 满铺、绝对无字；底/顶/侧 = 题字仅在铭牌/侧条；溶字 = 无铭牌/旁饰、仅一处标题字（与文字风格旁饰不一致时，以 prompts 溶字模板与 `{FONT_STYLE}` 溶字规则为准）
- 边框与布局英文展开见 [prompts.md](references/prompts.md) / [banner-layouts.md](references/banner-layouts.md)；术语见 [defaults.md](references/defaults.md)

## 读什么

| 何时 | 读哪些 |
|------|--------|
| 开始前 | [defaults.md](references/defaults.md) |
| 提问时 | [question-cards.md](references/question-cards.md)；Q2 前→[image-styles.md](references/image-styles.md)；Q6 前→[font-styles.md](references/font-styles.md)；Q9 前→[mood-modifiers.md](references/mood-modifiers.md) |
| 生成前 | **必读** [prompts.md](references/prompts.md)、[image-styles.md](references/image-styles.md)、[fidelity-levels.md](references/fidelity-levels.md)（Q1=a/c 路径同样必读，非表内档位）；有标题区→[banner-layouts.md](references/banner-layouts.md)；需题字→[font-styles.md](references/font-styles.md)；氛围≠无→[mood-modifiers.md](references/mood-modifiers.md) |

只用包内 `references/`。提问照搬 question-cards；取值与默认见 defaults。跳过/未确定 → 该题默认项；禁止未问就替用户选定；未到的题不提前读对应表。自定义分批见 question-cards。

## 📌 总流程

调度顺序如下。提问分批 / 记录 / 门控 → [question-cards.md](references/question-cards.md)；取值 → [defaults.md](references/defaults.md)。

```text
读本页「产品约定」、defaults
  → 问 Q1
      → a 默认配置
            套用 defaults 主表 + 布局分支（不问 Q2–Q11；单风格；不经 G1/G2）
      → b 自定义（见 question-cards）
            → 📌 幕1：Q2 → Q3 → Q4
            → 有标题区？ → 是：▶ 幕2 Q5 → Q6；否：跳过幕2
            → 📌 幕3：Q7 → Q8 →（开：▶ Q9）→ Q10 → Q11（分批见 question-cards）
      → c 按所述配置
            见 defaults「按所述配置」（不问 Q2–Q11；无可解析偏好 → 回退 a；
            标题意图见 question-cards Q3）
  → 多风格且多源？（仅 b/c 可能；a 不会）
        → 是：🚪 G1（G1=b 再 G2）
        → 否：跳过
  → 若需 AI 拟定标题 → 见 defaults「标题文字」
  → 生成前复述（侧条+横图见 defaults「画幅比例」）
  → 用户明确确认（「确认」「开始生成」「可以」等）后方可生成
  → 按「读什么·生成前」读表 → GenerateImage（源图 × 风格，可并行；
        共用项见 defaults「多风格共用」；
        aspect_ratio=该源图比例；reference_image_paths=该源图仅一张）
  → 移到输出目录，按下方「场景与命名」重命名
        → 同名输出见 defaults「输出目录」
        → 列出路径（多风格按风格分组）
```

术语见 defaults。

## 场景与命名

取源文件名去扩展名后稀疏拼接（默认档不写入文件名），段序固定。

```text
{源文件名去扩展名}-{风格短名}[-{忠实度}][-{氛围}][-有边框]{布局后缀}
```

| 段 | 取值 | 写入条件 |
|----|------|----------|
| 风格短名 | 表内→[image-styles.md](references/image-styles.md)「文件名短名」；自定义风格提炼 2–4 字 | 始终 |
| 忠实度 | [fidelity-levels.md](references/fidelity-levels.md)「忠实度」列原文 | ≠ `形似` |
| 氛围 | 表内→[mood-modifiers.md](references/mood-modifiers.md)「氛围」列；自定义氛围提炼 2–4 字 | 氛围 ≠ 无 |
| 有边框 | 固定词 `有边框` | 要边框 |
| 布局后缀 | 下表；布局取值见 [banner-layouts.md](references/banner-layouts.md) | 始终（无为 `.png`） |

自定义风格/氛围短名避开非法字符，复述时告知。

| 布局 | 布局后缀 | 示例 |
|------|----------|------|
| 无 | `.png` | `photo-绘本水粉.png` |
| 底 | `-底横幅.png` | `photo-绘本水粉-底横幅.png` |
| 顶 | `-顶横幅.png` | `photo-绘本水粉-顶横幅.png` |
| 侧 | `-侧条.png` | `photo-绘本水粉-侧条.png` |
| 溶字 | `-溶字.png` | `photo-绘本水粉-溶字.png` |

例：`photo-绘本水粉-紧贴-雨夜-有边框-底横幅.png`；`photo-绘本水粉-黄昏-溶字.png`（形似默认不写）。

## ❗️ 红线

- 未复述并获明确确认前，不得 `GenerateImage`
- 永不覆盖源文件
- 禁止 M×K → defaults「多风格 × 多源」
- 标题区回退 → question-cards Q3
- 氛围 `关/无` → defaults；题字/溶字/霓虹装配 → prompts
- 同名输出 → defaults「输出目录」
