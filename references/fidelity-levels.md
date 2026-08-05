# 忠实度表

**职责**：忠实度取值、`{FIDELITY}` 原文、氛围叠加句的单一事实源。  
**不写**：问答回退、布局句末追加、输出命名段序。  
**何时读**：生成前必读；`{MOOD}` 非空时用叠加句。

- 取值与「忠实度」列严格全等；跳过/表外 → `形似`（Q7 / policy）
- 英文列仅供生成，勿展示用户、勿写入提问卡
- 句末追加 → [prompts.md](prompts.md) `{FIDELITY}`；文件名非默认段 → [policy.md](policy.md)「输出命名」

| 忠实度 | 提示词原文（英文）→ `{FIDELITY}` | 氛围叠加句（英文）→ 接在 `{MOOD}` 后 |
|--------|----------------------------------|--------------------------------------|
| 形似 | Fidelity: recognizable likeness. Keep the source image's main subject identity, overall composition, and emotional tone of the subject matter recognizable. Minor props and background may be simplified or merged. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Mood may lightly affect atmosphere and subtle environment cues; do not replace the main subject. |
| 紧贴 | Fidelity: close match. Closely preserve the source image's subject placement, pose/orientation, foreground–background layering, and major color-block layout. Change medium and technique only; do not rearrange the scene. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Apply mood only as lighting/color-temperature shift; do not add weather props or change layout. |
| 再演绎 | Fidelity: loose reinterpretation. Keep only the source image's theme keywords and emotional tone of the subject matter. Composition, camera angle, and props may change freely. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Mood may reshape environment, weather, and time of day while keeping theme keywords. |
