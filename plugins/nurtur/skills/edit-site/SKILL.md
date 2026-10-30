---
description: Edit a live Nurtur Websites site by talking it through, or by working through its BugHerd feedback. Give the site's id, or its name. Small edits are made straight away; anything destructive or sweeping is described first and only done once you say yes. Changes only ever reach the one site opened.
argument-hint: "<site id or name>"
---

Edit a live estate agency website on Nurtur Websites, for the person you're talking to: `$ARGUMENTS`.

## Before you start

You need the `websites` tools from this plugin. If they ask you to sign in, the person signs in with their Nurtur account. If the tools refuse for lack of permission, stop and say so. Claude in Chrome helps you check each change as a visitor sees it; if it isn't connected, say you can't look at the pages, and carry on.

The plugin brings BugHerd's tools too. If the person is working from BugHerd feedback, they sign in with their BugHerd account when the tools first ask. `how_to_edit` says how to find this site's project, by its `addresses`, and work through its tasks; never work from a project that isn't this site's.

## Open the site

1. Find the site. If you were given a number, it's the site's id. Otherwise it's a name: look it up with `find_sites`. If more than one site fits, list them, each with its address and whether it's live, and ask which one. If none does, ask the person for the name as it appears in the admin, or the site's id.
2. Open it with `open_site`, giving its id. It answers with a key and `how_to_edit`. Give the key as `website` to every other tool, and follow `how_to_edit` to the letter: it says which changes you make straight away, and which you describe and only make once the person says yes.
3. Tell the person which site you've opened, with its address, and ask what they'd like to change, unless they've already said.

## While you work

This conversation edits that one site. Don't open another unless the person asks for it by name or id; if they do, say which site you're leaving and which you're opening, and wait for their yes. Every change is live as soon as it's saved, so after each one say what changed and where to see it.
