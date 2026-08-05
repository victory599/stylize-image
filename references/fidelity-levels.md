# 忠实度表

取值与提示词的**单一事实源**。填 `{FIDELITY}`、以及 `{MOOD}` 非空时的叠加句时读本文件。英文列仅供生成，勿展示给用户、勿写入提问卡。

取值须与「忠实度」列严格全等。跳过或不在表内 → `形似`（见 Q7、defaults）。文件名用本列原文（仅非默认写入），见 SKILL「场景与命名」。`{FIDELITY}` 句末追加（底/顶/侧 vs 溶字+紧贴等）见 [prompts.md](prompts.md)，勿改写表内原文。

| 忠实度 | 提示词原文（英文）→ `{FIDELITY}` | 氛围叠加句（英文）→ 接在 `{MOOD}` 后 |
|--------|----------------------------------|--------------------------------------|
| 形似 | Fidelity: recognizable likeness. Keep the source image's main subject identity, overall composition, and emotional tone of the subject matter recognizable. Minor props and background may be simplified or merged. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Mood may lightly affect atmosphere and subtle environment cues; do not replace the main subject. |
| 紧贴 | Fidelity: close match. Closely preserve the source image's subject placement, pose/orientation, foreground–background layering, and major color-block layout. Change medium and technique only; do not rearrange the scene. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Apply mood only as lighting/color-temperature shift; do not add weather props or change layout. |
| 再演绎 | Fidelity: loose reinterpretation. Keep only the source image's theme keywords and emotional tone of the subject matter. Composition, camera angle, and props may change freely. Recreate in the specified style; do not merely filter, recolor, or LUT the source. | Mood may reshape environment, weather, and time of day while keeping theme keywords. |
