# HereBeginsAGI Setup (Cursor)

This file explains how to incorporate HereBeginsAGI into your Cursor setup.

## Source of truth

Cursor does **not reliably auto-load symlinked** rule files. So for new repos/projects, the recommended setup is to **copy** the rules into that repo’s `.cursor/rules/`.

Treat these files as the source of truth (the “upstream” you periodically re-copy from):

- `core-principles/01-problem-solving.mdc` (always on): universal problem-solving methodology
- `core-principles/02-continuous-learning.mdc` (always on): continuous learning system (execution doc iteration, project diary, careful core evolution)

## Setup in a Cursor project

From the root of *your* project, put the core rules in `.cursor/rules/` as **real files** (copied, not symlinked).

Important: “copy” here means a **literal file copy** (e.g. `cp -f ...`), not copy/pasting the contents into a new file by hand.

### Option A: HereBeginsAGI is in a separate folder (recommended)

Use absolute paths so you can reuse one HereBeginsAGI checkout across many repos:

```bash
mkdir -p .cursor/rules
HERE_BEGINS_AGI="/absolute/path/to/HereBeginsAGI"

# (Re)copy the two always-on rules
cp -f "$HERE_BEGINS_AGI/core-principles/01-problem-solving.mdc" .cursor/rules/01-problem-solving.mdc
cp -f "$HERE_BEGINS_AGI/core-principles/02-continuous-learning.mdc" .cursor/rules/02-continuous-learning.mdc
```

That’s it. Cursor will load the `.mdc` rules for every task.

### Notes (recommended)

- Option B (monorepo): if `HereBeginsAGI/` lives **inside** your repo (e.g. at `./HereBeginsAGI/`), copy from the local path (portable across machines):

```bash
# Example: your repo contains ./HereBeginsAGI/
mkdir -p .cursor/rules
cp -f ./HereBeginsAGI/core-principles/01-problem-solving.mdc .cursor/rules/01-problem-solving.mdc
cp -f ./HereBeginsAGI/core-principles/02-continuous-learning.mdc .cursor/rules/02-continuous-learning.mdc
```

- If you rerun the commands and the files already exist, overwrite with `cp -f ...`.
- If you update the core principles, re-run the copy commands to sync downstream repos.

### Quick verification

From your project root:

```bash
ls -la .cursor/rules
```

You should see `01-problem-solving.mdc` and `02-continuous-learning.mdc` as real files (not symlinks).

### This repo (HereBeginsAGI)

If you want the rules to be active when working *inside* the HereBeginsAGI repo itself, copy them into `HereBeginsAGI/.cursor/rules/`:

```bash
mkdir -p .cursor/rules
cp -f ./core-principles/01-problem-solving.mdc .cursor/rules/01-problem-solving.mdc
cp -f ./core-principles/02-continuous-learning.mdc .cursor/rules/02-continuous-learning.mdc
```

## Create your project diary

In the new repo, create a `project_diary.md` for record-keeping. Use the diary guidance in `core-principles/02-continuous-learning.mdc`.

Minimal starter:

```markdown
# Project History

Chronological log of work activity, decisions, implementations, fixes, and learnings.

Diary guidance (principle + lightweight prompts) lives in HereBeginsAGI `core-principles/02-continuous-learning.mdc`.

---

## Entries

Append new entries at the bottom in chronological order (oldest → newest).
```

## How to use in practice

- Use `core-principles/01-problem-solving.mdc` as the default operating method for every task.
- Use `core-principles/02-continuous-learning.mdc` to:
  - iterate execution docs quickly (learning log + assumption lifecycle)
  - write/update `project_diary.md`
  - evolve the core slowly and carefully (evidence-based changes)

## Notes

- This repository is intentionally **core-only** right now. If you later apply the system to a specific domain/project, add extensions only when repeated evidence shows they’re needed.
