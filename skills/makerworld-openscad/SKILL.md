---
name: makerworld-openscad
description: MakerWorld-specific OpenSCAD export rules including bundled upload files, multi-plate 3MF export, multi-color export, and user-uploaded files. Use when preparing OpenSCAD files for MakerWorld.
---

# MakerWorld OpenSCAD

## When to use

Use this skill when preparing OpenSCAD files for MakerWorld upload or export, especially for bundled SCAD files, 3MF plate exports, color export, and uploaded asset inputs.

## Workflow

1. Verify the model can be bundled cleanly.
2. Check whether the model is single-plate or intentionally multi-plate.
3. Confirm color and file-input behavior only where MakerWorld supports it.
4. Keep export-specific rules separate from general OpenSCAD structure.

## Core Rules

- Use the bundled SCAD for upload, not the raw source tree.
- Use multi-plate `mw_plate_N()` modules only when the model is intentionally split across multiple build plates.
- Use `mw_assembly_view()` only when you need a clearer assembled preview.
- Keep color export explicit with `color()` and user-editable hex color parameters.
- Use `default.png`, `default.svg`, or `default.stl` for user-uploaded files when exposing an upload control.
- Keep MakerWorld-specific export behavior out of the general OpenSCAD authoring rules.

## Common Checks

- Bundled output exists in `build/`.
- Single-plate models do not use multi-plate syntax.
- Multi-plate models have a clear plate-by-plate layout.
- Colorized parts are emitted in a way the exporter can preserve.
- File inputs are wired to a variable and documented clearly.

## Reference

See [MakerWorld OpenSCAD Guide](openscad_guide.md).
