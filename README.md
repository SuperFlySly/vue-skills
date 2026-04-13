# Vue Codex Skills

Reusable Codex skills for Vue 3 and TypeScript projects.

Codex discovers repo-local skills from `.agents/skills`. This repository is laid out so launching Codex here or copying `.agents/skills` into a Vue project makes the skills available without a separate packaging step.

## Included Skills

- `vue-project-architecture`
- `vue-component-design`
- `vue-code-quality`
- `vue-testing-and-verification`
- `vue-code-review`

## Use In A Vue Project

For a project-local install, copy the skills directory into your Vue project:

```bash
mkdir -p /path/to/vue-project/.agents
cp -R .agents/skills /path/to/vue-project/.agents/
```

Restart Codex after adding or changing skills so it can discover them.

If the Vue project already has an `.agents/skills` directory, copy only the skill folders:

```bash
mkdir -p /path/to/vue-project/.agents/skills
cp -R .agents/skills/vue-* /path/to/vue-project/.agents/skills/
```

## Use By Default

For a user-wide install on this machine, symlink the skill folders into Codex's user skill directory:

```bash
mkdir -p "$HOME/.agents/skills"
ln -sfn "$PWD/.agents/skills/vue-project-architecture" "$HOME/.agents/skills/vue-project-architecture"
ln -sfn "$PWD/.agents/skills/vue-component-design" "$HOME/.agents/skills/vue-component-design"
ln -sfn "$PWD/.agents/skills/vue-code-quality" "$HOME/.agents/skills/vue-code-quality"
ln -sfn "$PWD/.agents/skills/vue-testing-and-verification" "$HOME/.agents/skills/vue-testing-and-verification"
ln -sfn "$PWD/.agents/skills/vue-code-review" "$HOME/.agents/skills/vue-code-review"
```

Restart Codex after creating or changing symlinks.

If you prefer copied files instead of symlinks:

```bash
mkdir -p "$HOME/.agents/skills"
cp -R .agents/skills/vue-* "$HOME/.agents/skills/"
```

Restart Codex after copying the skills.

## Install From GitHub With Codex

Codex also supports installing GitHub-hosted skill folders through the `skill-installer` skill. In Codex, ask:

```text
Use skill-installer to install these Codex skills:
- https://github.com/SuperFlySly/vue-skills/tree/main/.agents/skills/vue-project-architecture
- https://github.com/SuperFlySly/vue-skills/tree/main/.agents/skills/vue-component-design
- https://github.com/SuperFlySly/vue-skills/tree/main/.agents/skills/vue-code-quality
- https://github.com/SuperFlySly/vue-skills/tree/main/.agents/skills/vue-testing-and-verification
- https://github.com/SuperFlySly/vue-skills/tree/main/.agents/skills/vue-code-review
```

Restart Codex after installing.

## Recommended Project Prompt

To make intent explicit in each Vue repo, add an `AGENTS.md` file:

```md
# AGENTS.md

This is a Vue 3 + TypeScript project.

Use these skills by default:

- Use `vue-project-architecture` for project structure, module boundaries, and architecture refactors.
- Use `vue-component-design` when creating or changing components.
- Use `vue-code-quality` for naming, TypeScript discipline, local contracts, and implementation clarity.
- Use `vue-testing-and-verification` before claiming Vue changes are complete.
- Use `vue-code-review` when reviewing Vue changes.

If multiple skills apply, use the smallest relevant set.
```

## Future Packaging

For a cleaner one-command installation experience, package these skills as a Codex plugin. The plugin can expose the same `.agents/skills` content through a reusable repository-level package instead of asking users to install each skill folder separately.

## References

- [Using skills in Codex](https://developers.openai.com/codex/skills/)
- [OpenAI skills catalog](https://github.com/openai/skills)
