# ajitta's Claude Code plugins

A catalog of ajitta's plugins. It holds no plugin code. **Each plugin serves
itself from its own repository**, and that is the recommended way to install
it. This catalog lists them side by side and is a second route to the same
code.

## Plugins

| Plugin | What it does | Repository |
|---|---|---|
| `game-engagement-retention` | Reward-moment design and lifecycle retention for games and consumer interactive apps | [Game-Engagement-Retention-Skills](https://github.com/ajitta/Game-Engagement-Retention-Skills) |
| `unknowns` | Skills for what you, the AI, or neither of you knows yet, in any domain | [know-your-unknowns](https://github.com/ajitta/know-your-unknowns) |
| `dia` | Thirteen reasoning-and-review skills plus the dia router: goal confirmation (skopos), Socratic elenchus and inquiry (quaestio), reductio, internal critique, argument warrants, counterexamples, counterplans, a single review pass (emend), verification-gated rounds, adjudicating review reports, rules for text a model follows (regula), and deepening a request as a field's top practitioners would; a skill starts when the message begins with dia or its name | [dialectic-skills](https://github.com/ajitta/dialectic-skills) |
| `dia-panel` | Claude Code only: a workflow that runs four dia review skills on one document in parallel and has `dia-adjudicate` judge their reports twice; installs `dia` with it | [dialectic-skills](https://github.com/ajitta/dialectic-skills) |
| `karpathy-regula` | Karpathy's coding guidelines (think before coding, keep it simple, make scoped changes, define verifiable goals), revised with dia-regula; an unofficial adaptation | [karpathy-regula](https://github.com/ajitta/karpathy-regula) |

## Install (recommended): straight from the plugin's repository

```
/plugin marketplace add ajitta/Game-Engagement-Retention-Skills
/plugin install game-engagement-retention@game-engagement-retention-skills
```

```
/plugin marketplace add ajitta/know-your-unknowns
/plugin install unknowns@know-your-unknowns
```

```
/plugin marketplace add ajitta/dialectic-skills
/plugin install dia@dialectic-skills
/plugin install dia-panel@dialectic-skills   # optional, Claude Code only
```

```
/plugin marketplace add ajitta/karpathy-regula
/plugin install karpathy-regula@karpathy-regula
```

The suffix after `@` is the marketplace name each repository declares, not the
owner.

## Install through this catalog

This route still works and is still maintained:

```
/plugin marketplace add ajitta/claude-plugins
/plugin install game-engagement-retention@ajitta
/plugin install unknowns@ajitta
/plugin install dia@ajitta
/plugin install dia-panel@ajitta   # optional, Claude Code only
/plugin install karpathy-regula@ajitta
```

Both routes install the same code, from the plugin's own repository, at the
version its `plugin.json` declares. You do not need to switch if you already
installed through `@ajitta`. Installing the same plugin through both routes
gives you two copies of every skill, so pick one.

## Why explicit HTTPS URLs

Each entry gives a full `https://` git URL rather than the `owner/repo`
shorthand. `game-engagement-retention` is a `git-subdir` source with
`path: plugin`, because that repository serves the plugin from `plugin/` as of
3.3.0; `unknowns` is a `git-subdir` source with `path: plugins/unknowns`, the generated plugin folder in know-your-unknowns as of 0.10.0; `dia` is a `git-subdir` source with `path: plugins/dia`, the generated plugin folder in dialectic-skills. `dia-panel` is a `git-subdir` source with `path: companions/dia-panel` in the same repository; its dependency `dia` resolves in whichever of the two marketplaces it is installed from. `karpathy-regula` is a `git-subdir` source with `path: plugins/karpathy-regula`. Claude Code clones shorthand sources over SSH by default,
which fails outright for anyone without a key configured. The marketplace itself
falls back to HTTPS, but a plugin install does not. Spelling the URL out keeps the
install working regardless of the reader's git setup.

## Renamed: `game-engagement-retention-skills` → `game-engagement-retention`

As of that plugin's 3.0.0, its `name` is `game-engagement-retention`. Claude Code
keys an installed copy on `name`, so a rename is a different plugin and no
`/plugin update` carries the old copy across. If you installed it before 3.0.0:

```
/plugin uninstall game-engagement-retention-skills@ajitta
/plugin marketplace update ajitta
/plugin install game-engagement-retention@ajitta
```

## Updating

`/plugin marketplace update ajitta` refreshes this catalog. Installing or
updating a plugin then fetches from that plugin's own repository, at the
version its `plugin.json` declares.

## License

MIT for this catalog. Each plugin carries its own license.
