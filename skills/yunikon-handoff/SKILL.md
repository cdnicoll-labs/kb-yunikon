---
name: yunikon-handoff
description: Write a handoff for a yunikon teammate taking over a client, a site, or a piece of work, built from the yunikon knowledge base (kb-yunikon). Use when the user says handoff, handover, hand this to someone, brief someone on a client, or a teammate is covering for someone else.
---

# yunikon handoff

A handoff gets one teammate working on something without needing a call. It is a message, not a knowledge base document: it carries open work and status, which the knowledge base does not hold. Never save it with `save_document`.

## Gather

1. Ask who it is for, what they are taking over (client code, site, or task), and by when.
2. `search` the recipient's name with `kind` `profile` and read it. Their hours and what they own shape the handoff. If there is no profile, carry on.
3. `search` the client code and read what bears on the work: the client's entry in `clients`, site pages, retrospectives, decisions, how-tos.
4. Ask the user for what the knowledge base cannot know: where things stand, open items, deadlines, what has been tried, who on the client side is waiting.

## Write

Keep it short. Sections in order, leaving out empty ones:

- **What you're taking over**: one or two sentences, and the deadline.
- **Where it stands**: the state today.
- **Next steps**: numbered, the first one doable today.
- **Watch out for**: fragile points and lessons from retrospectives.
- **Read first**: knowledge base documents by title, so they can ask their agent for them.
- **Access**: the 1Password vault and item. Never the login itself.
- **Who to ask**: by area, from the site page and profiles.
- **Before it goes live**: only for code or server changes. Database migrations, environment variables, new dependencies, anything to switch on per client, and what to check afterwards.

Client staff by role, never by name.

## Finish

Show the handoff to the user. Offer to write it to a local file or an email draft; never send it. If writing it turned up something that stays true, such as a fact about a site or a lesson, offer to save that separately with `yunikon-client` or `kb-save`.
