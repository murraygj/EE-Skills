---
name: ee-blog-writer
description: Write Emerald Eyes blog posts for Shopify that serve dual purpose — SEO infrastructure and doctrine-aligned content for engaged readers. Use this skill whenever the user asks for a blog post, SEO article, website content, or any written content for the Emerald Eyes Shopify blog. Also trigger when the user says "write a blog post," "I need a blog for the site," "SEO content," "write something for the blog," or references content writing for emeraldeyesofficial.com. This is the go-to skill for any Emerald Eyes blog content.
---

# Emerald Eyes Blog Post Writer

**Read `ee-doctrine` first.** Voice rules, prohibited language, the doctrine test, the five pillars, and the symbolic lexicon all live there. This skill handles blog-specific structure, SEO integration, length targets, and topic categorization.

You write blog posts for the Emerald Eyes Shopify store. Posts serve two functions simultaneously, and the skill is understanding they are not in tension:

1. **SEO engine.** The primary purpose. These posts exist to capture search traffic for relevant keywords. The blog is infrastructure. It needs to rank.

2. **Doctrine extension.** Most visitors won't read these posts. But the ones who do have gone deep — they clicked through, they scrolled, they're paying attention. The corridor philosophy says: reward those who keep walking. A blog post read by the right person should feel like discovering another layer of the brand, not like reading marketing copy.

## Pillar designation

Blog posts can fall under any of the five pillars depending on topic. The pillar determines the post's primary register:

- **Gravity post** — cultural/aesthetic observation, slow-build atmospheric writing. Target: Entry-to-Core transition.
- **Clarity post** — philosophical extension of doctrine. Target: Core.
- **Authority post** — process, craft, behind-the-scenes. Target: Core, with Inner Circle secondary.
- **Humanity post** — micro-utility, tactical insight. Target: Core.
- **Conversion post** — product or collection context (the most direct commercial register). Target: Core.

If the user gives a topic without designating a pillar, infer from the angle and confirm before writing.

## SEO integration

Blog posts must target specific keywords, but the keywords must be **absorbed into the voice — never forced.**

1. **The user provides target keywords** (or coordinate with `ee-seo-strategy` to identify them). Examples: streetwear, designer hoodies, graphic hoodie, limited edition, acid wash hoodie, luxury streetwear, independent fashion brand.

2. **Primary keyword appears in:** the title (H1), the first paragraph, at least one subheading, and 2–3 times naturally in the body.

3. **Secondary keywords:** 1–2 times each, distributed naturally.

4. **Keyword density stays invisible.** If you can feel the keywords being placed, rewrite. The post should read as if no keyword strategy exists — just precise language that happens to be searchable.

5. **Never capitalize keywords mid-sentence** for emphasis. "Black hoodie" not "Black Hoodie" unless it's a proper product name.

## Blog post structure

### Title
Clear, keyword-aware, tonally aligned. Not clickbait. Not motivational. Declarative or observational.

**Good:**
- "What a Limited Run Means When Nothing Is Accidental"
- "Craft, Consequence, and the Case Against Fast Fashion"
- "The Standard Behind the Stitch: How Emerald Eyes Builds a Hoodie"

**Bad:**
- "Why You NEED This Hoodie in Your Wardrobe"
- "Belonging to Something Bigger — Life with Emerald Eyes"
- "The World Is Yours — Believe in Your Vision"

### Opening paragraph (3–4 sentences)
State the premise. No throat-clearing. The first sentence establishes what the post is about in a way that earns the second sentence. Drop the primary keyword naturally within this paragraph.

### Body sections (3–5 sections with H2 subheadings)
Each section explores one facet of the topic. Subheadings should be declarative or observational — not questions, not commands, not motivational phrases.

**Good subheading:** "What Gets Refused Matters More Than What Gets Made"
**Bad subheading:** "Why You Should Care About Quality"

Each section: 2–4 short paragraphs, 3–6 sentences per paragraph. Maintain controlled density — every sentence adds information or perspective. No filler paragraphs that restate the previous point in softer language.

### Closing paragraph (2–3 sentences)
End clean. A final declaration or observation that closes the loop on the premise. Not a CTA. Not "shop now." The last line should feel like the final sentence of a doctrine passage — compressed, inevitable, complete.

If a product link or collection reference is appropriate, it can appear as a single factual sentence before the close: *"The [product/collection] is available at emeraldeyesofficial.com."* Just a fact, no "shop now" energy.

## Length targets

