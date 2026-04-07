# MakerWorld Listing Guide

This guide captures the repository conventions for writing MakerWorld model descriptions, README-style docs, customization guides, tags, and media plans.

## 1. What the listing should do

The listing description should read like a sales page first and a technical guide second.

### Suggested order

1. Model title or copy block.
2. Short hook that explains the problem the model solves.
3. Feature bullets.
4. MakerWorld customization steps.
5. Icon, size, or variant options.
6. Compatibility table.
7. Printing recommendations.
8. Troubleshooting and fit notes.
9. License or support note.
10. Tags.

### What to emphasize

- What the model is.
- What it fits.
- Why it is worth printing.
- How to customize it quickly.
- Whether it needs AMS/MMU or supports single-color assembly.
- Any limits, fit notes, or print orientation constraints.

### What to avoid

- Long code explanations that only matter to maintainers.
- Repeating the same print advice in three places.
- Unclear terms like "works great" without a concrete setting or print mode.
- Listing every internal parameter unless it helps the user choose between options.

## 2. What the README or customization guide should do

The README is the technical companion to the listing description.

### Suggested README sections

- Overview
- Compatibility
- Customization reference
- Print modes
- Assembly or installation notes
- Troubleshooting
- File structure
- Changelog or version notes

### Good README behavior

- Explain what the model does without marketing language.
- Document the actual parameter groups users see in OpenSCAD.
- Mention default values that matter for fit or print quality.
- Link to deeper customization docs or listing assets.

## 3. What the listing assets should contain

The repo already treats listing assets as a small package around the public-facing model page.

### Recommended asset set

- Hero image for web.
- App cover for mobile.
- Gallery sequence that explains what the model is, how it prints, and how it is installed.
- Optional GIF or comparison image when the model benefits from motion or side-by-side contrast.
- A PDF customization guide when the model has many parameters.

### Image workflow

Photo setup, framing, cover crops, and editing are better documented in the separate image guide:
- [MakerWorld Image Guide](../makerworld-images/image_guide.md)

Use the listing guide to decide *which* images you need. Use the image guide to decide *how to make* them.

### Practical media order

1. Main hero image.
2. Detail shot.
3. In-use photo.
4. Variant or feature comparison.
5. Installation or assembly steps.
6. GIF if available.

## 4. Tags and metadata

Tags should reflect the real model type and use case.

### Good tag traits

- Match the product family.
- Match the print method or customization style.
- Include the relevant Packout size or part number.
- Avoid filler tags that do not help discovery.

## 5. Suggested file split

- `makerworld_listing/` should hold the main sales copy and media plan.
- `listing_assets/` should hold the guide PDF, photos, and other supporting files.
- `README.md` or a customization guide should document settings in more detail.
