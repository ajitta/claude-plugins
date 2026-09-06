# ajitta's Claude Code plugins

A marketplace catalog. It holds no plugin code — every entry points at the
repository that owns that plugin, so each one is versioned and released on its
own.

```
/plugin marketplace add ajitta/claude-plugins
```

Then install what you want:

```
/plugin install game-engagement-retention-skills@ajitta
/plugin install unknowns@ajitta
```

## Plugins

| Plugin | What it does | Repository |
|---|---|---|
| `game-engagement-retention-skills` | Reward-moment design and lifecycle retention for games and consumer interactive apps | [Game-Engagement-Retention-Skills](https://github.com/ajitta/Game-Engagement-Retention-Skills) |
| `unknowns` | An operational loop for the gaps between the plan and reality | [know-your-unknowns](https://github.com/ajitta/know-your-unknowns) |

## Why explicit HTTPS URLs

Each entry uses a `url` source with a full `https://` git URL rather than the
`owner/repo` shorthand. Claude Code clones shorthand sources over SSH by default,
which fails outright for anyone without a key configured — the marketplace itself
falls back to HTTPS, but a plugin install does not. Spelling the URL out keeps the
install working regardless of the reader's git setup.

## Updating

`/plugin marketplace update ajitta` refreshes this catalog. Installing or
updating a plugin then fetches from that plugin's own repository, at the
version its `plugin.json` declares.

## License

MIT for this catalog. Each plugin carries its own license.
