# AI Toolkit

Reusable skills, agents, prompts, templates, and workflow helpers for AI-assisted projects.

This repo is intentionally broad. It started with OpenSCAD and MakerWorld skills, but it is set up to hold future project helpers that are not tied to a single codebase.

## Layout

- `skills/`: reusable agent skills with `SKILL.md` files and nearby references.
- `agents/`: agent role definitions, operating notes, or reusable persona/workflow specs.
- `prompts/`: prompts that are useful across projects.
- `templates/`: reusable file templates, issue/PR text, checklists, or starter content.
- `scripts/`: helper scripts used by skills or workflows.
- `docs/`: notes about how to use and maintain the toolkit.

## Current Skills

- `skills/openscad-authoring`: general OpenSCAD structure, modular modeling, parameter organization, and maintainable source layout.
- `skills/makerworld-open-scad`: MakerWorld-specific OpenSCAD export rules.
- `skills/makerworld-listing`: MakerWorld listing copy, README text, customization guides, tags, and release notes.
- `skills/makerworld-images`: MakerWorld listing images, covers, gallery sequencing, comparison images, and GIFs.

## Conventions

Each skill should live in its own directory:

```text
skills/
  example-skill/
    SKILL.md
    reference.md
    scripts/
    examples/
```

Keep `SKILL.md` short and operational. Put longer explanations, examples, and checklists in adjacent reference files so agents can load only what they need.

