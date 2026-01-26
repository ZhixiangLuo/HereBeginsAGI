# HereBeginsAGI

HereBeginsAGI is an attempt to build **autonomous agents** that can **learn and evolve**, guided by **first principles**.

The north star is coherence: a small set of durable principles that can generate useful behavior across many situations—without accumulating a fragile pile of special cases.

## Vision

- **First principles first**: derive behavior from fundamentals whenever possible.
- **Minimum effective rules**: keep rules small, simple, and consistent.
- **Reality-driven evolution**: let real work shape what survives, what changes, and what gets deleted.

## Why this exists

Today’s AI improves on a slow, centralized cadence—often **6–12 months** between meaningful capability upgrades. It also tends to be **one-size-fits-all**: the same general behavior is shipped to everyone, regardless of individual goals, context, and lived experience.

We believe a plausible path toward AGI is **democratized**, **individualized** systems: foundation models (LLMs and beyond) are already powerful, but what’s missing is a surrounding **system** that can **learn and evolve** through use. Like humans, different agents may be guided by different principles—while sharing the same underlying structure.

## Status

This project is in its early phase and will evolve rapidly. The direction is clear; the system mechanics and structure will continue to change.

## Collaboration

Right now, HereBeginsAGI is maintained by me and shaped by my experience. I plan to open it up for collaboration as the system matures.

## Prereqs

- **Cursor**: this repo is designed to be used via Cursor rules.
- **Rule loading mechanism**: Cursor loads `.mdc` rule files placed in `.cursor/rules/`.

## How it works (in practice)

The “source of truth” lives in two always-on rule files:

- `core-principles/01-problem-solving.mdc`: universal problem-solving methodology
- `core-principles/02-continuous-learning.mdc`: continuous learning (kept intentionally minimal; evolves over time)

When these files are present in a project’s `.cursor/rules/`, Cursor will load them automatically for every task.

### Use in other repos/projects

See `setup.md` for the exact steps (symlinks + quick verification) and how to bootstrap a `project_diary.md`.

## Repo contents

- `core-principles/`: the always-on principles (source of truth)
- `setup.md`: how to link HereBeginsAGI into any Cursor project (instructions live here)
- `project_diary.md`: chronological project record (what happened / why / how / future impact)
- `LICENSE`: MIT license

