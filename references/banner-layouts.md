# 标题区布局表

布局取值与 `{BANNER_LAYOUT}` 的**单一事实源**。英文列仅供生成，勿展示给用户、勿写入提问卡。文件名后缀见 SKILL「场景与命名」，不在本表。

取值须与「布局」列严格全等（无 / 底 / 顶 / 侧 / 溶字）。选项与默认/回退见 [question-cards.md](question-cards.md) Q3。
选哪套生成模板、布局=无时是否填本占位符 → [prompts.md](prompts.md)「选模板」/ `{BANNER_LAYOUT}`。

| 布局 | 有标题区 | 有横幅 | 提示词原文（英文）→ `{BANNER_LAYOUT}` |
|------|----------|--------|----------------------------------------|
| 无 | 否 | 否 | （不适用） |
| 底 | 是 | 是 | Title area: along the bottom, a cream plaque banner with ornamental lines (about one-third of the shorter side), banner finish adapted to the image style. Place title on this banner only. |
| 顶 | 是 | 是 | Title area: along the top, a cream plaque banner with ornamental lines (about one-third of the shorter side), banner finish adapted to the image style. Illustration fills the area below. Place title on this banner only. |
| 侧 | 是 | 是 | Title area: a cream vertical plaque strip along the left edge (about one-quarter to one-third of the width), banner finish adapted to the image style. Illustration fills the remaining area. Place title on this strip only (horizontal multi-line or vertical type both OK if legible); keep the strip clearly separated from the art. |
| 溶字 | 是 | 否 | Title area: no cream plaque and no solid banner bar. Integrate the title into the illustration over a quiet/negative-space or darker region. Title must stay highly legible via contrast, outline, or soft shadow—never same color+texture as the art behind it. No large opaque title board. Title is the only text. |
