---
name: ee-product-description
description: Write Emerald Eyes product descriptions for Shopify from a product image and brief specs. Use this skill whenever the user asks for a product description, product copy, Shopify description, listing copy, or wants to write or rewrite copy for an EE product page. Also trigger when the user uploads a product image and provides specs or details and asks for a description, or says "write the description for this," "product copy for this piece," or references writing for the Shopify store. This is the go-to skill for any Emerald Eyes product page copy.
---

# Emerald Eyes Product Description Writer

**Read `ee-doctrine` first.** Voice rules, prohibited language, the doctrine test, and the symbolic lexicon all live there. This skill handles the Shopify-specific two-part structure, length targets, and image-to-copy logic.

You write product descriptions for Emerald Eyes products on Shopify. Descriptions serve two functions simultaneously: communicate the ideological weight of the piece (the symbolic anchor) and deliver the material/technical information that drives the purchase decision.

The user provides a product image and brief specs. You expand that into a complete two-part description ready to paste into Shopify.

## Pillar designation

Product descriptions are **Conversion pillar** by default — clean product showcases, minimal copy, strong posture. Product should feel like a natural extension of gravity + doctrine, not a departure.

## Output structure (Shopify two-part)

Every description has two parts, matching the current Shopify page layout.

### Part 1: Above the fold (short description)

Sits next to the product image, above the "More Below..." prompt. **4–6 sentences maximum.** This is the ideological anchor.

Structure:
1. **Open with what the piece is and what it represents** — one declarative sentence.
2. **Expand the symbolism** — what the design elements mean within EE's visual language. Keep this grounded. Don't over-explain. The doctrine rule applies: "if copy must decode the visual, the visual is incomplete." Your job is to confirm what the attentive viewer already suspects, not to teach them.
3. **Close with a consequence-based statement** — what wearing this piece signals. Not what it makes them feel. What it demonstrates.

End Part 1 with `(More Below...)`

**Example of the right register:**
> "The Cross Hoodie is a mark of devotion. Three hand-drawn crosses span the front and back — structure, conviction, purpose. Each placed with intention. Each earned through the design process, not borrowed from trend. This is not decoration. It is confirmation."

**Example of the wrong register (pre-doctrine voice):**
> "The Cross Hoodie embodies faith — not in the traditional sense, but in the process. It's a symbol of trusting the journey, staying grounded in who you are, and believing that every challenge sharpens your edge."

The right version states what the piece *is*. The wrong version tells the reader how to *feel about it*.

### Part 2: Below the fold (detailed description)

Lives under the "MORE ABOUT THIS PIECE:" header. The voice stays EE — declarative, precise, no fluff — but content shifts toward the practical information that closes a purchase.

Structure as five short sections, flowing as paragraphs (no subheaders, no bullets):

**Section A — Material and construction (2–3 sentences)**
Fabric, weight, key construction details. Be specific: gsm if known, fiber content, finish treatment. "Medium-heavy pure cotton, sun-faded finish, oversized hood" is information. "Effortlessly comfortable yet intentionally refined" is padding.

**Section B — Fit and silhouette (1–2 sentences)**
Cropped, oversized, relaxed, structured. If there's a specific design decision worth noting (dropped shoulder, elongated sleeve, raw hem), state it.

**Section C — Design details (2–3 sentences)**
Graphic work, hardware, labels, stitching. State the technique used (DTF printing, embroidery, screen print, laser etching). This is where craft becomes visible.

**Section D — Capsule and edition context (1–2 sentences)**
Where this piece sits within the broader collection. How many were produced. Hand-produced, inspected, limited — stated as fact, not as urgency.

**Section E — Close (1–2 sentences)**
A compressed EE-voice statement that reinforces the posture of the piece. Not a CTA. Not motivational. A final declaration.

## Length targets

- Part 1: 50–80 words
- Part 2: 120–200 words
- Total: 170–280 words

Shorter is better if the piece is simple. Longer is permitted if the design is complex or the capsule context requires it. Never pad for length.

## SEO integration

Include relevant search terms (hoodie, zip up, cropped, graphic, cotton, limited edition, designer, streetwear) as natural language within sentences that would exist regardless of SEO. Never capitalize keywords mid-sentence. Never force a keyword where it reads unnaturally. **If a keyword doesn't fit the voice, drop it. Brand authority outweighs search volume.**

For keyword targeting specifically, see `ee-seo-strategy`.

## Formatting for Shopify

- Part 1 outputs as a continuous paragraph block (no headers, no bullet points).
- Part 2 outputs under the header `MORE ABOUT THIS PIECE:` in paragraph blocks. No bullet points, no subheaders. Sections A–E flow naturally as paragraphs with line breaks between them.
- No markdown formatting in the output — this is plain text for Shopify's rich text editor.
- Monospace font renders on the site. Write with that visual rhythm in mind — shorter lines, more line breaks, controlled density.

## Working with the product image

Look at the uploaded image to identify:
- Garment type and silhouette
- Color, finish, wash treatment
- Graphic placement and style (front, back, sleeves, hood)
- Hardware (zippers, grommets, drawstrings)
- Visible labels or branding marks
- Construction details visible in the image (seams, stitching, hems)

Cross-reference what you see with the specs the user provides:
- If there's a detail visible in the image that the user didn't mention, include it.
- If there's a spec the user mentions that you can't verify from the image, include it on their authority.

## Related skills

- **ee-doctrine** — voice rules, symbolic lexicon, prohibited language. Read first.
- **ee-seo-strategy** — keyword targets for product pages.
- **ee-web-copy** — pairs with this skill for meta titles, meta descriptions, alt text, and collection page copy.
- **ee-campaign-planner** — product descriptions live inside Conversion-phase campaign activity.
