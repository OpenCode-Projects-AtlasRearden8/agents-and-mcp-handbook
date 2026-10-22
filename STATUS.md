# STATUS.md

## What was built

**"Agents & MCP: A Friendly Handbook"** — a beginner manual explaining AI
agents and the Model Context Protocol in plain English, published as Markdown
docs plus a static HTML site generated from them. By Dylan Asdale /
Asdale Dynamics, LLC.

### Contents (`docs/`, 10 pages + README)

1. `index.md` — Start Here: how to use the handbook, ground rules
2. `01-what-is-an-agent.md` — chatbot vs. agent, the act–observe loop,
   model/tool/agent distinctions, what agents are good and bad for
3. `02-safe-first-uses.md` — safe real uses: notes, file tidying, reminders,
   with "show me first" patterns and backup habits
4. `03-permissions-and-safety.md` — least privilege, scoping, approval
   prompts, backups, what *not* to connect to agents
5. `04-mcp-concepts.md` — hosts, servers, tools, resources, prompts; the
   "USB-C for AI" framing and request flow
6. `05-desktop-setup.md` — step-by-step desktop-client setup: config-file
   shape, a complete filesystem-server example, restart/tools/approval
   verification, an undo guide
7. `06-your-first-notes-server.md` — on-ramp to building/owning a notes MCP
   server, positioning readers for the sibling **notes-mcp-server** project
8. `glossary.md` — plain-English A–Z definitions linking back to chapters
9. `safety-checklist.md` — printable pre-flight checklist
10. `troubleshooting.md` — five common failure modes with evidence-gathering

### Site generator (`scripts/`)

- `build.py` — stdlib-only static site generator: a small Markdown renderer
  (headings, paragraphs, fenced code, tables, ordered/unordered **and
  checkbox** lists, blockquotes, rules, inline styles, links with automatic
  `.md` → `.html` conversion), sidebar navigation, prev/next paging,
  accessibility basics (skip link, aria labels, semantic HTML).
  CLI: `--out DIR`, `--check` (build + verify), `--serve` (local preview).
- `assets/style.css` — warm, readable typography, responsive layout.
- `test_build.py` — 17 unit tests covering inline rendering, block
  structures, escaping, link conversion, full-build output, and the check.

### Other files

- `LICENSE` — MIT, copyright line exactly
  `Copyright (c) 2026 Asdale Dynamics, LLC`.
- `README.md` — overview, chapter table, build instructions; credits
  Asdale Dynamics, LLC. No secrets, API keys, or personal data anywhere.
- `.gitignore` — ignores `site/`, `__pycache__/`, build droppings.

## How to run it

```bash
python3 scripts/build.py                 # build site/ and run self-checks
python3 scripts/build.py --out /tmp/site # build elsewhere
python3 scripts/build.py --serve         # build + preview at http://127.0.0.1:8000
python3 scripts/test_build.py            # run the test suite
```

Python 3.10+ (tested on 3.13). No dependencies, no network needed, no keys.

## Verification results

All run in this workspace, 2026-10-22:

- `python3 scripts/test_build.py` — **17/17 tests pass**.
- `python3 scripts/build.py` — builds 10 pages; self-check reports
  *"All checks passed: pages built, links resolve, structure valid."*
  The check verifies: every listed page renders, every internal href/src
  resolves, no unresolved code-block placeholders, no docs links to
  unlisted pages, H1 present on every page.
- Duplicate build to a second output dir also passed.
- All generated HTML verified tag-balanced via an `html.parser` walk
  (no unclosed/misnested tags).
- Preview server (`--serve --port 8123`) verified with curl: HTTP 200 on
  `index.html` (~10.4 KB) and `styles.css` (~5.2 KB).
- One defect found and fixed during testing: fenced code blocks were being
  wrapped in `<p>` and quote characters weren't escaped in code output;
  both corrected, then re-verified by the suite.

## Git

Initialized locally, single commit on `main`
(`f126707 "Add Agents & MCP handbook: docs, static site generator, and tests"`).
Committed as the existing identity, no co-author trailers, nothing pushed.

## Known gaps / next steps

- The Markdown renderer covers the constructs this handbook uses; it does
  not implement the full CommonMark spec (e.g. nested lists, reference
  links, footnotes). Tests document exactly what is supported.
- The exact client menus in chapter 5 will drift between app versions;
  the config-file *shape* is stable, but specific screenshots weren't
  included by design (no product endorsements).
- The `--serve` preview binds to `127.0.0.1` only — intentional, local-first.
- No generated-site analytics, no external requests, no CI configured (repo
  is local-only per instructions; a CI workflow is an easy add later).
- Sibling project **notes-mcp-server** is referenced as the natural next
  step in chapter 6 but does not exist yet in this task's scope.
