# RIB Heritage AR — Prompt Pack
### Ready-to-paste prompts for all 5 Qishlah Palace scenes

Everything here is built so you can be productive the moment your accounts are live. Work scene by scene: generate the **keyframe** in Midjourney → animate it in **Veo 3** → record narration in **ElevenLabs** → score it in **Suno** → assemble in **DaVinci/ffmpeg**.

**The 5 scenes:**
1. **The Gate** — horsemen arriving at the fortress gate
2. **The Courtyard** — soldiers at drill
3. **The Souq** — trade caravans and market life
4. **Governance** — scribes and councils at work
5. **Present ↔ Past Dissolve** — the modern palace fading into its living past

**Consistency tips (use across every scene):**
- Keep a fixed style suffix on every Midjourney prompt so all 5 keyframes match.
- Reuse the same light direction (warm low-angle desert sun) and palette (sandstone, ochre, deep blue sky) throughout.
- Generate keyframes at **16:9** so they map cleanly to video.

---

# PART A — Midjourney Keyframe Prompts

**Recommended settings for all:** add `--ar 16:9 --style raw --stylize 250` at the end. The shared style suffix below keeps the 5 scenes visually consistent — paste it on every prompt.

**Shared style suffix (append to each):**
`cinematic historical realism, warm low-angle desert sunlight, sandstone and ochre palette, deep blue sky, fine dust in the air, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250`

> Note: These render a Najdi/Arabian fortress setting in a generic, historically-inspired style. Avoid prompting real living people; use anonymous historical figures.

### Scene 1 — The Gate
```
A grand mud-brick Najdi fortress gate at golden hour, tall timber doors open, a group of robed horsemen on Arabian horses arriving across the sand toward the entrance, dust kicked up by hooves, palm trees flanking the wall, towering crenellated ramparts, wide establishing shot, sense of arrival and authority, cinematic historical realism, warm low-angle desert sunlight, sandstone and ochre palette, deep blue sky, fine dust in the air, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250
```

### Scene 2 — The Courtyard
```
Interior courtyard of a historic Arabian mud-brick fortress, rows of robed guards in formation at morning drill, long shadows across packed-earth ground, wooden balconies and shuttered windows on the surrounding walls, a banner on a tall pole, orderly and disciplined atmosphere, medium-wide shot at eye level, cinematic historical realism, warm low-angle desert sunlight, sandstone and ochre palette, deep blue sky, fine dust in the air, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250
```

### Scene 3 — The Souq
```
A bustling historic Arabian marketplace beside the fortress walls, camel caravans loaded with goods, merchants under woven awnings, baskets of dates and spices, traders haggling, woven textiles and copper wares on display, lively crowd in traditional robes, layered depth from foreground stalls to distant ramparts, cinematic historical realism, warm low-angle desert sunlight, sandstone and ochre palette, deep blue sky, fine dust in the air, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250
```

### Scene 4 — Governance
```
Interior majlis hall of a historic Arabian fortress, robed scribes seated on rugs writing on parchment, a council of elders in discussion around a low arrangement, soft light from high small windows falling across the room, carved wooden details and woven floor coverings, calm scholarly atmosphere, warm interior tones, cinematic historical realism, sandstone and ochre palette, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250
```

### Scene 5 — Present ↔ Past Dissolve (generate TWO matched frames)
Generate both from the same camera angle so they dissolve cleanly.

**5a — Present (today):**
```
The restored historic fortress today, clean preserved mud-brick walls, modern interpretive signage, a few visitors with phones, paved visitor path, bright midday clarity, same wide angle framing the main gate and ramparts, documentary realism, sandstone and ochre palette, deep blue sky, photoreal textures, 35mm film look --ar 16:9 --style raw --stylize 250
```
**5b — Past (living history):**
```
The same fortress alive in its historic past from the identical camera angle and framing, robed figures moving through the gate, horses and market activity, banners flying, weathered lived-in walls, dust and life in the air, golden-hour glow, cinematic historical realism, sandstone and ochre palette, deep blue sky, photoreal textures, volumetric light, 35mm film look --ar 16:9 --style raw --stylize 250
```

---

# PART B — Veo 3 Motion Prompts (image-to-video)

In Google Flow, upload the matching Midjourney keyframe, then paste the motion prompt. Keep clips to **8 seconds** (one "quality" generation ≈ 100 credits). Describe camera + subject motion only — the look is already set by the image.

### Scene 1 — The Gate
```
Slow cinematic push-in toward the open fortress gate as the horsemen ride closer; horses' manes and robes move in the wind, dust drifts across the frame, doors subtly sway. Smooth steady camera, gentle parallax, no cuts.
```

### Scene 2 — The Courtyard
```
Slow lateral dolly across the courtyard as the guards perform a synchronized drill step; banner ripples on the pole, shadows shift slightly, fine dust floats in the sunbeams. Steady cinematic motion, no cuts.
```

### Scene 3 — The Souq
```
Gentle handheld-style drift through the marketplace; camels shift their weight, merchants gesture, awnings flutter, smoke and dust catch the light, crowd moves naturally in the background. Lively but smooth camera, shallow depth, no cuts.
```

