# Agents & MCP: A Friendly Handbook

A plain-English manual about AI agents and the Model Context Protocol (MCP),
written the way a friend would explain it: clearly, kindly, and never
condescending. It ships as Markdown docs plus a small static HTML site you can
build and read entirely on your own computer.

Written by [Dylan Asdale](https://dylanasdale.github.io) and published by
**Asdale Dynamics, LLC** — beginner-friendly AI education, books, and tools.

## Who it's for

- People who have heard the words "AI agent" and "MCP" and want a real
  explanation, not a hype cycle.
- Nurses, writers, small-business owners, and anyone who learns best from
  step-by-step instructions with zero status symbols attached.
- Readers who want to *try* agents safely before trusting them with anything
  that matters.

## What's inside

| Page | What you'll learn |
| --- | --- |
| [Start here](docs/index.md) | How to use this handbook |
| [What is an agent?](docs/01-what-is-an-agent.md) | Agents vs. chatbots, the act–observe loop |
| [Safe first uses](docs/02-safe-first-uses.md) | Notes, files, reminders — useful *and* low-stakes |
| [Permissions & safety](docs/03-permissions-and-safety.md) | Least privilege, approval prompts, sandboxing |
| [MCP concepts](docs/04-mcp-concepts.md) | Hosts, servers, tools — the "USB-C for AI" idea |
| [Desktop setup](docs/05-desktop-setup.md) | Step-by-step client configuration examples |
| [Your first notes server](docs/06-your-first-notes-server.md) | A gentle on-ramp to building your own MCP server |
| [Glossary](docs/glossary.md) | Every word, defined without the jargon fog |
| [Safety checklist](docs/safety-checklist.md) | A pre-flight list you can print |
| [Troubleshooting](docs/troubleshooting.md) | When it doesn't work, start here |

## Build the website

Everything runs on the Python standard library — no installs, no keys, no
accounts, nothing leaves your machine.

```bash
python3 scripts/build.py
```

That writes the finished site into `site/`. Open `site/index.html` in any
browser. The build also runs a self-check:

```bash
python3 scripts/build.py --check   # build to a temp dir + verify links
python3 scripts/build.py --serve   # build, then preview at http://localhost:8000
```

## Run the tests

The generator ships with a small stdlib-only test suite (unit tests for the
Markdown renderer plus site-level checks that every page builds and every
internal link resolves):

```bash
python3 scripts/test_build.py
```

## Repository layout

```
docs/           The handbook, one Markdown file per chapter
scripts/        build.py — markdown-to-HTML static site generator (stdlib only)
scripts/        test_build.py — tests for the generator
scripts/assets/ The stylesheet the build embeds and ships as styles.css
site/           Generated output (safe to delete; rebuild any time)
LICENSE         MIT, © 2026 Asdale Dynamics, LLC
```

## Requirements

Python 3.10 or newer. Nothing to install — the generator and its tests use
only the standard library, work fully offline, and never touch a network
except when `--serve` listens on your own localhost.

## A note on safety

This handbook deliberately teaches **local-first, low-stakes** uses first:
your notes, your files, your reminders. It contains no API keys, no personal
data, and no instructions that require handing anything sensitive to a cloud
service. When you're ready for more, the next step — described in chapter 6 —
is a small, friendly notes MCP server you can run yourself.

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 Asdale Dynamics, LLC.
