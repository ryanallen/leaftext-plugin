# Leaftext plugin

Lets your coding agent read, edit, check, tick and save the documents open in [Leaftext](https://leaftext.com), and write Markdown Leaftext draws. It adds one skill and one tool server, `leaftext --mcp`, which the installed app answers. It changes nothing else about your agent.

Leaftext has to be installed. On Windows the installer already puts the word `leaftext` on your command path. On a Mac, run this once in a terminal:

```
sudo mkdir -p /usr/local/bin && sudo ln -sf /Applications/leaftext.app/Contents/MacOS/leaftext /usr/local/bin/leaftext
```

## Install

**Claude Code**

```
claude plugin marketplace add ryanallen/leaftext-plugin
claude plugin install leaftext@leaftext
```

**Codex**

```
codex plugin marketplace add ryanallen/leaftext-plugin
```

Then install Leaftext from `/plugins` in Codex.

**Cursor** — install Leaftext from the Cursor marketplace.

**Antigravity**

```
git clone https://github.com/ryanallen/leaftext-plugin ~/.gemini/config/plugins/leaftext
agy mcp add leaftext -- leaftext --mcp
```

For an existing clone, update it with `git -C ~/.gemini/config/plugins/leaftext pull`, then run `agy mcp add leaftext -- leaftext --mcp`. Check the server with `agy mcp list`.

**Gemini CLI**

```
gemini extensions install https://github.com/ryanallen/leaftext-plugin
```

Restart the agent after installing, so it starts the tool server. The [agents page](https://leaftext.com/docs/01-features/10-agents.md) says what each tool does and how to connect an agent this plugin does not cover.
