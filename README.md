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
| `nurtur` | `/nurtur:import-site <site id or name>` imports an estate agency's existing website into Nurtur Websites, from the site's setup wizard; `/nurtur:edit-site <site id or name>` edits a live site by talking it through, or works through its BugHerd tasks, asking before anything destructive or sweeping. Brings BugHerd's (`mcp.bugherd.com`) and Atlassian's (`mcp.atlassian.com`) MCP servers too, to work through BugHerd tasks and raise what needs a developer on the EP board, labelled `websites_mcp`. Needs a Nurtur account with the "import websites" permission, and Claude in Chrome for imports. | `websites` repository, `routes/ai.php` |
| `nurtur-uat` | The same, against UAT (`mcp.websites.uat.nurtur.digital`), for testing: `/nurtur-uat:import-site` and `/nurtur-uat:edit-site`. UAT's setup wizard shows it. | the same, on UAT |
| `members-hub` | Answers questions from Nurtur's members hubs (their pages, news, events, files, private knowledge bank, and the products each hub uses) as the signed-in user, on the hub they were last on; `list-hubs` and `open-hub` move between hubs. Needs a role that may use the hub assistant, on a hub with its assistant switched on. | `property-logic` repository, `routes/ai.php` |
| `members-hub-uat` | The same, against UAT (`api.members.uat.nurtur.tech`), for testing. | the same, on UAT |

## Adding a plugin

Any of Nurtur's projects can add one: a folder under `plugins/` with `.claude-plugin/plugin.json`, an `.mcp.json` naming its server's address, and its skills, listed in `.claude-plugin/marketplace.json`. Keep the method an agent follows on the server, where it can change without a plugin release, and keep anything private out of this repository: it is public, so people without GitHub access can install it.

Bump a plugin's `version` when it changes, so Claude offers the update.

A plugin's server address is fixed in its `.mcp.json`: an address taken from the environment stops the desktop app signing in. So each environment is a plugin of its own, `nurtur`, `nurtur-uat` and `nurtur-dev`, whose skills are kept the same: change `nurtur`, `nurtur-uat` and `nurtur-dev` together. Each holds a copy: Claude Code installs a plugin by copying it, and leaves a symbolic link out, so a plugin linking to another's skills is installed without them.

## Developing locally

`dev/` is a second marketplace, `nurtur-dev`, whose plugin `nurtur-dev` connects to the MCP servers running in Sail. Its skills are a copy of the production plugin's. From a checkout:

```
/plugin marketplace add ~/Documents/GitHub/mcp-plugins/dev
/plugin install nurtur-dev@nurtur-dev
```

Its plugin is `nurtur-dev`, so its commands are `/nurtur-dev:import-site` and `/nurtur-dev:edit-site`, and never clash with production's when both are installed.

The desktop app won't sign in to an `http` address, so test against Sail in the terminal (`claude --chrome`).
