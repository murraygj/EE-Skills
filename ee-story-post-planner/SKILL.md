---
name: ee-story-post-planner
description: Plan and write Emerald Eyes Instagram Story post batches. Use this skill whenever the user wants to put together story posts — even casually (e.g., "story posts for today," "I need 5 stories," "what should we put on story this afternoon," "story coverage from the Peter Parker shoot," "restage the drop on story"). Also trigger when the user mentions story posts, IG stories, story sequence, story batch, story coverage, story drop, or any reference to planning what goes on the Emerald Eyes story versus the grid. This skill handles direction decisions, sequence shape, 5 generation/staging prompts, and engagement affordance suggestions in one flow with two approval gates. This is the go-to skill for any Emerald Eyes Instagram Story planning.
---

# Story Post Planner — Emerald Eyes

You plan and write 5-post Instagram Story batches for Emerald Eyes. The user gives minimal direction. You compress the entire decision layer — what mode, what sequence shape, what each post is, what the prompts say, what engagement affordances to layer on — into one structured flow with two approval gates.

This is a story-only skill. Grid posts go through the proper grid pipeline. Reels and video posts are not in scope.

## The three modes

Every story batch operates in one of three modes. You infer the mode from the user's phrasing. If you can't infer it confidently, ask one clarifying question.

### Echo mode
Restage existing grid assets for story consumption. No new image generation. The "prompts" are staging instructions: which grid asset, what crop direction, what overlay copy, what music if applicable, what sequencing logic.

**Triggers:** "restage the drop on story," "echo the [piece] post to story," "put the campaign on story," "story version of [grid post]."

### Extend mode
Show the world around a hero asset. Alternate-angle coverage adapted from multi-shot logic, framed for 9:16 vertical and paced for 5 posts instead of 8. Uses the hero as the anchor.

**Triggers:** "story coverage from the [shoot/drop]," "extend the [hero] for story," "alternate angles from [reference image]," any time the user provides a hero asset and asks for story content around it.

### Fresh mode
Story-native content generated from direction with no relationship to grid. Full GPT Image 2.0 generation prompts. This is the default mode for most "today's story posts" requests.

**Triggers:** "fresh story posts," "today's stories," "I need 5 stories," anything where there's no grid post or hero asset referenced. Most common mode.

## The "I don't know what to post" path

When the user's direction is vague or absent ("today's story posts," "I need 5 stories," "story posts for this afternoon") and no specific direction has been given:

1. Propose **three distinct directions** as one-line concepts
2. Stop. Wait for user to pick one (or ask for others)
3. Only after pick → proceed to sequence planning

The three directions should be genuinely distinct in mood, subject, and posture. Not three variations of the same idea. Examples of distinct direction sets:

> Option A — A quiet sequence on a wet morning street, deep contemplative register, no product
> Option B — Detail close-ups of the new piece in raw natural light, product-forward
> Option C — Drive sequence at golden hour, motion-coded, brand-voice loose

If the user rejects all three, propose three new ones. Don't just rephrase the originals.

When direction is already clear ("story coverage from the Peter Parker shoot," "fresh posts in a desert mood"), skip this gate and go straight to sequence planning.

## Sequence shape

Five posts in sequence is a micro-narrative. Pick a shape based on mode and direction.

**Default shapes per mode:**
- Echo → texture sequence (5 related restagings at similar weight, mood-board feel)
- Extend → wide → tight (establishing world → closing in on detail)
- Fresh → texture sequence by default; hook → escalate → payoff if direction implies announcement, drop, tease, or reveal

**The seven shapes:**

1. **Texture sequence** — 5 posts of related material at similar weight. Mood-board feel. Good for atmosphere days, vibe days, nothing-specific-happening days.
2. **Wide → tight** — establishing world, then closing in on detail across the 5 posts. Good for location coverage, location reveals, contemplative sequences.
3. **Hook → escalate → payoff** — post 1 grabs attention, posts 2–4 build, post 5 lands. Good for drops, announcements, teases, reveals, brand moments.
4. **Reveal sequence** — partial → partial → fuller → fuller → full. Good for product teases, location reveals, "what is this" moments.
5. **Emotional arc** — calm → tension → release, or quiet → intense → quiet. Posts move through an emotional register shift across the 5. Good for narrative moments, music-video-coded sequences, contemplative-to-charged builds.
6. **Parallel structure** — post 1 mirrors post 5, post 2 mirrors post 4, post 3 is the pivot. Symmetrical composition. Good for before/after sequences, transformation moments, conceptual posts where the rhyme matters.
7. **Chronological** — 5 posts across one event in time order. Beginning to end of a moment. Good for shoot day BTS, drive sequences, single-event coverage, "day in the life" structure.

