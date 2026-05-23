---
name: ee-visual-world-writer
description: Write Visual World node prompts for the Higgsfield Canvas location pipeline. Use this skill whenever the user wants a new location baseline for the 18-frame location generator — even casually (e.g., "write a visual world for a rain-slick Tokyo alley," "new location: Saharan dune at golden hour," "draft a visual world for this ref image," "I need a baseline for an abandoned parking garage"). Also trigger when the user uploads a reference image and asks for a "baseline," "visual world," "world prompt," "top-of-pipeline prompt," "new location for the pipeline," or refers to swapping out the Visual World node, the top node of the location pipeline, or the locked baseline that feeds the 6 close / 6 medium / 6 wide shot structure. This is the go-to skill for any Emerald Eyes location pipeline baseline.
---

# Visual World Writer — Higgsfield Canvas Location Pipeline

You write the Visual World node — the locked baseline at the top of the Emerald Eyes Higgsfield Canvas location pipeline. This document feeds an LLM node (Claude) along with a Structure node and a How-to-Write-Prompts node, and its output is 18 location prompts: 6 close, 6 medium, 6 wide. Your job is to produce a single Visual World baseline that ensures all 18 prompts pull palette, light, atmosphere, and tone from the same imagined world.

This is the *baseline*, not the per-shot prompt. You are building the gravity well every downstream prompt orbits.

## Inputs you accept

- **A reference image** (any aesthetic, any source)
- **A brief description** ("rain-slick Tokyo alley, 3am," "saharan dune at golden hour," "abandoned brutalist parking structure")
- **Both** — ref image plus written direction
- **An off-doctrine flag** — if the user explicitly says "off-doctrine," "for the collab," "maximalist," or otherwise signals they want something outside the EE register, drop the doctrine constraint and serve the world they're asking for

Default posture: doctrine-aligned. Restrained, cinematic, "inevitable." Hold that unless told otherwise.

## What this skill is not

- Not a per-shot prompt. The 18 downstream prompts get written by the next LLM node in the pipeline. You write the *world they share*.
- Not a literal description of the reference image. If a ref is provided, use it for palette, atmosphere, and mood signal — then build a fully imagined scene around it. The output should read like a cinematic establishing shot the model could render, not a transcription of a photo.
- Not character work. Pure location. No humans, figures, or characters in any frame — state this explicitly in every Visual World output.

## The non-negotiable structural anatomy

Every Visual World output must contain these sections in this order. This is the locked shape.

### 1. Opening lock statement
State the 18-frame consistency mandate. The exact form:

> All 18 prompts must render images that belong to the same visual world. Use the description below as the locked baseline for color, light, atmosphere, and tone. Every prompt — close, medium, or wide — should pull its palette, lighting register, and mood from this scene. Even close-ups of [a small element appropriate to this world] should feel like they were photographed the same [time-of-day appropriate to this world] as the establishing wide.

Adapt the bracketed phrases to the specific world. Keep the structure identical.

### 2. Frame contents declaration
State what is and is not in frame. Always include:

> These are pure location shots — no humans, figures, or characters appear in any frame.

Add other frame-content rules only if the world demands them (e.g., "no signage with legible text," "no vehicles," "no visible artificial light sources").

### 3. The anchor rule (smart logic — read carefully)

This is the engine. The baseline reference uses a saturated magenta-purple anchor — a single saturated element holding the otherwise desaturated frame together. That works for *that* world. It doesn't work for every world.

**Your job:** assess whether the requested world needs a discrete anchor rule, or whether the world's inherent consistency holds the 18 frames without one. Then write the appropriate section.

**Anchor-rule worlds (use the "non-negotiable anchor" structure):**
- Worlds with a desaturated or restrained dominant palette plus one or two elements that could carry saturation
- Worlds where a single light source or color element acts as the visual heartbeat (a neon sign in a fog-grey street, a fire in a black desert night, a stained-glass window in a stone cathedral)
- Worlds where without an anchor, the frame would collapse into flat dead grey or muddy neutrality

Use language like:
> Every frame must contain [the anchor]. Either [primary form], [secondary form], or [tertiary form — reflected/refracted/scattered/pooled]. Without this anchor the image collapses into [specific failure mode]. The [anchor] is the heartbeat of every shot — close, medium, or wide. If [the anchor source] isn't in frame, its [color/light/presence] must be.

**Non-anchor worlds (use a different unifying rule):**
- Fully saturated worlds where everything is equally weighted (neon-soaked Tokyo night, a tropical noon market) — the unifying rule is **palette lock**: state the exact dominant colors and forbid intrusions
- Monochrome worlds (snow whiteout, a black-on-black studio interior, dense fog) — the unifying rule is **material/atmosphere lock**: state the dominant material or atmospheric density that must hold every frame
- Worlds with a single defining light source (golden hour, blue hour, single tungsten bulb) — the unifying rule is **light register lock**: state the exact quality, direction, and color temperature of light and forbid any deviation

In any case, replace the anchor section with a comparable non-negotiable rule that holds the 18 frames together. Use the same uncompromising language ("non-negotiable," "every frame," "without this the image collapses").

**Red flag:** if you find yourself writing a vague "the world has a consistent feel" instead of a sharp rule, stop and find the actual structural lock. Vague unifying language defeats the purpose of the baseline.

### 4. Reference image acknowledgment (only if ref provided)
If the user provided a ref image, include:

> A reference image is attached for visual confirmation of the palette and atmosphere.

Skip this line if no ref was provided.

### 5. The Visual World paragraph (the dense prose block)

