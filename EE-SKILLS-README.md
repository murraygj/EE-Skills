# Emerald Eyes Skill System — Architecture

This folder contains the full skill library for Emerald Eyes (EE). The skills are designed to work both as standalone tools and as a coordinated system orchestrated by `ee-campaign-planner` at the top level.

This README is the single source of truth for how the system fits together. Read it before editing any skill.

---

## The system at a glance

```
                    ┌─────────────────────────────┐
                    │       ee-doctrine           │
                    │  (foundational, read first  │
                    │   by every other skill)     │
                    └──────────────┬──────────────┘
                                   │
                                   ▼
                    ┌─────────────────────────────┐
                    │   ee-campaign-planner       │
                    │   (TOP-LEVEL ORCHESTRATOR)  │
                    │   Fires downstream skills   │
                    │   in package mode           │
                    └──┬───────┬───────┬───────┬──┘
                       │       │       │       │
        ┌──────────────┘       │       │       └──────────────┐
        ▼                      ▼       ▼                      ▼
  ┌──────────┐         ┌──────────────┐  ┌───────────────┐  ┌──────────┐
  │ ee-      │         │ ee-email-sms-│  │ ee-story-post-│  │ ee-blog- │
  │ caption- │         │ planner      │  │ planner       │  │ writer   │
  │ writer   │         │              │  │               │  │          │
  └──────────┘         └──────┬───────┘  └───────────────┘  └──────────┘
                              │
                              ▼
                       ┌──────────────┐
                       │ ee-email-sms │
                       │ (writer)     │
                       └──────────────┘

  ┌──────────────────┐   ┌──────────────┐   ┌──────────────┐
  │ ee-product-      │   │ ee-web-copy  │   │ ee-seo-      │
  │ description      │   │              │   │ strategy     │
  └──────────────────┘   └──────────────┘   └──────────────┘
  (invoked by campaign planner during Conversion phase)
```

---

## The skills

### Foundational

**`ee-doctrine`** — The constitution. Voice rules, the five pillars (Gravity / Clarity / Authority / Humanity / Conversion), consumer tiers (Entry / Core / Inner Circle), corridor philosophy, dual-state discipline, prohibited language, doctrine test ("does this feel inevitable, or does it feel performative?"). **Every other skill reads this first.**

### Top-level orchestrator

**`ee-campaign-planner`** — Plans and structures product launch and collection campaigns. Currently produces campaign architecture documents (phase timing, budget allocation, grid triptych, content production list). **To be upgraded into the full-package orchestrator** that fires downstream skills and produces a complete drafted campaign package on a single invocation.

### Planning skills (one layer below orchestrator)

**`ee-email-sms-planner`** — Plans email/SMS schedules across three cycle modes (between-drops, campaign, post-drop). Outputs schedule + briefs + media recommendations per send. Hands off to `ee-email-sms` for drafting.

**`ee-story-post-planner`** — Plans 5-post Instagram Story batches across three modes (Echo, Extend, Fresh). Outputs sequence plan + 5 prompts + overlay copy + engagement affordances per post.

### Writer skills

**`ee-caption-writer`** — Doctrine-aligned Instagram captions for grid posts. Pillar-aware (different voice per pillar).

**`ee-email-sms`** — Email and SMS marketing copy. Six email types (drop announcement, pre-launch warmup, post-purchase, abandoned cart, doctrine nurture, first-access) plus SMS rules.

**`ee-blog-writer`** — Blog posts for Shopify. Dual purpose: SEO infrastructure + doctrine-aligned reader content.

**`ee-web-copy`** — On-site text (hero, announcement bar, CTAs, meta, alt text, etc.) — everything except product descriptions and blog posts.

**`ee-product-description`** — Product page copy. Shopify product descriptions from image + spec.

### Supporting

**`ee-seo-strategy`** — Keyword research, SEO planning, search intent mapping. Operates upstream of `ee-blog-writer` and `ee-product-description`.

### Production-side skills (separate flow)

**`ee-visual-world-writer`** — Visual World node prompts for the Higgsfield Canvas location pipeline (18-frame baselines).

Plus production-pipeline structural nodes (audited and fixed; not skills themselves — they live in Higgsfield Canvas):
- Location pipeline: SYSTEM_STRUCTURE node + PROMPT_WRITING_GUIDE node + PROMPT_ENHANCEMENT_NODE
- Multi-shot pipeline: MULTI-SHOT_STRUCTURE_NODE + PROMPT_WRITING_GUIDE_MULTI-SHOT + PROMPT_ENHANCEMENT_NODE

---

## Orchestration model

The campaign planner operates in two modes:

### Plan mode (existing behavior)
Produces just the campaign architecture document — phase timeline, content production list, budget allocation, grid triptych plan, email/SMS touchpoint schedule (high-level), key metrics. Output is a planning document, not drafted content.

Use when: the user wants the strategic plan and will execute drafts themselves later (or via separate skill invocations).

### Package mode (to be built)
**Single invocation, full drafted campaign package out.** The campaign planner produces the plan, gets user approval at the appropriate gate, then orchestrates the downstream skills to produce drafted content for the entire campaign:

