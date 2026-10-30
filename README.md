# Nurtur's plugins for Claude

A [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces) for Nurtur's products. It holds only plugin manifests and skills: each plugin points Claude at an MCP server that lives in its product's own repository, behind that product's sign-in.

## Using it

In Claude Code (in the Claude desktop app, or the terminal), once:

```
/plugin marketplace add e-prop/mcp-plugins
/plugin install nurtur@nurtur
```

## Plugins

| Plugin | What it does | MCP server |
| --- | --- | --- |
| `nurtur` | `/nurtur:import-site <site id or name>` imports an estate agency's existing website into Nurtur Websites, from the site's setup wizard; `/nurtur:edit-site <site id or name>` edits a live site by talking it through, or works through its BugHerd tasks, asking before anything destructive or sweeping. Brings BugHerd's MCP server (`mcp.bugherd.com`) too. Needs a Nurtur account with the "import websites" permission, and Claude in Chrome for imports. | `websites` repository, `routes/ai.php` |
| `nurtur-uat` | The same, against UAT (`mcp.websites.uat.nurtur.digital`), for testing: `/nurtur-uat:import-site` and `/nurtur-uat:edit-site`. UAT's setup wizard shows it. | the same, on UAT |

## Adding a plugin

Any of Nurtur's projects can add one: a folder under `plugins/` with `.claude-plugin/plugin.json`, an `.mcp.json` naming its server's address, and its skills, listed in `.claude-plugin/marketplace.json`. Keep the method an agent follows on the server, where it can change without a plugin release, and keep anything private out of this repository: it is public, so people without GitHub access can install it.

Bump a plugin's `version` when it changes, so Claude offers the update.

A plugin's server address is fixed in its `.mcp.json`: an address taken from the environment stops the desktop app signing in. So each environment is a plugin of its own, `nurtur` and `nurtur-uat`, whose skills are kept the same: change both.

## Developing locally

`dev/` is a second marketplace, `nurtur-dev`, whose plugins connect to the MCP servers running in Sail. Its plugins share their skills with the production ones. From a checkout:

```
/plugin marketplace add ~/Documents/GitHub/mcp-plugins/dev
/plugin install nurtur@nurtur-dev
```

The desktop app won't sign in to an `http` address, so test against Sail in the terminal (`claude --chrome`).