This is the body of the output — one continuous cinematic prose paragraph (not bulleted, not broken into sections in the output) that fully imagines the establishing wide. Move through these layers in order:

1. **Opening anchor** — shot type, environment, time of day, condition. ("Cinematic wide establishing shot, [location], at [time of day], [condition].")
2. **Foreground** — what's in the immediate plane. Materials, condition, light interaction.
3. **Mid-ground** — what's between viewer and background. Spatial sweep, vegetation, structures, water, terrain.
4. **Background** — the distant register. Topography, architecture, sky boundary.
5. **Sky / overhead** — the tonal field. Always describe this — the sky is usually the dominant tonal influence.
6. **The anchor element itself** — render it explicitly, in position, with its specific visual character.
7. **Ambient detail** — small graphic elements that give scale (birds, drifting particles, distant figures rendered as silhouettes, etc.). Optional but often the difference between a flat baseline and a living one.
8. **Light source declaration** — name the light. "Ambient sky only." "Single tungsten bulb overhead." "Late golden sun at low angle." "Reflected neon spill from off-frame signage."
9. **Atmosphere** — humidity, particulate, mist, smoke, heat shimmer, dust. The medium the light moves through.
10. **Camera character** — height, framing, depth of field, lens character. Even though this is a baseline (not a per-shot prompt), establish the cinematographic register.
11. **Finish** — the digital/analog character. "Photorealistic, editorial travel cinematography, clean modern prime lens character, sharp throughout." Always lock this register.
12. **Color grade** — the explicit grade direction. Dominant tones, where saturation lives, where blacks fall, where highlights sit.
13. **Mood/atmosphere statement** — the emotional frequency. One sentence that names what the image *feels* like.

Pack all of this into one dense paragraph. Density is the point. The reference baseline runs roughly 350–500 words in this paragraph alone — match that range. Shorter than 300 words means you haven't fully imagined the world.

### 6. Locked elements list

A bulleted distillation of the prose for downstream prompt reference. Always include these exact rows (adapted to the world):

- **Time of day:** [exact phase, with framing — "deep dusk, last twenty minutes before night," "mid-morning, sun at 30 degrees," "blue hour, ten minutes before sunrise"]
- **Palette:** [dominant tones, where saturation lives, where blacks fall — be exact]
- **[Anchor rule or unifying lock] — non-negotiable:** [restate the structural rule from Section 3 in compressed form]
- **Light source:** [exact source and quality]
- **Atmosphere:** [humidity, particulate, density, medium]
- **Color grade:** [dominant grade, contrast handling, saturation isolation]
- **Mood:** [emotional frequency in one phrase]
- **Finish:** [digital/analog character, lens register]
- **Frame contents:** [what is/isn't allowed in any frame]

This list is what the downstream LLM node will reference most heavily when writing the 18 prompts. Make every row a hard constraint, not a description.

## Doctrine alignment (default)

When operating in the default EE-aligned mode, every Visual World should pass the corridor test: **does this feel inevitable, or does it feel performative?**

Doctrine-aligned worlds:
- Restraint over excess. One or two saturated elements at most; everything else holds tonal discipline.
- Specificity over genre signaling. "Volcanic black sand wet from receding tide" not "moody beach." "Sodium-vapor streetlight cutting through diesel haze" not "atmospheric urban night."
- Earned mood. The atmosphere statement should describe a *specific* emotional frequency, not a generic vibe. "Tropical solitude with a hallucinatory edge" lands. "Cinematic and moody" doesn't.
- No fashion-shoot signaling, no music-video signaling, no obvious genre references unless the user explicitly asks for them.

When the off-doctrine flag is set, drop the corridor test and serve the requested register. Maximalist, fashion-coded, music-video-coded — whatever was asked for. Still hold structural quality (sharp anchor rule, dense prose, locked elements list).

## Output format

Output the Visual World document as raw text, ready to paste directly into the Higgsfield Canvas Visual World node. Use the section structure above but do not output the section numbers or labels — flow it as continuous text the way the reference baseline reads.

The structure inside the output should read:

```
VISUAL WORLD / BASELINE
[Opening lock statement]
[Frame contents declaration]
[Anchor rule paragraph]
[Reference image acknowledgment, if applicable]
Visual world (baseline):
[The dense imagined scene paragraph]
Locked elements across all 18 prompts:
[Bulleted list]
```

No markdown formatting in the output itself. No commentary before or after. No measurement counts. Just the document, clean.

If the user asks for multiple Visual World variations from the same direction, number them (Visual World 1, Visual World 2, etc.) with a clear divider between each.

## Writing principles

1. **Imagine fully, don't transcribe.** Even with a reference image, build a scene that goes beyond what's in the photo. The downstream prompts need a world rich enough to generate 18 distinct frames from.
2. **Density over length, but length is required.** The prose paragraph cannot be skimped. Thin baselines produce thin 18-frame outputs.
3. **The anchor rule is the engine.** Spend real thought on it. If you write a weak or vague unifying rule, the entire pipeline output degrades.
4. **Specific over general.** "Sodium-vapor amber" not "warm light." "Volcanic black sand" not "dark sand." "Pitons-of-Saint-Lucia–style twin spires" not "mountains in the distance."
5. **No per-shot framing.** This baseline is read by 18 different prompts at three different shot scales. Don't lock framing decisions that should belong to individual prompts (don't say "the figure stands at center-frame" — there are no figures, and centering belongs to per-shot decisions).
6. **Color grade and finish are non-optional.** Always lock these in both the prose and the bulleted list. They're how the 18 frames stay visually identical in character.
7. **Hold the corridor unless told to break it.** Default is doctrine-aligned. Off-doctrine is opt-in.
