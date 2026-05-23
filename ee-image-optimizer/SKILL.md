---
name: ee-image-optimizer
description: Compress and convert images to web-optimized WebP for the Emerald Eyes Shopify theme WITHOUT washing out color. Use this skill whenever the user wants to optimize, compress, shrink, or convert images for the site, or mentions image weight, page speed from images, "convert to WebP," "compress these," "optimize the lookbook images," washed-out or faded color after conversion, or preparing a theme asset for upload. Also trigger when swapping heavy PNG/JPG theme assets for lighter versions. This is the go-to skill for any Emerald Eyes image optimization. NOT for product/content images uploaded through Shopify admin — those are handled by Shopify's CDN and must not be pre-compressed (see Scope below).
---

# Emerald Eyes Image Optimizer

This skill compresses theme images to WebP while **preserving color**. The whole reason it exists is that the obvious approach — a one-click "convert to WebP" — silently strips the embedded color profile, and on wide-gamut source files that produces the washed-out, desaturated result that has burned this project before (the MultiSZN hero). This skill does it correctly.

## The color rule (read this first)

Washout is almost never WebP's fault and almost never a quality-setting problem. It is a **color profile** problem:

- Images out of Lightroom / Photoshop / the Canon R5 C are often tagged **Adobe RGB** or **Display P3** (wide gamut).
- A naive conversion **drops the profile tag**. The browser then assumes plain sRGB and reinterprets every saturated color flatter — muddy reds, desaturated greens. That is the washout.
- The fix is to **convert the pixels** from the source gamut into sRGB (a real color-space transform), not to discard the tag.

`references/optimize.py` does this automatically: it detects the embedded profile and, if it is wide-gamut, runs a proper `profileToProfile` transform to sRGB before saving. Untagged/sRGB files pass through untouched (safe). The script prints what it did to each file's color so you can verify.

**The single habit that prevents 90% of washout:** export to sRGB at the source. If an image is already sRGB, there is no gamut to mishandle. Wide-gamut only matters for display on the web if you have a specific reason — for a storefront, sRGB is correct.

## Scope — what this skill does and does NOT touch

**DO optimize (theme assets):** files that live in the theme's `assets/` folder and are referenced by filename in Liquid/CSS — backgrounds, hero posters, lookbook stills, marquee imagery, decorative section images. These are rare, you control them, and they should be compressed **before** they enter the theme.

**DO NOT optimize (Shopify-managed images):** product photos, blog images, collection images, or anything uploaded through Shopify admin and rendered via `image_url` / `image_tag` with width parameters. Shopify's CDN already generates correctly-sized, optimized variants per device. Pre-compressing or batch-converting these **fights the CDN** and loses responsive sizing. If those images are slow, the problem is the **theme code requesting the full-res original instead of a sized version** — that is a code audit (look for raw `| image_url` with no width, or `<img>` pointing at originals), not a compression job.

When unsure which bucket an image is in: is it referenced by a fixed filename in the theme code (asset) or pulled from a product/article/collection object (Shopify-managed)? Asset → optimize. Object → leave it, audit the code.

## How to run

```bash
python3 references/optimize.py <files...> [--out DIR] [--quality 85] [--max-edge 1600]
```

Examples:
```bash
# one file
python3 references/optimize.py ./assets/hero-poster.png

# a whole set into an output folder
python3 references/optimize.py ./assets/lookbook-*.png ./assets/lookbook-*.jpg --out ./optimized
```

Requires Pillow (`pip install pillow --break-system-packages -q`).

## Settings and when to change them

- **`--quality 85`** (default): visually lossless for photography. Stay in **82–85**. The earlier washout was NOT caused by quality — do not drop below 80 chasing smaller files; that introduces real artifacts on top of any color issue.
- **`--max-edge 1600`** (default): caps the longest edge. Hero/lookbook/background display rarely needs more than ~1600px even on retina, and uncapped exports are most of the bloat. Raise it (e.g. 2000) only for a full-bleed asset that must stay razor-sharp on large desktop. Set `0` to disable resizing entirely (keep native dimensions).
- Expect **~85–90% size reduction** on typical uncompressed PNG/JPG theme assets.

## Verifying color held (do this on wide-gamut conversions)

For any file the script reports as `converted ... -> sRGB`, eyeball it before shipping — that is the category that can go wrong. Generate a side-by-side:

```python
from PIL import Image
a = Image.open("assets/source.jpg").convert("RGB")
b = Image.open("optimized/source.webp").convert("RGB")
h = 500
a = a.resize((int(a.width*h/a.height), h)); b = b.resize((int(b.width*h/b.height), h))
c = Image.new("RGB", (a.width+b.width+20, h), "white")
c.paste(a,(0,0)); c.paste(b,(a.width+20,0)); c.save("compare.png")
```
Saturated reds, volt greens, oranges, and clean whites are the tells. If those held, the conversion is good. Untagged/sRGB files do not need this check.

## Swapping assets into the theme

After conversion, the theme references must point at the new `.webp` files:

1. Place the `.webp` files in `assets/`.
2. Update every reference to the old filename — search the theme for the old name (`grep -rn "source.png" sections/ snippets/ assets/*.liquid layout/`) and replace with the `.webp` filename. References appear as `'name.png' | asset_url`, in `asset_img_url`, and inside `.liquid` CSS files.
3. Leave the old originals in place until the swap is verified rendering, then remove them to drop the weight.
4. Confirm nothing still points at the old file before deleting it.

## Gotchas

- **Animated GIFs:** this script flattens to a single frame. Do not run it on animated assets.
- **Transparency:** PNGs with real transparency are flattened to RGB (alpha dropped) for photo WebP. If an asset genuinely needs transparency (a logo over varied backgrounds), pass `--max-edge 0`, and convert with alpha preserved manually — most theme *photos* do not need it, but logos/marks do.
- **Logos and flat graphics:** WebP at q85 is for photographs. Hard-edged logos, the EE mark, and flat-color graphics are often better left as optimized PNG or SVG — WebP can soften crisp edges. Judge per asset.
- **"c2ci" or unreadable profile names:** the script keeps these as-is rather than guessing. If such a file looks off, re-export it from source as sRGB and reconvert.
