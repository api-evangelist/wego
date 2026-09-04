---
name: wego-setup
description: One-time setup so this agent can plan and book travel through Wego. Installs the wego CLI and its skill, then follow that skill to search and compare flights and hotels for the user.
---

# Set up Wego for this agent

One-time setup. Afterwards you plan flights and hotels for the user through the
`wego` command: they ask for a trip and you run the commands, parse the JSON,
and present the choices.

## 1. Install the wego CLI

Check whether it is already present:

    wego version

If that fails, install it. Ask the user before running a remote installer:

    curl -fsSL https://docs.wego.com/cli/install | bash

This installs the `wego` command and the wego skill together - through a pipe
there is no prompt, so nothing to approve and nothing to wait for. Set
`WEGO_CLI_INSTALL_SKILL=0` beforehand to opt out of the skill step; a
skill-install failure never fails the CLI install. The on-disk copy of the skill
is what makes future agent sessions discover it automatically, and it stays
current on its own (a silent, once-a-day background refresh).

## 2. Load the skill in this session

Read the installed skill and follow it now. No restart is needed – ask the CLI
where it landed, then read that file:

    wego skill path

It defines the full workflow: login, place resolution, flight and hotel search,
comparison, id handling, and Wego checkout links.

## 3. Handle the request

Follow that skill to serve whatever trip the user asked for, for example
"cheapest one way Riyadh to Cairo, second week of next month". Never claim a
booking, payment, or reservation happened. The CLI searches and generates
checkout links only.
