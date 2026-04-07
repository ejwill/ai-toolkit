---
name: openscad-authoring
description: General OpenSCAD structure, modular modeling, parameter organization, and maintainable source layout. Use when writing or refactoring OpenSCAD files independent of any upload platform.
---

# OpenSCAD Authoring

## When to use

Use this skill for general OpenSCAD modeling work, including file structure, module organization, parameter grouping, and maintainability.

## Workflow

1. Read the source model structure.
2. Check the parameter groups and helper layout.
3. Refactor toward small reusable modules and a clear render entrypoint.
4. Preserve readability and stable naming where possible.

## Core Rules

- Keep the top of the file simple: banner comment, includes, then parameters.
- Put user-facing controls in obvious Customizer sections.
- Put computed geometry values and helper functions in a hidden section.
- Prefer reusable helper modules over repeated geometry blocks.
- Keep one obvious module or call as the visible final output.
- Use clear names for modules, functions, and parameters.
- Keep Customizer inputs as simple literals or short numeric arrays so they show up reliably.
- Use explicit range and step comments for sliders instead of trusting the Customizer to guess.
- Use `/* [Hidden] */` for internal values that should not appear in the UI.

## Common Checks

- The file should open cleanly in OpenSCAD.
- The model should still be understandable after future edits.
- Related parameters should stay grouped together.
- Repeated geometry should be factored into helpers where practical.
- The final render path should be easy to find.
- Customizer-visible inputs should appear before the hidden section.

## Example Patterns

```scad
/* [Main Settings] */
mode = "assembly"; // [assembly:Assembly View, print:Print View]
enabled = true; // [false, true]
size = 14; // [10:0.5:20]
offset = [0, 0, 1];

/* [Hidden] */
derived_size = size + 2;
```

- Use dropdown-style comments for named modes or presets.
- Use booleans for feature toggles.
- Use slider-style ranges for bounded numeric inputs.
- Use short numeric arrays for vectors and dimensions.
- Put dependent values after the hidden marker.

## Reference

See [OpenSCAD Authoring Guide](authoring_guide.md).