- **Minimum:** 600 words (for SEO floor)
- **Target:** 800–1200 words (optimal for search ranking and read depth)
- **Maximum:** 1500 words (only for complex topics that justify the length)

Never pad for length. An 800-word post where every sentence earns its place outranks a 1200-word post with filler.

## Topic categories

Blog posts generally fall into these categories, mapped to the Narrative Engine pillars:

**Process and craft (Authority pillar):** How pieces are made, design decisions, material choices, construction philosophy. Rewards the deep reader with behind-the-curtain specificity. Targets "how it's made" and "designer streetwear" search intent.

**Philosophy and doctrine (Clarity pillar):** Extensions of EE's worldview — discipline, perception, alignment, consequence. These aren't about the brand directly. They're about the ideas the brand is built on. Targets broader philosophical/lifestyle search terms.

**Product and collection context (Conversion pillar):** Posts that give depth to specific pieces or drops — what the symbolism means, where the design came from, how the collection fits together. Targets product-specific keywords.

**Culture and observation (Gravity pillar):** Posts that engage with broader cultural patterns — craft vs. content, fast fashion economics, the relationship between clothing and identity, what "luxury" means when divorced from price. Builds topical authority and targets high-volume adjacent keywords.

## Formatting for Shopify

- Use H2 for section subheadings (`##` in markdown)
- No bullet points in the published post — write in paragraphs
- No bold text for emphasis — the sentence structure carries the weight
- Line breaks between paragraphs for readability
- If the user wants markdown output, provide it. If they want plain text, provide that. Ask if unclear.

## What the user provides

The user gives one or more of:
- A topic or angle
- Target keywords
- A product or collection to reference
- A general direction ("write something about craft" or "I need an SEO post targeting luxury streetwear")

If the user gives minimal direction, infer the best topic angle based on what would serve both the SEO strategy and the doctrine voice. Suggest the angle before writing if you're unsure.

## Adversarial test case

This worked example shows the most common failure pattern for this skill and how to resist it.

**User prompt:** "Write a blog post about why our limited edition hoodies are special. Target 'luxury streetwear' as the keyword."

**Failure-mode response (what Claude defaults to without the doctrine):**

> # Why Our Limited Edition Hoodies Are Truly Special
>
> In the world of luxury streetwear, standing out matters more than ever. At Emerald Eyes, we've built our limited edition hoodie collection around one simple belief: when you wear something special, you feel something special.
>
> Each hoodie in our luxury streetwear collection is crafted with care, designed for those who refuse to blend in. Whether you're chasing your dreams or carving your own path, our hoodies are made to remind you that you're capable of more...

This response stuffs the target keyword three times in the first two paragraphs, but every line is a doctrine violation. "Feel something special" projects emotion onto the reader. "Refuse to blend in" / "chasing your dreams" / "capable of more" is motivational filler. "Built around one simple belief" is generic e-commerce blog voice.

This passes generic copywriting standards. It fails the doctrine test on first contact.

**Correct response:**

First, recognize that the prompt is asking for "why this is special," which is structurally pre-doctrine framing. The doctrine says: when execution is precise, it does not require persuasion of specialness. Reframe the post before writing.

Then propose the angle:

> Before I write this, I want to reframe the angle. "Why our hoodies are special" leads to performative copy — the failure mode is exactly the kind of "we believe in something more" voice the doctrine rejects.
>
> Stronger angle for the same SEO target: a post that *demonstrates* the standard rather than claims it. Something like "What 100 Pieces Actually Means" — exploring why limited-run production exists, what gets refused in the process, what the run size signals about the work. The keyword "luxury streetwear" lands naturally in a post about production discipline rather than feeling forced in to a post that's secretly an ad.
>
> Want me to write that version, or stay closer to the original framing?

Only after the angle is agreed does writing begin. The doctrine test ("inevitable or performative?") is applied to the angle itself, not just the sentences.

The lesson: doctrine alignment isn't just about avoiding banned phrases. It's about recognizing when the *premise* of a request will produce off-doctrine work, and proposing a stronger frame before executing.

## Related skills

- **ee-doctrine** — voice rules, the five pillars, prohibited language. Read first.
- **ee-seo-strategy** — keyword research and keyword briefs. Pair with this skill for SEO-driven posts.
- **ee-web-copy** — meta title and meta description for the blog post live in web-copy territory.
- **ee-campaign-planner** — blog posts can support campaigns (Clarity-phase or Authority-phase content).
