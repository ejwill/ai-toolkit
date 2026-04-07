# Using Skills

Skills are stored under `skills/`, with each skill in its own directory.

## Install with the Skills CLI

Use the `skills` CLI for normal installation.

```sh
npx skills add ejwill/ai-toolkit --list
npx skills add ejwill/ai-toolkit --skill '*' --global --agent codex --yes
npx skills add ejwill/ai-toolkit --skill openscad-authoring --global --agent codex --yes
```

The CLI supports GitHub shorthand (`owner/repo`), full GitHub URLs, direct skill paths, and local paths. Use `--copy` if you need physical copies instead of symlinks.

## Manual Install

If the CLI is not available, copy or symlink the skill directory into the target agent's skills folder.

```sh
ln -s /Users/erwinwill/Documents/Programming/ai-toolkit/skills/openscad-authoring ~/.codex/skills/openscad-authoring
```

Keep repo-specific material out of reusable skills where possible. If a workflow only makes sense for one project, keep it in that project instead.
