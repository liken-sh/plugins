# Working on plugins

This repository is the Claude Code plugin catalog for the Agent Skills
that each component of the `liken` repository emits.
`.claude-plugin/marketplace.json` lists one plugin for each component,
as a `git-subdir` source on liken-sh/liken with the component's
directory as its `path`, and `everything` depends on all of them.
`README.md` explains the catalog.

When a component adds or removes its `skills/` directory, update the
catalog, the `everything` plugin, and the table in `README.md` in one
change. Run `claude plugin validate .` after every change to the
catalog.
