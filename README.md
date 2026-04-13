# Vue Codex Skills

Reusable Codex skills for Vue 3 and TypeScript projects.

## Included Skills

- `vue-project-architecture`
- `vue-component-design`
- `vue-code-quality`
- `vue-testing-and-verification`
- `vue-code-review`

## Install Locally

Codex discovers user-installed skills from `$CODEX_HOME/skills`. If `CODEX_HOME` is not set, the default is `~/.codex/skills`.

From this repository root:

```bash
CODEX_SKILLS_DIR="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$CODEX_SKILLS_DIR"

cp -R skills/vue-project-architecture "$CODEX_SKILLS_DIR/"
cp -R skills/vue-component-design "$CODEX_SKILLS_DIR/"
cp -R skills/vue-code-quality "$CODEX_SKILLS_DIR/"
cp -R skills/vue-testing-and-verification "$CODEX_SKILLS_DIR/"
cp -R skills/vue-code-review "$CODEX_SKILLS_DIR/"
```

Restart Codex after installing so it can discover the new skills.

## Install For Local Development

If you want Codex to use edits from this repo immediately, symlink the skill folders instead of copying them:

```bash
CODEX_SKILLS_DIR="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$CODEX_SKILLS_DIR"

ln -sfn "$PWD/skills/vue-project-architecture" "$CODEX_SKILLS_DIR/vue-project-architecture"
ln -sfn "$PWD/skills/vue-component-design" "$CODEX_SKILLS_DIR/vue-component-design"
ln -sfn "$PWD/skills/vue-code-quality" "$CODEX_SKILLS_DIR/vue-code-quality"
ln -sfn "$PWD/skills/vue-testing-and-verification" "$CODEX_SKILLS_DIR/vue-testing-and-verification"
ln -sfn "$PWD/skills/vue-code-review" "$CODEX_SKILLS_DIR/vue-code-review"
```

Restart Codex after creating or changing symlinks.

## Install From GitHub

After this repository is pushed to GitHub, ask Codex to install the skill folders from the repo, for example:

```text
Install these Codex skills from <owner>/<repo>:
- skills/vue-project-architecture
- skills/vue-component-design
- skills/vue-code-quality
- skills/vue-testing-and-verification
- skills/vue-code-review
```

Codex installs GitHub-hosted skills into `$CODEX_HOME/skills` and will tell you to restart after installation.

## Use In Vue Projects By Default

To make Codex apply these skills by default in a Vue repo, add an `AGENTS.md` file to that repo:

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
