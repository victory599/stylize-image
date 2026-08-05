# 情绪 / 季节氛围表

**职责**：氛围选项行与 `{MOOD}` 英文（完整版 / 紧贴短版）的单一事实源。  
**不写**：开关/匹配/回退、自定义精化与叠加句、输出文件名。  
**何时读**：问 Q9 前；氛围≠无 时生成前。

- 对用户只展示 **# / 氛围**；英文列仅供 `{MOOD}`
- 匹配与回退 → [question-cards.md](question-cards.md) Q9
- 选用/精化/叠加句 → [prompts.md](prompts.md) `{MOOD}`；文件名 → [policy.md](policy.md)「输出命名」

| # | 氛围 | 完整版（形似 / 再演绎）→ `{MOOD}` | 紧贴短版 → `{MOOD}` |
|---|------|-----------------------------------|---------------------|
| 1 | 雨夜 | Mood overlay: rainy night — cool wet reflections, soft rain streaks, lowered saturation, blue-gray cast. Do not add readable signage or letters. | Mood overlay: rainy night — cool blue-gray cast and lowered saturation; wet-surface sheen via lighting only. No rain streaks, puddle props, or readable signage. |
| 2 | 黄昏 | Mood overlay: dusk/golden hour — warm side/back light, long soft shadows, orange-to-violet sky shift. Keep subjects recognizable per the fidelity level. | Mood overlay: dusk/golden hour — warm side/back light and orange-to-violet color temperature only. Do not add props or change layout. |
| 3 | 初雪 | Mood overlay: first snow — diffuse light, cool whites, light mist, sparse snow dusting. Do not bury the subject. | Mood overlay: first snow — diffuse cool-white light and slight mist via atmosphere only. No snow accumulation props. |
| 4 | 夏日午后 | Mood overlay: summer afternoon — bright overhead light, higher key greens/cyans, gentle heat haze or leaf shade. No text. | Mood overlay: summer afternoon — bright overhead light and higher-key green/cyan temperature only. No added props. No text. |
| 5 | 霓虹夜 | Mood overlay: neon night — magenta/cyan spill light and glow only; reflections on wet ground optional. ABSOLUTELY no neon lettering, logos, or captions in the scene. | Mood overlay: neon night — magenta/cyan spill light and glow only. No wet-ground props, lettering, logos, or captions. |
| 6 | 雾晨 | Mood overlay: foggy morning — soft haze, muted distance, cool low-contrast air. Keep main subject readable. | Mood overlay: foggy morning — soft haze and cool low-contrast air via lighting only. Keep main subject readable. |
| 7 | 烛火室内 | Mood overlay: candlelit interior — warm localized key light, deep falloff, amber highlights. No readable text on props. | Mood overlay: candlelit interior — warm localized key light, deep falloff, amber highlights only. No new props or readable text. |
