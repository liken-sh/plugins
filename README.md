# liken plugins

This repository is the catalog of liken's Agent Skills for Claude
Code. Each component of the [liken](https://github.com/liken-sh/liken)
repository emits its how-to guides as skills, in a `skills/` directory
in the component's own directory. This catalog lists those components
so one command installs them.

Add the catalog, then install everything:

```sh
claude plugin marketplace add liken-sh/plugins
claude plugin install everything@liken
```

Or install one component's skills:

```sh
claude plugin install media@liken
```

Each plugin's skills are namespaced by its name, so the guide for
mapping a controller becomes `/media:mapping-a-controller`. The
plugin names are:

| Plugin | Directory |
| --- | --- |
| `liken` | [`liken/`](https://github.com/liken-sh/liken/tree/main/liken) |
| `media` | [`media-operator/`](https://github.com/liken-sh/liken/tree/main/media-operator) |
| `display` | [`display-operator/`](https://github.com/liken-sh/liken/tree/main/display-operator) |
| `audio` | [`audio-operator/`](https://github.com/liken-sh/liken/tree/main/audio-operator) |
| `bluetooth` | [`bluetooth-operator/`](https://github.com/liken-sh/liken/tree/main/bluetooth-operator) |
| `library` | [`library-operator/`](https://github.com/liken-sh/liken/tree/main/library-operator) |
| `people` | [`people-operator/`](https://github.com/liken-sh/liken/tree/main/people-operator) |
| `equipment` | [`equipment-operator/`](https://github.com/liken-sh/liken/tree/main/equipment-operator) |
| `git-csi` | [`git-csi-driver/`](https://github.com/liken-sh/liken/tree/main/git-csi-driver) |
| `per-node` | [`per-node-csi-driver/`](https://github.com/liken-sh/liken/tree/main/per-node-csi-driver) |

`everything` contains no skills of its own. It depends on every plugin
above, and Claude Code installs its dependencies with it.

## Where the skills come from

A skill is a guide in the component's manual on
[liken.sh](https://liken.sh/), emitted a second way. The guide's front
matter carries a `description` that says what the guide does and when
to use it, and the generator in
[`brand/skills/`](https://github.com/liken-sh/liken/tree/main/brand/skills)
writes the rest of the skill from the guide's body. The guide stays
the one source, and CI fails when a component's `skills/` directory is
stale. The design is `brand/plans/01-guides-as-skills.md` in the liken
repository.

## Versions

Every entry follows the liken repository's `main`. Each entry is a
`git-subdir` source, so an install or an update downloads only the
component's directory, with the guides currently on that branch. The
catalog has no pinned set that was tested together. A pinned catalog
would need a commit here for every release of liken.

## Other agents

The catalog is for Claude Code. Any agent that reads the
[Agent Skills](https://agentskills.io/) format can take a component's
`skills/` directory directly, for example with
`npx skills add https://github.com/liken-sh/liken/tree/main/media-operator`.
