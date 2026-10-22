# Safe First Uses: Notes, Files, Reminders

The fastest way to trust an agent is to watch it work on something where a
mistake costs you a shrug. This chapter is your starter menu: three uses that
are genuinely useful, run entirely on your machine, and are nearly impossible
to have a disaster with.

## Why these three

Notes, personal files, and reminders share four properties that make them
perfect for a first agent:

1. **You already have backups or can make one in a minute.** Copy a folder,
   zip it, done.
2. **Mistakes are visible.** A mangled note is not a silent failure — you'll
   see it and fix it.
3. **They involve *your own stuff*, nobody else's.** No privacy blast radius.
4. **They save real time every day.** This isn't practice on a toy; it's the
   actual chores.

## Use 1: A second brain for your notes

Give the agent a **notes folder** — plain text or Markdown files — and ask
things like:

```
"Search my notes folder for anything about the furnace filter
 and summarize what I've figured out so far."
```

```
"Create a new note called '2026-10-22 - saw ideas' with today's
 bullet points from our conversation, one per line."
```

```
"Every note tagged #project needs a one-line summary added
 under the title. Show me the first three before doing the rest."
```

That last one is important: **"show me first"** is the single most useful
phrase in agent work. Asking to see a sample before a bulk action turns a
risky step into a reviewable step.

## Use 2: A tidy-up helper for files

The Downloads folder is where files go to test your patience. Agents are
weirdly great at this chore:

```
"List what's in my Downloads folder, grouped by file type.
 Don't move anything yet — just show me the plan."
```

Then, after you like the plan:

```
"Okay, do it. Move images into Pictures/inbox, PDFs into
 Documents/inbox, and everything else stays."
```

Notice the safety pattern again: **plan first, approve, then act.** With a
good agent you can even ask it to keep a log of everything it moved, so a
mistake can be undone by reversing the list.

## Use 3: A reminder catcher

Reminders are where agents feel almost uncannily helpful, because the
request is tiny and the payoff is large:

```
"Whenever a message starts with 'remind me', append it to
 reminders.txt with today's date."
```

Then "remind me to reorder contacts" becomes a line in a file you check
daily. Is it a fancy to-do app? No. Is it reliable, local, completely yours,
and free of advertising? Yes — and that's the point.

A step up:

```
"Read reminders.txt, sort the lines by urgency word
 (today / this week / someday), and rewrite the file in that order."
```

## The scripts of repetition (write them down)

As you use an agent, you'll notice you ask similar things repeatedly. Save
those phrasings. A short `prompts.txt` next to your notes folder is an
honestly underrated productivity tool:

```text
# My agent sentences that work
- "Search notes for X and summarize."
- "Add today's date as a heading in diary.md."
- "Show me Downloads organized by type, then ask before moving."
```

Copy, paste, tweak. An agent's memory is yours to script — sentences you
already know work beat clever new ideas every time.

## The one rule of this chapter

**Stakes low, backups on.** Before any first run of a new agent against
files you care about:

1. Make a quick copy of the folder (or let the agent's tool read from a
   copy).
2. Run your request.
3. Compare. If it went wrong, restore the copy and adjust the request.

Ten seconds of copying beats ten minutes of regret, every time.

---

You now know what agents are and what to safely point them at. The next
chapter answers the question hiding under all of this: *how do I keep the
agent inside the lines I drew?* That's [Permissions & safety](03-permissions-and-safety.md).
