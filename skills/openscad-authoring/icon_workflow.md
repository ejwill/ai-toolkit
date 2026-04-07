# OpenSCAD Tool Icon Workflow

Use this workflow when turning a product photo or stylized icon reference into a reusable OpenSCAD icon module.

## Goal

Produce an icon that:

- reads clearly at small latch or label scale
- uses deliberate stylization rather than literal photo tracing
- can be split into print-friendly color regions
- is validated as a standalone draft before entering the shared icon library

## Icon Model

For latch-style graphics, think in printable layers only:

- `white`: the white border or stroke region
- `red`: the red highlight regions

Optional:

- `cutouts`: small negative details if they still read at print size
- `guide`: a temporary black silhouette used during drafting only

The final icon should usually be driven by 2D modules, not imported art. In the final latch model, black is typically just the exposed latch body.

## Source Hierarchy

Use sources in this order:

1. Stylized icon reference if one exists
2. Real product photo for recognition cues
3. Existing repo icons for proportion, stroke weight, and simplification style

Do not try to reproduce every product detail. Match the icon language, not the photo.

## Simplification Rules

- Start with the outer silhouette first, but treat it as a guide rather than a final printed layer.
- Keep the shape upright or horizontal at first. Rotation can be applied later.
- Use 3 to 6 accent islands max.
- Remove logos, tiny vents, teeth, and secondary bevels unless they still read at small scale.
- Avoid thin unsupported slivers and very small detached islands.
- Prefer bold proportions and recognizable landmarks over exact geometry.

## Geometry Strategy

Build icons from simple OpenSCAD-friendly primitives:

- `hull()` between circles for soft product contours
- `polygon()` for sharp panels and accent fields
- `difference()` for trigger openings or major negative spaces
- `offset()` for derived outline rings

Good pattern:

```scad
module icon_example_white(size) { ... }
module icon_example_red(size) { ... }
```

## Repeatable Authoring Steps

1. Choose one reference image and crop mentally to the tool only.
2. Identify 3 to 5 recognition landmarks.
3. Sketch the outer silhouette in OpenSCAD as a guide.
4. Generate the white layer from that guide or draw it directly.
5. Add the largest red accent regions.
6. Add one or two negative details only if they survive reduction.
7. Preview at large size.
8. Preview again at actual target size.
9. Reject or simplify anything that turns muddy.
10. Only after that, move the icon into the shared library.

## Validation Checklist

Validate each draft standalone before integration:

- The white layer reads clearly on its own.
- The accent layer still reads when rendered small.
- The outline thickness looks balanced relative to the tool size.
- No tiny floating islands are likely to fail in printing.
- The icon looks correct at both preview size and real use size.
- The icon still looks acceptable when rotated later.

## Recommended Draft File Shape

- Create draft icons in `scad/assets/` first.
- Include a `preview_size` parameter.
- Include booleans for showing a black guide, white layer, and red layer.
- End with a single preview module call.

Once approved:

- move the final white/red modules into the shared library or layered icon set
- keep any draft-only black guide module out of the shared library when possible
- keep failed or exploratory drafts out of the shared library

## Prompt Template

Use this prompt when asking an LLM to generate or refine an icon:

```text
Create a standalone OpenSCAD draft icon module for a stylized tool graphic.

Target style:
- bold product-icon silhouette, not a literal photo trace
- suitable for a small Milwaukee latch or label
- black latch body with white and red inlay regions
- clean, simplified, recognizable

Requirements:
- do not rotate the icon unless asked
- create separate 2D modules for white and red printable regions
- you may use a temporary black guide silhouette during drafting, but the final icon definition should focus on white and red layers
- use hulls, circles, polygons, and simple differences
- avoid tiny isolated islands and micro-detail
- keep the result readable at small size

Output:
- one standalone .scad draft file
- preview controls for show_guide, show_white, and show_red
- modules named icon_<name>_white and icon_<name>_red
- one preview module call at the bottom

Reference priorities:
1. match the stylized icon language first
2. preserve only the most recognizable features from the real product
3. simplify aggressively for printability
```

## Review Standard

If the output does not match the stylized icon language, reject it and revise. A technically valid OpenSCAD file is not enough if the icon does not read correctly.
