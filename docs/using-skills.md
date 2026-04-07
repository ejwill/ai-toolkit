# Using Skills

Skills are stored under `skills/`, with each skill in its own directory.

To use a skill in another environment, copy or symlink the skill directory into that environment's skills folder.

Example:

```sh
ln -s /Users/erwinwill/Documents/Programming/ai-toolkit/skills/openscad-authoring ~/.agents/skills/openscad-authoring
```

Keep repo-specific material out of reusable skills where possible. If a workflow only makes sense for one project, keep it in that project instead.

