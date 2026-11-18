# arduino-claude-plugins

A catalog of Claude Code plugins that take repetitive engineering tasks off your hands, from board testing to release chores. It holds no plugin code: each entry of [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json) points to the repository where the plugin lives, and the plugin keeps its own manifest and version there.

## Use

```console
$ claude plugin marketplace add robgee86/arduino-claude-plugins
$ claude plugin install <plugin>@arduino-claude-plugins
```

The catalog has no releases: Claude Code reads its current state when you add it and again on `claude plugin marketplace update arduino-claude-plugins`. A plugin updates when its own version changes, with `claude plugin update <plugin>@arduino-claude-plugins`. To get both without asking, enable auto-update for the catalog under Marketplaces in `/plugin`. On a machine with no GitHub SSH key, set `CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1`.

## Plugins

| Plugin | What it does | Repository |
|---|---|---|
| `arduino-test-buddy` | Test App Bricks on a real Arduino board: the `board-test` skill and the MCP server it drives | [robgee86/arduino-test-buddy](https://github.com/robgee86/arduino-test-buddy) |

## Add a plugin

Add an entry to `plugins` with the plugin's `name`, as its own manifest states it, and its `source`. A GitHub repository whose root is the plugin takes `{ "source": "github", "repo": "owner/repo" }`; a plugin in a subfolder of a repository takes `{ "source": "git-subdir", "url": "owner/repo", "path": "folder" }`. Then check the file:

```console
$ claude plugin validate . --strict
```