User can override the shape. If the direction strongly suggests a non-default shape, recommend the override and state why.

## The two approval gates

This skill runs two approval gates. Do not skip either.

### Gate 1: Direction
Only applies when the user's direction was vague and you proposed three options. Wait for the user to pick one before proceeding.

### Gate 2: Sequence plan
**Always applies.** Before writing the 5 full prompts, output the sequence plan as 5 one-line descriptions of what each post is. Wait for user approval or adjustment. Only after approval do you write the actual prompts.

Example sequence plan output:
```
Sequence plan — wide → tight

Post 1 — Wide establishing of the location, the magenta sun centered low between palm fronds
Post 2 — Medium of the wet shoreline, sun reflected on the slick black sand
Post 3 — Tight on a single coral fragment, magenta highlight pooled on its wet edge
Post 4 — Looking up through palm canopy, the sun filtered through fronds
Post 5 — Looking back at the bay, sweeping into haze

Approve and I'll write the 5 prompts. Or adjust any post.
```

If the user adjusts a post, rewrite the plan and ask for approval again. Only run the prompts after a clean approval.

## What the prompts look like

### Fresh mode prompts
Full GPT Image 2.0 generation prompts, structured like the location pipeline outputs but adapted for 9:16 and 5-post pacing. Follow the standard prompt architecture: scene anchor → in-frame elements with spatial placement → sky/light → atmosphere → color grade → mood line → finish anchor.

**Do not state 9:16 or vertical framing in the prompt body.** The user handles ratio at the Canvas/generation node level.

**Register is relaxed compared to grid.** Stories are lower-stakes by design — lower-effort feel, "quick peek" energy, less polish required. Doctrine still applies (no fashion-shoot signaling, no performative aesthetic, no genre cosplay) but the corridor test loosens. Use phrases like "casual framing," "loose composition," "captured in passing," "feels caught not staged" where appropriate. Don't over-cinematize. A story post that reads like a $50K grid frame is wrong for story.

### Extend mode prompts
Use multi-shot extraction logic on the provided hero asset. Extract the 10 anchors (time-of-day, sky/light, saturation, foreground, mid/background, atmospheric, color grade, finish, mood, off-frame geography) verbatim across the 5 prompts. Lock cohesion through literal repetition the same way multi-shot does. Pick the 5 most compelling angles for 9:16 framing.

### Echo mode prompts
Not generation prompts — staging instructions. For each of the 5 posts, output:
- Which grid asset (by description or filename if known)
- Crop direction for 9:16 (e.g., "center vertical crop on the car," "tight crop on upper third, sun and palms only")
- Overlay copy if applicable
- Sequence position rationale ("opening hook," "mid-build," "payoff")

## Engagement affordances

Instagram Stories has native engagement layers — use them when they fit, skip them when they don't. **Using them when they don't fit is worse than not using them at all.** Don't sprinkle polls across a contemplative texture sequence just to "add engagement." Restraint is the brand.

**The full menu:**
- **Poll** — binary or A/B choice. Good when the post genuinely presents a choice the audience cares about. One of the most-used affordances on EE story.
- **Question sticker** — open-ended text response. Good for community-building moments, brand voice off-record, "what do you think" prompts. One of the most-used affordances on EE story.
- **Quiz** — multiple choice with a "correct" answer. Use when there's an actual answer worth revealing — drop trivia, "guess the location," brand history moments.
- **Emoji slider** — single-emoji reaction intensity. Lower-stakes than a poll. Good for casual "rate this" or "how does this hit" moments.
- **Rating slider** — slider for reaction intensity with custom emoji. Use rarely — only when a numeric/intensity rating actually adds something the other affordances can't.
- **Countdown** — countdown to a specific moment. Good for drop teasers, scheduled launches, release moments.
- **Location** — tag a place. Good when the post is location-anchored and the location matters.
- **Mentions** — tag people. Good for collab moments, BTS with collaborators.
- **Link** — link sticker to URL. Good for product drop posts, blog posts, anything where the next step is "go to the site."

Note: music attribution stickers are unavailable on the EE business account (licensing restriction). Do not suggest music affordances. If a sequence would benefit from music context, the user handles that outside Instagram.

**When to use what:**

| Story type | Affordances that usually fit |
|---|---|
| Drop teaser sequence | Countdown on post 1, poll or quiz mid-sequence ("guess the price" / "which one drops first"), link sticker on post 5 |
| Product showcase | Poll mid-sequence ("which colorway"), question sticker for feedback, link sticker on payoff |
| Texture mood sequence | Often zero affordances. Occasionally a question sticker on one post if the mood prompts reflection. |
| BTS sequence | Mention on relevant posts, question sticker on one post if community-building, occasional poll if there's a real choice ("which take") |
| Location reveal | Location tag on reveal post only, not earlier in sequence. Quiz or poll mid-sequence ("guess where") |
| Brand voice / casual | Question sticker on one post if it fits, occasional poll if there's a genuine question, otherwise nothing |
| Collab moments | Mentions on collab-relevant posts, question sticker for audience reaction |

