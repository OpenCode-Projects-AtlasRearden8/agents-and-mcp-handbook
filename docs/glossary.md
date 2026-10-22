# Glossary

Plain-English definitions, alphabetized. When a term links to a chapter,
the chapter shows it in action.

## A

**Agent** — An AI model connected to tools, working through your request in
a loop: think, act, observe, repeat. A chatbot with hands. See
[chapter 1](01-what-is-an-agent.md).

**API key** — A long secret string that identifies you to a cloud service.
This handbook uses none, but you'll meet the term in wider reading.

**Approval prompt** — A dialog asking "allow this?" before the agent acts.
Your middle-speed safety knob. See
[chapter 3](03-permissions-and-safety.md).

## B

**Backup** — A second copy of your files from before an experiment.
Ten seconds of copying beats ten minutes of regret.

**JSON** — A text format for settings and data, written with braces and
quotes. Human-editable if you're careful with commas.

## C

**Command** — In an MCP config, the program to run to start a server
(e.g. `npx`). Part of the "command + args" recipe.

**Config file** — A settings file. MCP hosts read an `mcpServers` config to
know which servers to start.

## H

**Host** — The app you use — the desktop client, editor panel, or assistant
UI where you type requests. The place servers get attached. See
[chapter 4](04-mcp-concepts.md).

## L

**Least privilege** — The safety principle of granting only the access a
task needs, nothing more.

**Local-first** — Software that keeps your data on your machine. The whole
point of this handbook's approach.

**Loop (act–observe)** — The agent rhythm: plan, use a tool, look at the
result, continue or finish.

## M

**MCP (Model Context Protocol)** — A standard way for AI apps (hosts) to
talk to tools (servers); "USB-C for AI." See
[chapter 4](04-mcp-concepts.md).

**Model** — The AI "brain" that understands and writes language: ChatGPT,
Claude, local Llama. Distinct from the agent (model + tools) and the tool
(one ability).

## N

**Notes folder** — A folder of plain-text/Markdown notes; the handbook's
favorite first target for an agent.

## P

**Permission** — A rule about what a tool may read or write, and where.

**Plain text** — A file format humans can read directly (`.txt`, `.md`)
with no special app. Ideal for agent work because it survives everything.

**Prompt** — Two meanings, context decides: (1) your request; (2) a saved
template a server offers to host apps.

## R

**Resource** — In MCP, data a server *offers* (for reading), as opposed to
a tool, which *acts*. See [chapter 4](04-mcp-concepts.md).

## S

**Sandboxing** — Restricting software to a limited area so it can't wander.

**Scope** — The specific folders/file-types a tool may touch. The single
most useful safety setting.

**Server (MCP server)** — A small program on your machine that offers tools
to a host. Not a humming basement rack; just "a helper process."

## T

**Tool** — One named ability a server offers, like `search_notes(query)`.
The agent's hands.

## U

**Undo guide** — The steps to remove what you added (see chapter 5's
"Getting out safely"). Anyone who writes guides should include one.
