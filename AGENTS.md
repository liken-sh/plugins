# Working on plugins

This repository is the Claude Code plugin catalog for the Agent Skills
that each `liken` repository emits. `.claude-plugin/marketplace.json`
lists one plugin for each repository, and `everything` depends on all
of them. `README.md` explains the catalog.

When a repository adds or removes its `skills/` directory, update the
catalog, the `everything` plugin, and the table in `README.md` in one
change.
