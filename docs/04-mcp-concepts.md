# MCP Concepts: Hosts, Servers, Tools

## The problem MCP solves

You now know tools give agents hands. The awkward part used to be *how* those
hands got attached. Every AI app had its own plug format, so every tool
developer had to build a custom version for every app. Apps spoke N
languages, tools had to speak all of them.

The **Model Context Protocol (MCP)**, introduced in late 2024, said: let's all
agree on one plug. Now an app that speaks MCP can use any tool built for MCP —
and a tool built for MCP works in every MCP-speaking app. One language,
everyone fluent.

The nickname that stuck: **"USB-C for AI."** Devices used to need a drawer of
cables; now one cable shape fits the laptop, the monitor, the charger. MCP is
that standardized cable for AI tools.

## The three words

### Host — the app you use

The **host** is the desktop app you actually open: the chat window, the
editor's AI panel, the assistant app. It's where you type requests and read
answers. "Host" is the polite word for "the AI client on your machine."

Examples of what hosts look like (brand names change; *shapes* don't): a
desktop chat app with an "Extensions" or "Connectors" settings page, a code
editor with an AI sidebar, a locally-run assistant UI.

### Server — the little program that offers tools

An **MCP server** is a small program that runs on your machine and says,
"here are the tools I provide: `search_notes`, `write_reminder`,
`list_files`…" That's it. The word "server" sounds like a humming rack in a
basement, but here it mostly means "a helper process on your own computer."

Important: an MCP server is *local to you* by default. It doesn't need the
cloud, an account, or an internet connection to do its job — unless its tools
themselves reach outward (like a web-search tool would).

### Tool — one ability, with a name

A **tool** is a single, named capability the server offers, e.g.:

- `list_dir(path)` — show what's in a folder
- `write_note(title, body)` — save a note
- `search_notes(query)` — find matching lines

The host learns a tool's name, description, and inputs — its *menu entry* —
and can then call it on your behalf when your request fits.

## How a request actually flows

One trip around the loop, start to finish:

```
1. You (in the host):  "Find my furnace-filter notes and save a summary."
2. Host:               looks through its connected servers' tool lists
3. Host → Server:      "please run search_notes('furnace filter')"
4. Server:             does it, returns the matches
5. Host:               shows the model the matches
6. Host → Server:      "please run write_note(title='Filter summary', ...)"
7. Server:             writes the file, returns success
8. You:                read the note. Approve or correct. Carry on.
```

Steps 3–7 can each be invisible, or — with approval prompts on — can each be
a click of yours. The client decides; you choose the client setting.

## Everything else you'll see named

You only *need* host/server/tool. But documentation will use two more words,
so here they are, demystified:

- **Resource** — *data* a server offers to read: the contents of a file, a
  list of reminders. Tools *do* things; resources *are* things to look at.
- **Prompt** — a saved, reusable starting request the server provides, like
  a template: "Summarize note [pick one]."

## Why one protocol matters to you

- **Tools you install travel.** Learn one server, use it in every MCP
  client — today's setup knowledge applies tomorrow too.
- **Servers compete on quality, not lock-in.** A notes server that works
  everywhere has to actually be *good*, not merely installed.
- **Your skills transfer.** A config file for one host looks like a config
  file for another. Chapter 5 shows the pattern; you'll recognize it in any
  client forever after.

## What an MCP server is *not*

- Not a cloud service you're logging into. It's a program running beside
  your agent, often seconds after you launched the host app.
- Not automatically trusted. It's software like any other; you install it
  from somewhere, look at what it asks for, and grant access accordingly.
  In fact its *demands* are exactly what you learned to read in chapter 3.

## Where confusions usually happen

- "Is my chat window a server?" No — the chat app is the **host**. It
  *connects to* servers.
- "Do I need to be online?" Usually not, especially for local file/notes
  tools. (The model behind the host may be cloud-based depending on your
  client — that's the client's business, not the server's.)
- "Can one server do everything?" Technically yes; practically, small
  focused servers are the norm — a notes server, a file server, a reminders
  server. Dropping and swapping is easy precisely because the plug is
  standard.

---

Concepts in hand. Time to attach real ones:
[Desktop setup, step by step](05-desktop-setup.md)