1. Campaign plan (phase architecture, dates, budget)
2. Email/SMS sequence drafted via `ee-email-sms-planner` → `ee-email-sms`
3. Caption drafts for grid posts via `ee-caption-writer`
4. Story sequences planned via `ee-story-post-planner`
5. Blog post drafts (if applicable) via `ee-blog-writer`
6. Product description (if new piece) via `ee-product-description`
7. Web copy updates (if needed) via `ee-web-copy`

Output is a complete campaign package — ready to schedule, post, and send.

Use when: the user wants the full deliverable in one workflow.

---

## How downstream skills coordinate

Every downstream skill is **invokable standalone** AND **orchestration-aware**. The coordination posture means:

1. When invoked standalone, the skill runs its own direction/approval gates and asks the user for context as needed.
2. When invoked by `ee-campaign-planner` in package mode, the skill receives campaign context (cycle phase, drop details, dates, doctrine pillar weights, target tiers) directly and skips its direction gate — the campaign context replaces it.
3. The skill still runs its approval gate when sensible — e.g., the email planner still shows the schedule plan for approval before drafting. The orchestrator handles consolidated approval flow.

Each skill's "Related skills" section reflects this orchestration relationship.

---

## Cross-reference map

Who references whom (and how):

| Skill | Reads | Hands off to | Invoked by |
|---|---|---|---|
| ee-doctrine | (none — foundational) | (none — referenced by all) | All EE skills |
| ee-campaign-planner | ee-doctrine | All downstream skills in package mode | User directly |
| ee-email-sms-planner | ee-doctrine, ee-email-sms | ee-email-sms (for drafts) | User OR ee-campaign-planner |
| ee-email-sms | ee-doctrine | (none — final output) | User OR ee-email-sms-planner OR ee-campaign-planner |
| ee-story-post-planner | ee-doctrine | (none — produces prompts + plan directly) | User OR ee-campaign-planner |
| ee-caption-writer | ee-doctrine | (none — final output) | User OR ee-campaign-planner |
| ee-blog-writer | ee-doctrine, ee-seo-strategy | (none — final output) | User OR ee-campaign-planner |
| ee-product-description | ee-doctrine, ee-seo-strategy | (none — final output) | User OR ee-campaign-planner |
| ee-web-copy | ee-doctrine | (none — final output) | User OR ee-campaign-planner |
| ee-seo-strategy | ee-doctrine | ee-blog-writer, ee-product-description (provides keyword direction) | User OR ee-campaign-planner OR ee-blog-writer/ee-product-description |
| ee-visual-world-writer | ee-doctrine | (none — output goes to Higgsfield Canvas) | User directly |

---

## Status

| Skill | Status | Notes |
|---|---|---|
| ee-doctrine | ✅ Production | Foundation. Stable. |
| ee-campaign-planner | 🔧 Needs upgrade to orchestrator | Add package mode; explicit downstream skill firing logic |
| ee-email-sms-planner | ✅ New, ready to drop in | Replaces gap between email-sms (writer) and campaign-planner |
| ee-email-sms | ✅ Production | Update Related skills to reflect planner pairing |
| ee-story-post-planner | ✅ New, ready to drop in | 7 sequence shapes, polls/Q&A-weighted affordances |
| ee-caption-writer | ✅ Production | Audit needed: confirm orchestration-aware |
| ee-blog-writer | ✅ Production | Audit needed: confirm orchestration-aware |
| ee-product-description | ✅ Production | Audit needed: confirm orchestration-aware |
| ee-web-copy | ✅ Production | Audit needed: confirm orchestration-aware |
| ee-seo-strategy | ✅ Production | Audit needed: confirm orchestration-aware |
| ee-visual-world-writer | ✅ New, ready to drop in | Standalone — production pipeline, not campaign orchestrator-fired |

---

## Future expansion

**Template library (Claude Design — Phase 2)**
When EE design guidelines are locked, build the email template library in Claude Design. Templates referenced by `ee-email-sms` for HTML rendering. Welcome template, BTS process template, drop announcement template, post-drop template, first-access template, plus reusable design tokens (colors, fonts, spacing, components).

**Production pipeline skills**
The visual world writer is the first of what may become a family of production-side skills (cinematic prompt writer, motion writer, character description writer — many already exist in `/mnt/skills/user/`). Cross-reference here as they get consolidated into the EE library.

---

## Working in this folder

When upgrading any skill:

1. Read this README first
2. Read `ee-doctrine` to confirm voice/posture
3. Read the skill being upgraded + any skills it coordinates with
4. Make changes; preserve the Related skills section as the cross-reference truth
5. If the change affects how the skill coordinates with others, update the cross-reference map in this README
6. Test orchestration end-to-end — invoke the campaign planner in package mode and confirm the full workflow produces a coherent package

When adding a new skill:

1. Define its role: planner / writer / supporting / production
2. Decide if it's invokable by the campaign planner or standalone-only
3. Add it to the system diagram and the cross-reference map
4. Add its Status row
5. Update affected skills' Related skills sections

---

## Doctrine compliance — always

Every skill in this library is a doctrine instrument. The system test:

> "Does this feel inevitable — or does it feel performative?"

Applies at every level: individual sends, individual posts, individual captions, full campaigns, the system itself. When a change to a skill would loosen doctrine for convenience, the change is wrong even if it works mechanically.
