---
name: yunikon-client
description: Add a new yunikon client, or update one, in the yunikon knowledge base (kb-yunikon): its entry in the client list and a page for each of its websites. Use when the user says new client, add a client, set up a client code, document a client's website or shop, or names a client code that has no entry yet.
---

# yunikon client

Every client has a short code, usually three letters. The team uses it everywhere, and site pages carry it as their `project`.

A client lives in two places:

- **The client list** (slug `clients`): one row in the "All client codes" table and one section per client. One document holds every client.
- **A site page per website** (`kind: site`): what someone needs to work on that site without asking around.

Save to `kb-yunikon` only. If `whoami` reports another client, stop and say so.

## Start

`get_document` `clients`. If the code is already there, this is an update: work from the existing entry and `search` the code for its site pages. Ask whether the user wants the client entry, a site page, or both.

## Interview

Ask one question at a time. Skip what the user has already said or what a file they point to answers. A WordPress Site Health or WooCommerce status report is the best source for a site page.

Client entry:

1. Code and name. Focus client? Any naming rule, such as a name always written in lowercase.
2. The client's business, in two or three bullets.
3. What yunikon does for them.
4. Who at yunikon does what, and who is the main contact.
5. The client side, by role only, and the language used with them.

Site page, once per website:

6. URL, what the site is (shop, corporate, landing page), languages, currency.
7. Platform and theme.
8. The plugins that matter, each with its purpose. No versions.
9. Hosting, staging, backups.
10. Where to look when it breaks, and who to call for each area.
11. Recurring support topics, update timing, watch points. Skip if there are none.

Access is a pointer only: "logins are in 1Password". Never a username, password, or key. If the user pastes one, do not write it anywhere and tell them to keep it in 1Password.

## Draft

**Site page**

- `kind`: `site` · `project`: the client code
- `slug`: the domain with dots as hyphens (`<domain>-<tld>`), or `<code>-<purpose>` when a client has several sites (`<code>-shop`)
- Title: `<CODE> — <client name> (<domain>)`
- Body opens with two lines: `- **Client:** <CODE>, see [[clients]]` and `- **Status of this page:** <where the facts came from, with the date>. Versions are deliberately not listed; check them on the live site.`
- Sections in order, leaving out empty ones: **Client**, **Who does what at yunikon**, **Services**, **Known recurring support topics**, **Platform**, **Theme**, **Plugins** (table: Plugin, Purpose), **Hosting and environments**, **Where to look when it breaks**, **Update timing**, **Watch points**, **History** (links to retrospectives and decisions, newest first)

**Client list**

- Add a row to "All client codes": code, client, business, what yunikon does, site pages as `[[<slug>]]` or "not yet".
- Add a section `## <CODE> – <name>` with **Business**, **Websites**, **What yunikon does**, **Who at yunikon**.
- Add a source for where the facts came from.
- Leave every other client's entry exactly as it is.

Save site pages first and the client list last, so its links resolve.

## Finish

Show every draft before saving any of them. Then follow the `kb-save` skill from step 3 (check the draft) through step 8 for each document.
