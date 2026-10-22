# Desktop Setup, Step by Step

Time to attach real tools to a real agent on your own computer. This chapter
walks a full setup for a typical desktop client, using one concrete example —
the config-file pattern you'll meet in nearly every MCP host. Menu names
drift between versions and apps, so we teach the *shape* first and the exact
clicks second.

## What you need offline-first

- A desktop MCP host app installed (a chat client or editor that supports
  "MCP", "tools", or "connectors" in its settings).
- Node.js installed — many popular MCP servers run via `npx`. Get the
  LTS version from nodejs.org; the default options are fine.
- A folder you're happy letting the agent read. We'll use a notes folder:
  - Windows: `C:\Users\you\Documents\notes`
  - macOS/Linux: `~/Documents/notes`

Make that folder now and drop a couple of plain-text notes in it. Hello,
test material.

## The shape of the thing: a config file

Most desktop hosts learn about servers through a **JSON config file** — a
settings file you edit with any text editor. It always looks like this
shape:

```json
{
  "mcpServers": {
    "<name-you-choose>": {
      "command": "<program to run>",
      "args": ["<arguments>"]
    }
  }
}
```

Three lines of meaning:

- the whole file is a list under the key `mcpServers`;
- each server gets a name you pick (this is just a label);
- each server says *how to start it*: a command and its arguments.

That's the entire format. Any client, any server — same shape, different
words inside.

## Worked example: a filesystem server

The classic first server is a filesystem server, which lists/reads/writes
files inside folders you explicitly name. Perfect fit for everything we
practiced in chapter 2.

### 1. Find the config file

Host apps differ in where they keep it. The usual suspects:

- the app's Settings → Developer / Extensions / Connectors page, often with
  an "Edit config" or "Open config" button (look for this first);
- a settings/menu item that reveals the app's support or data folder;
- documentation for your specific client titled something like
  "connect MCP servers" or "extend."

### 2. Add the server

Edit the file so it contains your notes folder in the arguments — this is
you *scoping* the tool, exactly like chapter 3 taught:

```json
{
  "mcpServers": {
    "filesystem-notes": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "C:\\Users\\you\\Documents\\notes"
      ]
    }
  }
}
```

macOS/Linux users replace the last argument with `~/Documents/notes` and
*don't* need the doubled backslashes. Only Windows paths need `\\` inside
JSON strings.

Read it back to yourself in plain English: *"run npx, auto-yes the package
download, use the filesystem server, and limit it to my notes folder."*

### 3. Restart or reload the host

Completely quit the client (not just close the window) and reopen it. On
startup the host starts the server, asks for its tool list, and — usually —
shows it in a tools/extensions panel.

### 4. Prove it works

Ask the agent something that can only be answered with the tool:

```
"What's in my notes folder? List the files and the first line of each."
```

If the answer names *your actual files*, congratulations — the loop from
chapter 4 just ran in real life. Enjoy that. It never stops being a little
satisfying.

### 5. Watch it work (approval mode)

Right after a fresh setup, keep approval prompts **on**. You should see
requests like "filesystem-notes wants to read …". Approve, glance at the
result, repeat a few times. This is the calibration period for both of you.

## Other example shapes (same idea, different command)

A config file can hold many servers. Here are *shapes* you'll see — matching
your own client's documentation beats copying internet examples:

```json
{
  "mcpServers": {
    "filesystem-two-folders": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem",
               "~/Documents/notes", "~/Documents/reminders"]
    }
  }
}
```

The filesystem server accepts several folders — every extra folder is
another scope you're granting, so only add what the job needs.

A later chapter of your life may include a **local notes MCP server** —
one you own, described in
[Your first notes server](06-your-first-notes-server.md). Its config entry
will use exactly this same shape, with a different command.

## Editor clients (briefly)

Code editors with AI assistants use the same pattern, usually storing
`mcpServers` config in a `.json` settings file in a menu like
"Extensions / MCP / Servers." Everything else — restart, tool list, approval
prompts — behaves the same as the desktop chat client above. Once you've
done it once anywhere, you can do it everywhere.

## Getting out safely (undo guide)

Half of confidence is knowing the exit.

- **Remove a server:** delete its block from the config file, fully restart
  the host. Done — gone.
- **Disable without deleting:** some clients have a per-server on/off
  switch; otherwise comment out the block (JSON doesn't allow real
  comments, so move the block aside and keep valid JSON).
- **Kill a runaway server:** the server is an ordinary program; OS task
  manager shows it (often as an `npx`/`node` process). Closing the host
  normally stops it anyway.
- **Nuke from orbit:** delete the config edits from before your first
  change (that pre-flight backup habit, again).

## If it doesn't work

Deep breath. The three usual culprits, in order: a JSON typo (one missing
comma fails the whole file), the wrong path spelling, or the host not fully
restarted. [Troubleshooting](troubleshooting.md) has the full detective
guide.
