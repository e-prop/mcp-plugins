---
description: Import an estate agency's existing website into Nurtur Websites, into a site whose setup wizard was finished with "Import an existing website". Give the site's id, shown in the wizard. Asks nothing; the wizard recorded the existing website and whether it moves onto one of our templates.
argument-hint: "<site id>"
---

Import an estate agency's existing website into Nurtur Websites, into site `$ARGUMENTS`.

## Before you start

You need two sets of tools. Check both are there before you begin:

- The `websites` tools from this plugin. If they ask you to sign in, the person signs in with their Nurtur account, which needs the "import websites" permission. If they refuse for lack of it, stop and say so.
- Claude in Chrome, to see the existing website and the new one side by side. If it isn't connected, ask the person to switch it on, and wait.

If no site id was given, ask for it once: it is shown at the end of the site's setup wizard. That is the only question you ask.

The import runs to the end without asking the person anything, as it may be left running overnight. Tell them so, and that two things can still pause it, which they can allow now:
- Claude Code asking permission to use a tool: the `websites` tools, Claude in Chrome and helper agents can be allowed for the session;
- Claude in Chrome asking for access to a site: both the existing website and the new one need it.

## Then

1. Get the method with `get_import_method`, for the site. If it refuses the site, because it's set up already or isn't waiting for an import, stop and tell the person what it said.
2. Follow the method to the letter, to the end, without stopping to ask the person anything. It ends with `finish_import`.

Tell the person the new site's preview and admin addresses (from `get_site`) as soon as you start, so they can watch it take shape.