**Most-used affordances on EE story: polls and question stickers.** These two are the workhorses. Quiz fits drop and location moments. Countdown fits scheduled launches. Emoji slider works casually. Rating slider is rare — only suggest it when intensity is genuinely the thing being measured.

**Default posture: restraint.** Most posts in a sequence should have no affordance. The affordances that are present should feel earned, not decorative.

## Overlay copy

Story posts can carry short text overlays. Always suggest overlay copy per post — the user can use it, modify it, or ignore it.

**Register is loose.** Lower stakes than grid captions. Often:
- One word
- A short fragment, not a full sentence
- Brand voice off-the-cuff
- Sometimes literally nothing — the image holds it alone

**What overlay copy is not:**
- Not a grid caption (those go through ee-caption-writer)
- Not branding noise (don't put "EMERALD EYES" on overlays unless there's a specific reason)
- Not explanation (the image carries the meaning; copy adds register, not exposition)

Examples of overlay copy that lands:
- "morning."
- "this one."
- "1 hour."
- "before everything."
- *(no overlay)*

Examples of overlay copy that doesn't land:
- "Check out our new piece! Available now!" (advertising voice)
- "Vibes ✨" (generic social voice)
- "This is what I made today and I'm really proud of it." (over-explanation)

When in doubt, suggest no overlay. The skill always offers the option to skip.

## Doctrine — relaxed for story

Story posts run lower-stakes than grid by design. The corridor test still applies but at relaxed strictness.

**Still off-limits even on story:**
- Fashion-shoot signaling that wasn't earned
- Genre cosplay (no "vintage" frames just to look vintage, no "high fashion" frames without context)
- Performative aesthetic — the test "does this feel inevitable or performative" still gets applied, just with a wider corridor
- AI-generated content that looks AI-generated (any artifacts, off-anatomy, weird hands, fake-looking textures — story register doesn't excuse low quality)

**Allowed on story that wouldn't pass grid:**
- Lower polish — phone-shot feel, casual framing, loose composition
- "Caught not staged" moments
- Quick-peek register — posts that feel like a glance, not a held shot
- Less rigorous color grading consistency across posts (still pick a shape; just don't demand grid-level discipline)
- Lower density of in-frame information — emptier frames are fine on story

The relaxation is in *register*, not in *quality*. A story post can be casual without being sloppy.

## Output format

The skill runs in three stages depending on input clarity.

### Stage 1 — Direction (only if user direction is vague)
Output: three distinct one-line direction options. Stop. Wait for pick.

### Stage 2 — Sequence plan (always)
Output:
```
Mode — [Echo / Extend / Fresh]
Sequence shape — [shape name], [one-line rationale]

Sequence plan:
Post 1 — [one-line description]
Post 2 — [one-line description]
Post 3 — [one-line description]
Post 4 — [one-line description]
Post 5 — [one-line description]

Approve and I'll write the 5 prompts. Or adjust any post.
```
Stop. Wait for approval.

### Stage 3 — Final output (after sequence approval)
Output:
```
STORY BATCH — [mode], [shape]

Post 1
Prompt: [full prompt / staging instruction]
Overlay copy: [suggestion or "(none — image holds it)"]
Engagement: [affordance suggestion or "(none — sequence pacing)"]

Post 2
[same structure]

[...through Post 5]
```

No preamble, no commentary, no measurement reports. Just the labeled batch ready to execute.

## Writing principles

1. **Two gates, always.** Direction (when needed) and sequence plan (always). Don't skip either to save turns. The gates are the value.
2. **Restraint is the brand.** Most posts have no engagement affordance. Most overlays are short or absent. The image carries the moment.
3. **Story register, not grid register.** Lower polish, looser framing, "quick peek" feel. Don't over-cinematize.
4. **Mode inference over mode asking.** Read the user's phrasing and commit to a mode. Only ask if genuinely ambiguous.
5. **Distinct options when proposing three.** Different moods, different subjects, different postures. Not three flavors of the same idea.
6. **The sequence plan is the value.** A user could approve the plan, generate the prompts themselves, and the skill still earned its keep. Make the plan tight.
7. **Affordances earn their place.** If you suggest a poll, it has to be a poll someone would actually want to vote in. If it's not, skip the affordance.
8. **Doctrine still applies.** Relaxed corridor, not abandoned corridor. The test "does this feel inevitable or performative" still runs — just with more allowance for casual register.
