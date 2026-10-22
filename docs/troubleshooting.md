# Troubleshooting

When something doesn't work, it's usually one of five boring causes. This
page lists them in the order they occur in real life, with friendly
evidence-gathering at each step. Nothing here needs reinstalling anything.

## Problem 1: My server doesn't show up in the host

**Symptoms:** tools panel is empty, agent says "no tools available," the
extension list has no entry with your name on it.

**Check, in order:**

1. **Config file syntax.** One missing comma or an unquoted path in JSON
   fails the *whole file*, so *every* server vanishes, not just yours. Paste
   the file into any JSON validator (many free, browser-based, work fully
   offline on a small file) or eyeball:
   - every key and string in double quotes?
   - commas between entries, none after the last one?
   - braces balanced — count `"` pairs if feeling skeptical?
2. **Path spelling.** Windows paths need doubled backslashes inside JSON
   (`"C:\\Users\\you\\..."`). macOS/Linux use `~/...` and forward slashes.
   Try pasting the path into a file manager's address bar — if it doesn't
   open, it's spelled wrong, not configured wrong.
3. **Full restart.** Not closing the window — actually quitting the host
   app (check the taskbar/tray, give it two honest seconds) and reopening.
   Servers start at host startup, not while you watch.

**When fixed:** the tools panel lists your server. If it does and tools
still don't fire, see Problem 2.

## Problem 2: Server connects, but tools don't do anything

**Symptoms:** the extension shows as connected/running, but the agent says
it can't find files, or actions quietly don't happen.

**Check:**

1. **Ask a tool-only question.** "List the files in my notes folder" — a
   request the model could answer *without* tools only by guessing, so a
   correct answer here proves the loop is wired.
2. **Approval mode is too strict.** An unanswered approval dialog can park
   silently behind a window. Check for stacked dialogs.
3. **Scope mismatch.** The server only sees folders you gave it. If it
   "can't find" a file, confirm the file is inside the folder path from the
   config — locations outside the scope are invisible by design. That's
   chapter 3 doing its job.
4. **First run downloading.** The first `npx` run downloads a package and
   can take a minute or two on slow connections. Wait once; it's instant
   every time after.

## Problem 3: The agent did something I didn't expect

**Symptoms:** a file changed, a note got mangled, something moved.

**Check:**

1. **Restore the backup.** This is why the pre-flight checklist exists;
   copy the backup back, adjust the request.
2. **Re-read the request you actually sent.** Ambiguity is the usual
   culprit: "clean up my notes" is a wish, not a spec. Compare to
   "list files in notes/ that contain the word DRAFT, print the plan, ask
   before touching."
3. **Tighten scope first, phrasing second.** If the mismatch was *where* it
   acted, shrink the config path before re-wording anything.

## Problem 4: A tool is slower or noisier than expected

**Check:**

1. **First-run download** (again, for Problem 2 — most "slowness" is this).
2. **Many servers at once.** Each config entry is a program that starts and
   keeps running with the host. Trim entries you're not using — the exit
   guide in chapter 5 is one delete plus one restart.
3. **Huge folders.** A "list everything in my 10,000-file drive" request is
   a *you* problem the tool will faithfully attempt. Scope the folder, not
   the request.

## Problem 5: I want to start over from a clean slate

**Do:**

1. Remove all server blocks from the config file (keep a copy of the file
   first — it's tiny).
2. Fully restart the host.
3. Add one server back. Test it with one small request.
4. Repeat, one at a time, only keeping what earned its place.

Clean-slate syndrome is common, harmless, and — honestly — sometimes the
fastest route to a setup you understand completely.

## The reading-the-error habit

Real errors usually contain the answer:

- `ENOENT` or "no such file" → a path is misspelled (Problem 1 / 2).
- Unexpected end of JSON input → syntax (Problem 1).
- "Tool not found" / tool name mismatch → server connected but the request
  named a tool it doesn't provide; ask "what tools do you have?" — hosts
  will list them honestly.

And the meta-rule of this whole page: **change one thing, retest, then
change the next.** Two simultaneous "fixes" leave you unable to tell which
one worked — or broke something.
