# liken plugins

This repository is the catalog of liken's Agent Skills for Claude
Code. Each liken repository emits its how-to guides as skills, in a
`skills/` directory at its root, and this catalog lists those
repositories so one command installs them.

Add the catalog, then install everything:

```sh
claude plugin marketplace add liken-sh/plugins
claude plugin install everything@liken
```

Or install one repository's skills:

```sh
claude plugin install media@liken
```

Each plugin's skills are namespaced by its name, so the guide for
mapping a controller becomes `/media:mapping-a-controller`. The
plugin names are:

| Plugin | Repository |
| --- | --- |
| `liken` | [liken](https://github.com/liken-sh/liken) |
| `media` | [media-operator](https://github.com/liken-sh/media-operator) |
| `display` | [display-operator](https://github.com/liken-sh/display-operator) |
| `audio` | [audio-operator](https://github.com/liken-sh/audio-operator) |
| `bluetooth` | [bluetooth-operator](https://github.com/liken-sh/bluetooth-operator) |
| `library` | [library-operator](https://github.com/liken-sh/library-operator) |
| `people` | [people-operator](https://github.com/liken-sh/people-operator) |
| `equipment` | [equipment-operator](https://github.com/liken-sh/equipment-operator) |
| `git-csi` | [git-csi-driver](https://github.com/liken-sh/git-csi-driver) |
| `per-node` | [per-node-csi-driver](https://github.com/liken-sh/per-node-csi-driver) |

`everything` contains no skills of its own. It depends on every plugin
above, and Claude Code installs its dependencies with it.

## Where the skills come from

A skill is a guide on the repository's site, emitted a second way. The
guide's front matter carries a `description` that says what the guide
does and when to use it, and the generator in the
[brand](https://github.com/liken-sh/brand) repository writes the rest
of the skill from the guide's body. The guide stays the one source,
and each repository's CI fails when its `skills/` directory is stale.
The design is `plans/01-guides-as-skills.md` in that repository.

## Versions

Every entry follows its repository's `main`. An install or an update
uses the guides currently on that branch. The catalog has no pinned set
that was tested together. A pinned catalog would need a commit here for
every release of every repository.

## Other agents

The catalog is for Claude Code. Any agent that reads the
[Agent Skills](https://agentskills.io/) format can take a repository's
`skills/` directory directly, for example with
`npx skills add liken-sh/media-operator`.
