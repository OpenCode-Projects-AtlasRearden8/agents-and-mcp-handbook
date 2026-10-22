# Permissions & Safety

Here's the slightly scary truth about agents: a tool that can write files can
write *wrong* files. The slightly wonderful truth: permissions exist, they
work, and setting them up well takes minutes. This chapter is the minutes.

## The core principle: least privilege

**Least privilege** means: give the agent exactly the abilities it needs for
the job, and nothing more. A cleaner who only needs to polish the kitchen
gets a kitchen key — not the master key to the house.

In practice, that means thinking in two axes:

| | **Read** (look) | **Write** (change) |
| --- | --- | --- |
| **Where** | which folders? | which folders? |
| **What** | file types, search | create, edit, delete |

An agent asked to summarize notes needs *read* on the notes folder, usually
*write* on one summary file — not delete, not other drives, not "everything."

## The four safety tools you actually use

### 1. Scoping (the big one)

Most desktop clients let you choose *which folders* a tool can touch. This
one setting does most of the work of safety:

- Good: `C:\Users\you\Documents\notes` (or `~/Documents/notes`)
- Nervous-making: your whole user folder, your whole Documents tree
- Bad: system folders, root of a drive ("just in case")

Narrow scope means mistakes stay small. A write-only-to-one-folder agent
physically cannot scramble anything else.

### 2. Approval prompts

Clients typically offer a middle mode: **the agent proposes, you approve.**
Every file write gets a dialog — "Agent wants to create `soup-plan.md`?
[Allow] [Deny]."

- **Start here.** Deny-what-looks-wrong trains you and the agent both.
- As trust builds, switch specific, well-tested actions to auto-allow.
- One-click "Always allow for this folder" is fine *after* a few days of
  clean behavior.

### 3. Backups

Not glamorous, unbeatable. Two kinds:

- **Before experiments:** copy the folder. `notes-backup-2026-10-22/`. 
- **Always, quietly:** any OS-level backup (Windows File History, Time
  Machine, a sync tool with versioning). If you have one, you've already
  paid the insurance premium; use the coverage.

### 4. The "show me first" habit

Already introduced in chapter 2, worth repeating as a *permission*: ask the
agent to propose before it acts. "Show me the plan," "list the files you
*would* change," "print the first three." You are the approval layer too.

## Reading a permission dialog like a pro

When a client asks "Allow this tool?", the useful questions are:

1. **What folder(s)?** Does the path make sense for what I asked?
2. **What action?** Read-only for research is very different from write.
3. **Once or forever?** "Always allow" is a real decision, not a dismissable
   popup.

If a dialog says the agent wants write access to somewhere you never
mentioned — that's not scary, that's *scope creep*, and it earns a Deny and
a reworded request.

## Things agents shouldn't touch (yet)

A short, non-flexible list for your first months:

- Anything with money: banking, invoices with payment details, tax stuff.
- Anything identity-ish: passwords, ID scans, insurance portals.
- Anything medical (your job or others'): the handbook's audience includes
  healthcare workers; the rule is education and organization, **never
  clinical decisions or protected patient data.** If info is regulated,
  it doesn't go near your agent until you've asked someone whose job is
  compliance.
- The only copy of anything.

None of this is permanent prohibition. It's beginner-speed. After months of
clean operation you'll know exactly what does and doesn't deserve access —
which is the actual skill.

## The two-minute pre-flight

Every new tool gets this checklist:

- [ ] Folder scope is as narrow as the task allows
- [ ] Write access only where needed — or off entirely
- [ ] Approval prompts ON for new tools
- [ ] Backup copied
- [ ] First request phrased as "show me, then ask"

Full printable version lives in the
[Safety checklist](safety-checklist.md). Copy it into your notes; that's
very on-brand for this whole handbook.

---

Next: the plumbing that connects agents to those tools in any app you use —
[What is MCP?](04-mcp-concepts.md)
