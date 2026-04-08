# MakerWorld OpenSCAD Guide

Use this guide when preparing OpenSCAD source files specifically for MakerWorld upload. For general OpenSCAD structure and maintainability, see [OpenSCAD Authoring Guide](../openscad-authoring/authoring_guide.md).

## Scope

This guide covers MakerWorld-specific export and upload behavior only.

- Bundled upload files
- Multi-plate 3MF export
- Multi-color export
- User-uploaded files

## Bundled Upload File

For MakerWorld upload, use the bundled version rather than the raw source tree.

### Bundle rules

- Inline local project includes so the upload is self-contained.
- Keep external library references only when they are intentionally shared dependencies.
- Preserve hidden calculations and helper code after the visible Customizer fields.
- Write the bundled output into a `build/` folder next to the source file.

### Practical rule

- `source.scad` is for editing.
- `*_bundled.scad` is for uploading.

## Multi-Plate 3MF

Only use the multi-plate `mw_plate_N()` pattern when the model is intentionally split across multiple build plates.

### Required pattern

- Use modules named `mw_plate_1()`, `mw_plate_2()`, and so on.
- Keep each plate focused on the parts that belong together.
- Use an optional `mw_assembly_view()` module for the assembled preview.
- Treat the assembly view as the presentation layer and the plate modules as the export layer.

### Practical guidance

- If the model is confusing when viewed as separate plates, provide a clear assembly preview.
- If a model needs both multi-plate 3MF export and STL export, prefer separate scripts instead of trying to make one file do both jobs.
- If a plate layout changes frequently, keep the assembly preview easy to read so users can verify the design before exporting.
- Do not use the multi-plate syntax for regular single-plate models.

## Multi-Color Export

MakerWorld's Parametric Model Maker can export color information when the OpenSCAD source uses `color()` in a normal, explicit way.

### Color rules

- Use `color()` around the geometry that should carry the exported color.
- When exposing a color as a user parameter, keep it as a hex string.
- Mark color parameters with `// color` so the MakerWorld UI recognizes them.
- Prefer simple, direct color definitions over clever abstractions when the goal is export reliability.
- Make the colored geometry part of the top-level emitted model when you want it to survive into the exported 3MF as a distinct colored object.
- Use helper modules for code reuse, but call the color-bearing geometry from top-level export modules or top-level objects.

### Practical guidance

- Use color parameters when the user should be able to customize appearance without editing the source.
- Use fixed colors when the color is part of the model's internal logic or preview clarity.
- If colorized geometry overlaps with cut or difference operations, check that the export still behaves as intended in the slicer.
- If a colored part is only buried inside a reusable helper and never emitted as its own top-level object, treat that as a likely export risk.

## User-Uploaded Files

If the model needs a user-provided image, vector, or mesh, define the file as a variable in the source so MakerWorld can expose an upload control.

### Supported file patterns

- Use `default.png` for image inputs.
- Use `default.svg` for vector inputs.
- Use `default.stl` for mesh inputs.
- Bind the file path to a variable first, then pass that variable into `surface()` or `import()`.

### Practical guidance

- Keep file-dependent transforms obvious so users can understand how the uploaded asset is being placed or scaled.
- If the model depends on a default asset to look correct, document that dependency clearly in the listing or README.
- Treat user-uploaded files as part of the model interface, not as hidden implementation details.

## Publish Checklist

- The `.scad` file opens cleanly in OpenSCAD.
- The Customizer sections are grouped logically.
- The bundled upload file exists in `build/`.
- The upload file still exposes the same visible controls as the source.
- The print recommendations in any companion doc match the actual geometry and orientation.
- Multi-plate files use `mw_plate_N()` names and an optional `mw_assembly_view()` when needed.
- If STL export matters, there is a separate STL-oriented script or workflow.
- Color parameters are declared as hex strings with `// color` comments when they should be user-editable.
- `color()` is applied explicitly where color should survive into the exported model.
- User-uploaded file inputs use `default.png`, `default.svg`, or `default.stl` as the default file names when applicable.

## Repo Pattern

This repository currently follows a simple pattern:

- `scad/.../*.scad` is the editable source.
- `scad/.../build/*_bundled.scad` is the upload-ready file.
- Shared geometry or icon helpers live under `scad/lib/`.
- Model-specific docs and media live beside the model they support.
