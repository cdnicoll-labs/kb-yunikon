# kb-yunikon

Yunikon's half of the shared knowledge base: the connection to Yunikon's MCP server, Yunikon's own skills, and the marketplace the Yunikon team installs from.

This repo is both a plugin and a marketplace. A teammate adds this marketplace and `kb-skills`, and never sees another client's entries.

```
.claude-plugin/plugin.json       the yunikon plugin manifest
.claude-plugin/marketplace.json  this plugin at ./. The core skills come from the kb-skills marketplace
skills/yunikon-client/           add or update a client: the client list entry and its site pages
skills/yunikon-handoff/          write a handoff for a teammate from what the knowledge base holds
```

This plugin carries skills and nothing else. The connection is added separately, as a connector or in a
client hub.

## Install

Two marketplaces: this one for Yunikon's skills, and `kb-skills` for the core skills everyone uses.

```bash
claude plugin marketplace add https://github.com/cdnicoll-labs/kb-skills.git
claude plugin marketplace add https://github.com/cdnicoll-labs/kb-yunikon.git
claude plugin install kb-core@kb-skills
claude plugin install yunikon@yunikon
```

Both repos are public, so no GitHub login is needed. Use the full `https://` URLs: the `owner/repo`
shorthand records an SSH remote, and updates then fail without an SSH key on GitHub.

Why two and not one: a marketplace entry that points into another repo is fetched over SSH, which
fails for anyone without an SSH key on GitHub. Tested 2026-09-24. Each repo listing only itself uses
the HTTPS path, which works.

Then connect to the knowledge base. In the Claude apps, add it as a custom connector with the server's
`/mcp` URL and sign in with your email. In Claude Code, work from a Yunikon client hub whose `.mcp.json`
lists the server; the first session asks you to sign in. Nothing is installed or pasted on your machine.

## Writing a skill

Follow the convention in `kb-skills`' README: no real people, no real client situations, placeholders
first. This repo may name Yunikon itself, and nothing about Yunikon's clients or people.

## Changing a skill

Edit it, bump `version` in both `.claude-plugin/plugin.json` and this repo's marketplace entry, open a pull request, merge. Everyone has it next session. A version bump in `kb-skills` also needs the `kb-core` entry here bumped to match.

```bash
claude plugin validate --strict .
```
