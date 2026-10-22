# What Is an Agent?

## Start with what you know: a chatbot

You've probably chatted with an AI before. You type a question, it types an
answer. It's like emailing a very well-read librarian: helpful, but strictly
limited to *talking*.

```
You:  "What should I put in a shopping list for making soup?"
AI:   "Here's a classic mirepoix-based soup list: onions, carrots..."
```

Notice what happened after that answer: *you* still had to do everything. The
AI can't open your notes app, can't tick anything off, can't write the list
into a file. It spoke. That's all.

## An agent is a chatbot with hands

An **AI agent** is the same kind of AI — same model, same way of thinking —
but connected to **tools** it can use while working on your request. Tools are
the hands. They might let the agent:

- read and write files in a folder
- search notes for a keyword
- set a reminder or calendar entry
- look something up on the web
- run a tiny, approved command

So the same request becomes:

```
You:  "What should I put in a shopping list for making soup?"
Agent: [thinks] This belongs in the user's shopping list.
Agent: [uses tool: read file] → shopping-list.txt currently says "milk, eggs"
Agent: [uses tool: write file] → adds onions, carrots, celery, broth
Agent: "Added soup ingredients to shopping-list.txt."
```

The agent didn't just *tell* you — it *did* it. That's the whole idea.

## The act–observe loop

Agents work in a simple rhythm you can predict once you've seen it once:

1. **Goal.** You give a request: "Save this recipe to my recipes folder."
2. **Think.** The agent decides which steps make sense.
3. **Act.** It uses a tool — maybe writes the file.
4. **Observe.** It checks the result. Did the write succeed? What did the
   file look like after?
5. **Repeat or finish.** If more steps are needed, it loops back. When
   you're satisfied, it reports back and stops.

A good mental picture: a careful assistant who keeps glancing at their work
after each step. A *careless* assistant barrels ahead without looking — and
agents differ in exactly that way, which is why permissions (chapter 3)
matter so much.

## Three words people mix up

- **Model** — the brain. The thing that "understands" language. ChatGPT,
  Claude, a local Llama file — these are models.
- **Tool** — one specific ability, like "write a file" or "search notes."
- **Agent** — a model plus tools plus a loop that gets things done.

You'll meet this same trio again in the MCP chapter, because MCP is the
standard way agents get handed tools — like an extension cord for abilities.

## What agents are *not*

It's worth being clear about the noise you may have heard:

- **Not magic.** An agent with a bad plan produces bad results confidently.
  "Confident" and "correct" are different words.
- **Not self-improving overlord software.** Your soup-list agent is not
  plotting. It does what you asked, in the tools you gave it, then stops.
- **Not all-or-nothing trust.** You choose which tools it gets. An agent that
  can only read your notes folder physically cannot touch anything else.
  That's the design we'll push in chapter 3.
- **Not a replacement for judgment.** It's a very fast assistant, and
  assistants need direction — and occasionally supervision.

## A taste of what agents are good for

Real examples, sized honestly:

- **Notes.** "Find every note that mentions the pharmacy and add a summary
  line to the top."
- **Files.** "Sort everything in my Downloads folder into subfolders by type;
  ask me before moving anything."
- **Reminders.** "When I say 'remember to call the eye doctor', put it on a
  reminders list with today's date."
- **Writing.** "Read chapter drafts in this folder and list every section
  missing a heading."

## What agents are *bad* for (for now)

- Anything where a mistake is expensive: sending money, deleting the only
  copy of something, medical or legal decisions.
- Situations where you can't see what it did. If you can't review the work,
  don't hand over the work.
- Things that need taste and accountability. It can draft; *you* decide.

The pattern you should notice: agents shine at **visible, fixable, local**
work — and that's exactly where the next chapter starts.