### Scene 4 — Governance
```
Very slow push-in on the seated scribes; hands move writing on parchment, the council leans into discussion, soft dust drifts in the window light, fabrics sway slightly. Quiet contemplative camera, minimal motion, no cuts.
```

### Scene 5 — Present ↔ Past (two short clips for the dissolve)
**5a — Present clip:**
```
Subtle slow push-in on the restored fortress today; a visitor walks slowly through frame, light shimmer of midday heat, almost still and documentary. Steady camera, no cuts.
```
**5b — Past clip:**
```
The same framing comes alive: robed figures and horses move through the gate, banners lift in the wind, dust and life fill the air, golden glow intensifies. Steady matching camera angle, no cuts.
```
> Stitch 5a → 5b with the ffmpeg `xfade=dissolve` command (see FFMPEG_REFERENCE.md) for the signature present→past transition.

---

# PART C — ElevenLabs Narration Scripts (English + Arabic)

Pick one warm, documentary-style narrator voice and reuse it for all scenes. Generate English and Arabic versions separately. Aim for a calm, measured pace.

### Scene 1 — The Gate
**EN:** "For centuries, these gates opened to riders carrying news, trade, and allegiance. To arrive here was to enter the heart of power in the region."
**AR:** "لِقرونٍ طويلة، فُتحت هذه البوابات لِفرسانٍ يحملون الأخبار والتجارة والولاء. الوصول إلى هنا كان دخولاً إلى قلب السلطة في المنطقة."

### Scene 2 — The Courtyard
**EN:** "Within these walls, discipline shaped the day. Each morning, the guard assembled — the steady rhythm of a fortress that never truly slept."
**AR:** "داخل هذه الجدران، كان الانضباط يرسم اليوم. في كل صباح يصطفّ الحرس، على إيقاعٍ ثابتٍ لِحصنٍ لا ينام."

### Scene 3 — The Souq
**EN:** "Beyond the walls, the market breathed life into the fortress. Caravans arrived heavy with dates, spices, and stories from distant lands."
**AR:** "خارج الأسوار، كان السوق يبثّ الحياة في الحصن. تصل القوافل مُحمّلةً بالتمر والتوابل وحكايات الأراضي البعيدة."

### Scene 4 — Governance
**EN:** "Here, decisions were weighed and written. Scribes preserved the word, and councils shaped the fate of a people through patient deliberation."
**AR:** "هنا كانت تُوزَن القرارات وتُكتَب. حفظ الكتّاب الكلمة، ورسمت المجالس مصير شعبٍ عبر تأمّلٍ متأنٍّ."

### Scene 5 — Present ↔ Past
**EN:** "Today the fortress stands quiet — preserved, restored. But look closer, and the past is never far away. It is still here, waiting to be seen."
**AR:** "اليوم يقف الحصن صامتاً، محفوظاً ومُرمَّماً. لكن إذا نظرت عن قُرب، فالماضي ليس بعيداً أبداً. إنه لا يزال هنا، ينتظر أن يُرى."

> Tip: In ElevenLabs, add a short pause between sentences using `...` or the pause control, and keep Stability ~50% / Similarity ~75% for a natural documentary tone.

---

# PART D — Suno Music Prompts

Generate one cohesive score, or short cues per scene. Use **instrumental** mode (no lyrics) so it sits under the narration. Pick a consistent instrument palette across all cues.

**Overall theme (one track for the whole piece):**
```
Instrumental cinematic documentary score, Middle Eastern / Arabian heritage mood, oud and ney flute over soft strings and gentle frame-drum percussion, warm and reverent, slow build, no vocals, film soundtrack quality
```

**Per-scene cues (optional, if scoring individually):**
- **Gate (arrival):** `Cinematic instrumental, rising and majestic, oud and strings, soft hand percussion building, sense of arrival and grandeur, Arabian heritage, no vocals`
- **Courtyard (discipline):** `Steady rhythmic instrumental, frame drum and low strings, disciplined measured pace, restrained tension, Arabian heritage, no vocals`
- **Souq (life):** `Lively warm instrumental, oud and hand percussion, bustling market energy, playful but cinematic, Arabian heritage, no vocals`
- **Governance (reflection):** `Slow contemplative instrumental, ney flute and sustained strings, scholarly calm, intimate, Arabian heritage, no vocals`
- **Dissolve (present↔past):** `Emotional cinematic swell, strings and oud, nostalgic and timeless, soft to full, bridging past and present, Arabian heritage, no vocals`

> After generating in Suno, download the **stems** (Pro plan) so you can balance music against the voiceover cleanly in DaVinci.

---

# Assembly Order (Workshop 05)

1. Generate all 5 keyframes (Midjourney) → confirm they look consistent.
2. Animate each into an 8s clip (Veo 3).
3. Record EN + AR narration (ElevenLabs).
4. Generate the score (Suno).
5. In **DaVinci Resolve** (or ffmpeg): lay clips in order, add the present→past dissolve, drop in narration, mix music underneath, color-match the clips.
6. Export to `assets/experience.mp4` (settings in FFMPEG_REFERENCE.md).
7. Deploy via GitHub Pages and generate the QR (see DEPLOY.md).
