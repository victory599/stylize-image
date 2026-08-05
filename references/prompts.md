# 生成提示词

**职责**：占位符装配规则与生成模板的**单一事实源**。  
**不写**：默认值/回退、题面、表行原文（长英文段以各表为准，本文件只写装配）。

生成前读本文件。占位符逐项替换，模板中不得残留花括号。

## 通用规则

**自定义描述精化**：过简 → 按维度扩为名称 + 特征短语（长度对齐表内行）；已详 → 保留全部有效信息，仅结构化与修缮。

`{MOOD}` 为空则删其所在空行；非空则单独成行。

## 占位符

### `{ASPECT}`

支持比例 → [policy.md](policy.md)「画幅比例」。填入对应英文：`{比例} aspect ratio`（例：`16:9 aspect ratio`）。

### `{IMAGE_STYLE}`

表内 → 取 [image-styles.md](image-styles.md) 对应行原文（译英，勿改写）。  
自定义过简 → 按技法/笔触、配色、质感/纹理、光影扩为名称 + 3–5 短语。

### `{PALETTE}`

| 条件 | 填入 |
|------|------|
| 氛围=无 | `Muted or style-appropriate palette matching the source image's mood.` |
| 氛围≠无 | `Palette and lighting follow the mood overlay below; keep style-appropriate chroma. Prefer mood overlay over the source image's original time-of-day when they conflict, subject to fidelity rules.` |

### `{MOOD}`

| 条件 | 填入 |
|------|------|
| 氛围=无 | 空（删空行） |
| 表内氛围 | 按当前忠实度取 [mood-styles.md](mood-styles.md) 对应英文列整段：形似/再演绎→「完整版」；紧贴→「紧贴短版」 |
| 自定义氛围 | `Mood overlay: ` + 精化一句（过简时按光影、色温/饱和、天气/环境点缀扩写；已详不压缩；**紧贴**时只写光色/色温，不加天气道具） |

非空时再追加 [fidelity-levels.md](fidelity-levels.md) 当前忠实度的「氛围叠加句」（勿改写；与源图时光/环境冲突时以叠句为准）。

### `{FIDELITY}`

1. 先填 [fidelity-levels.md](fidelity-levels.md) 当前忠实度「提示词原文」整段（勿改写）。  
2. 再按布局句末追加（**互斥，勿叠用**）：

| 条件 | 追加 |
|------|------|
| 布局∈{底,顶,侧} | `Apply fidelity to the illustration area only; the title area may be newly composed.` |
| 布局=溶字 且 忠实度=紧贴 | `Overlaid title (no plaque): a slight quiet/negative-space may be opened for title legibility only; keep subject placement, pose/orientation, and major color-block layout close-match—do not rearrange the scene beyond that.` |
| 布局=溶字 且 忠实度≠紧贴 | 不追加（溶字无独立标题板块；可读性见溶字模板与 `{BANNER_LAYOUT}`） |
| 布局=无 | 不追加 |

### `{BORDER}`

按「边框 × 布局」展开（勿混用）：

| 边框 | 布局 | 填入 |
|------|------|------|
| 不要 | 无 | `Keep the illustration edge-to-edge, full-bleed, no border, no ornamental frame.` |
| 不要 | ∈{底,顶,侧,溶字} | `No border, no ornamental frame.` |
| 要 | 无 | `Add a thin hand-drawn decorative border with small corner flourishes that wraps the entire image edge-to-edge. Do not add any title area, plaque, or strip.` |
| 要 | ∈{底,顶,侧,溶字} | `Add a thin hand-drawn decorative border with small corner flourishes that wraps the entire image including the title area; plaques/strips sit inside the border.` |

### `{BANNER_LAYOUT}`

仅有标题区模板使用。取 [title-layouts.md](title-layouts.md) 对应行（勿改写）。布局=无时不用。

### `{TITLE}`

已确认标题；取自文件名时去扩展名。

### `{FONT_STYLE}`

| 文字风格 | 填入 |
|----------|------|
| 非 0 | 取 [font-styles.md](font-styles.md) 对应行原文（译英，勿改写） |
| **0** | **禁止**填文字表第 0 行（元规则）。从当前画面风格提炼字形/材质/配色，展开为具体题字描述；勿照抄整段 `{IMAGE_STYLE}`；长度对齐文字表非 0 行 |
| 自定义过简 | 按字形、配色、装饰/质感扩为名称 + 2–3 短语 |

**0 的展开示例**（非穷尽，可略调）：

| 画面风格 | 英文示例 |
|----------|----------|
| 0 绘本水粉 | Soft hand-lettered title, gouache-like strokes, warm muted inks, slight paper grain; keep high contrast from the art |
| 1 赛璐珞 | Clean cel-animation title lettering, soft outline, translucent color fills |
| 4 木刻 | Woodcut/block-print carved letterforms, limited ink colors, stamped print feel |

**溶字**：以溶字模板为准；写入前去掉旁侧图形/火漆印/绳结饰等「题字旁装饰」；**保留**字形自身的连笔、环绕笔画装饰。

---

## 模板

选模板：布局=无 →「无标题区」；布局∈{底,顶,侧} →「有横幅」；布局=溶字 →「溶字」。布局语义列见 [title-layouts.md](title-layouts.md)。

### 无标题区

布局 = 无。

```text
Restyle the source image into a {ASPECT} image in this image style: {IMAGE_STYLE}. {PALETTE} Illustrated scene. {BORDER} No title area, no plaque or strip anywhere.
{MOOD}
ABSOLUTELY NO TEXT, NO LETTERS, NO LOGOS, NO CAPTIONS — strip any text from the source image. {FIDELITY}
```

### 有标题区 · 底 / 顶 / 侧（有横幅）

```text
Restyle the source image into a {ASPECT} image in this image style: {IMAGE_STYLE}. {PALETTE} Main area: illustrated scene. {BORDER}
{MOOD}
{BANNER_LAYOUT}

On the title area, title "{TITLE}" as the largest text, styled as: {FONT_STYLE}. Title must read as its own layer—high legibility, separated from the illustration by contrast, outline, emboss/shadow, and/or the cream plaque; never same color+texture as the art behind it (avoid blending/fusion). Title-area-only so the illustration stays primary. Tiny theme motifs beside the title on the plaque/strip. No other text outside the title area. {FIDELITY}
```

### 有标题区 · 溶字（无横幅）

```text
Restyle the source image into a {ASPECT} image in this image style: {IMAGE_STYLE}. {PALETTE} Main area: illustrated scene. {BORDER}
{MOOD}
{BANNER_LAYOUT}

On the title area, title "{TITLE}" as the largest text, styled as: {FONT_STYLE}. Title must read as its own layer—high legibility via contrast, outline, or soft shadow only; never same color+texture as the art behind it (avoid blending/fusion). No cream plaque, no solid title board, no decorative motifs beside the title. Title is the only text. {FIDELITY}
```
