# HereBeginsAGI Setup (Cursor)

This file explains how to incorporate HereBeginsAGI into your Cursor setup.

## Source of truth

Do not copy rules into other places. Link these files and treat them as the source of truth:

- `core-principles/01-problem-solving.mdc` (always on): universal problem-solving methodology
- `core-principles/02-continuous-learning.mdc` (always on): continuous learning system (execution doc iteration, project diary, careful core evolution)

## Setup in a Cursor project

From the root of *your* project, put the core rules in `.cursor/rules/` as symlinks.

### Option A: HereBeginsAGI is in a separate folder (recommended)

Use absolute paths so you can reuse one HereBeginsAGI checkout across many repos:

```bash
mkdir -p .cursor/rules
HERE_BEGINS_AGI="/absolute/path/to/HereBeginsAGI"

# (Re)link the two always-on rules
ln -sf "$HERE_BEGINS_AGI/core-principles/01-problem-solving.mdc" .cursor/rules/01-problem-solving.mdc
ln -sf "$HERE_BEGINS_AGI/core-principles/02-continuous-learning.mdc" .cursor/rules/02-continuous-learning.mdc
```

That’s it. Cursor will load the linked `.mdc` rules for every task.

### Notes (recommended)

- Option B (monorepo): if `HereBeginsAGI/` lives **inside** your repo (e.g. at `./HereBeginsAGI/`), prefer **relative** symlinks so the setup is portable across machines:

```bash
# Example: your repo contains ./HereBeginsAGI/
mkdir -p .cursor/rules
ln -s ../../HereBeginsAGI/core-principles/01-problem-solving.mdc .cursor/rules/01-problem-solving.mdc
ln -s ../../HereBeginsAGI/core-principles/02-continuous-learning.mdc .cursor/rules/02-continuous-learning.mdc
```

- If you rerun the commands and links already exist, overwrite with `ln -sf ...` (or remove the existing files first).
- Windows note: creating symlinks may require Admin privileges or enabling Developer Mode. If symlinks are painful on Windows, the fallback is to copy the files into `.cursor/rules/` (but copying is **not** source-of-truth and will drift).

### Quick verification

From your project root:

```bash
ls -la .cursor/rules
```

You should see `01-problem-solving.mdc` and `02-continuous-learning.mdc` as symlinks (or real files if you used the copy fallback).

### This repo (HereBeginsAGI)

This repository already wires itself by symlinking `core-principles/01-problem-solving.mdc` and `core-principles/02-continuous-learning.mdc` into `HereBeginsAGI/.cursor/rules/`.

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
