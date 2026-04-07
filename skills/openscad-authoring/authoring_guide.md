# OpenSCAD Authoring Guide

Use this guide for general OpenSCAD model structure, independent of any upload platform.

## Authoring Checklist

- Start with a short banner comment that names the model, author, version, and license.
- Keep all `include` statements near the top.
- Group user-facing parameters into clear Customizer sections.
- Put derived values, helper functions, and calculations in a hidden section.
- End the file with one clear render entrypoint, usually a single module call.
- Keep external dependencies minimal and explicit.
- Make file inputs, color inputs, and export intent obvious in the source.

## Source File Shape

The source `.scad` file should be easy to customize in OpenSCAD and easy to maintain later.

### Suggested sections

- `Main Settings`
- `Text Design`
- `Icon Design`
- `Custom Icon & Emoji`
- `Handle Design`
- `Print Tuning`
- `Advanced`
- `Hidden`

### Good habits

- Use MakerWorld-friendly Customizer comments like `/* [Section] */` and inline option lists.
- Keep parameter names stable between versions when possible.
- Put print-critical settings near the top of each group.
- Avoid burying export behavior inside long procedural chains.
- If a file needs assets such as custom SVGs, note that dependency in comments.

### User expectation

- The model opens cleanly in OpenSCAD.
- The key settings are obvious in the Customizer.
- The visible UI does not require editing code.

## Modular Structure

Prefer small helper modules and functions over monolithic geometry blocks.

### Good patterns

- Use helper modules for repeated geometry.
- Keep one module responsible for the visible output.
- Separate layout logic from mesh construction when possible.
- Name modules and variables consistently across related files.

### Practical guidance

- Use helper functions for measurements, string handling, and derived dimensions.
- Keep geometry code focused on the actual model shape.
- Keep preview logic separate when the file supports multiple display modes.

## Customizer Inputs

Use simple, predictable inputs so the OpenSCAD Customizer can expose them cleanly.

### Input rules

- Put editable variables in the main file, before the first `{` in the source.
- Use `/* [Hidden] */` to stop the Customizer from exposing internal values.
- Keep exposed values to simple literals: string, number, boolean, or arrays of up to four numeric literals.
- Avoid expressions for values you want the Customizer to show.
- Use inline comments to define ranges, steps, and option lists explicitly.

### Good patterns

- Strings for labels, names, and select-style values.
- Numbers for sizes, tolerances, and offsets.
- Booleans for feature toggles.
- Small numeric arrays for position, size, or vector inputs.

### Practical guidance

- Do not rely on the Customizer to guess a useful range when precision matters.
- Keep ranges tight enough that the UI guides users toward valid values.
- Use the hidden section for derived values and internal helpers, not user-editable controls.

### Example patterns

```scad
/* [Main Settings] */
mode = "assembly"; // [assembly:Assembly View, print:Print View]
enabled = true; // [false, true]
size = 14; // [10:0.5:20]
offset = [0, 0, 1];

/* [Hidden] */
derived_size = size + 2;
```

- Use a dropdown-style comment for named modes or presets.
- Use a checkbox-style boolean for feature toggles.
- Use a slider-style range when the value needs bounded precision.
- Use a short numeric array for positions or dimensions.
- Compute dependent values after the hidden marker.

## Maintenance Checklist

- The model is readable without tracing every line.
- The file structure makes future edits easy.
- Parameter groups are stable and clearly labeled.
- Repeated geometry is factored into reusable helpers.
- The final output is easy to find at the bottom of the file.

## References

Use the canonical docs when you need language behavior or library details:

- OpenSCAD Documentation: [openscad.org/documentation.html](https://openscad.org/documentation.html)
- OpenSCAD Language Reference: [OpenSCAD docs](https://files.openscad.org/documentation/manual/)
- OpenSCAD User Manual: [OpenSCAD docs](https://openscad.org/documentation.html)
- BOSL2 Wiki: [github.com/BelfrySCAD/BOSL2/wiki](https://github.com/BelfrySCAD/BOSL2/wiki)
- BOSL2 Repository: [github.com/BelfrySCAD/BOSL2](https://github.com/BelfrySCAD/BOSL2)

For this repo, BOSL2 is the main shared library for geometry helpers, attachments, rounding, and other modeling utilities.
