# ajitta's Claude Code plugins

A catalog of ajitta's plugins. It holds no plugin code. **Each plugin serves
itself from its own repository**, and that is the recommended way to install
it. This catalog lists them side by side and is a second route to the same
code.

## Plugins

| Plugin | What it does | Repository |
|---|---|---|
| `game-engagement-retention` | Reward-moment design and lifecycle retention for games and consumer interactive apps | [Game-Engagement-Retention-Skills](https://github.com/ajitta/Game-Engagement-Retention-Skills) |
| `unknowns` | An operational loop for the gaps between the plan and reality | [know-your-unknowns](https://github.com/ajitta/know-your-unknowns) |
| `socratic-brainstorm` | Socratic questioning that tests an idea, then options, convergence and a brief | [superclaude/portable-skills](https://github.com/ajitta/superclaude/tree/master/portable-skills) |
| `socratic-elenchus` | Plato's elenchus: what is X, contradiction from your own premises, aporia; no advice | [superclaude/portable-skills](https://github.com/ajitta/superclaude/tree/master/portable-skills) |

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
/plugin marketplace add ajitta/superclaude
/plugin install socratic-brainstorm@ajitta-socratic
/plugin install socratic-elenchus@ajitta-socratic
```

The suffix after `@` is the marketplace name each repository declares, not the
owner.

## Install through this catalog

This route still works and is still maintained:

```
/plugin marketplace add ajitta/claude-plugins
/plugin install game-engagement-retention@ajitta
/plugin install unknowns@ajitta
/plugin install socratic-brainstorm@ajitta
/plugin install socratic-elenchus@ajitta
```

Both routes install the same code, from the plugin's own repository, at the
version its `plugin.json` declares. You do not need to switch if you already
installed through `@ajitta`. Installing the same plugin through both routes
gives you two copies of every skill, so pick one.

## Why explicit HTTPS URLs

Each entry gives a full `https://` git URL rather than the `owner/repo`
shorthand. `game-engagement-retention` is a `git-subdir` source with
`path: plugin`, because that repository serves the plugin from `plugin/` as of
3.3.0; `unknowns` is a `url` source at its repository root. Claude Code clones shorthand sources over SSH by default,
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
