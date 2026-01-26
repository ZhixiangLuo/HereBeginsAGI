# Project History

Chronological log of work activity, decisions, implementations, fixes, and ideas discussed.

Diary guidance (principle + lightweight prompts) lives in `core-principles/02-continuous-learning.mdc`.

---

## Writing principle

This is a diary, not a form. Write in a way that makes it easy to revisit later:
- What happened, why, and how
- What changed (files/decisions)
- Anything that might matter in the future (constraints, risks, follow-up ideas)

Append new entries at the bottom in chronological order (oldest → newest).

## 2026-01-26 14:00

Renamed the repository from "dragon training" to "HereBeginsAGI" to better reflect the project's purpose and scope. The new name emphasizes the beginning of AGI development and learning systems.

Started establishing the project structure and documentation:
- Created core principles documentation in `core-principles/` (`core-principles/01-problem-solving.mdc`, `core-principles/02-continuous-learning.mdc`)
- Initialized this project diary to track ongoing work and decisions

The project focuses on building autonomous AI agents with learning capabilities, following principles of independent thinking, holistic problem-solving, and continuous evolution through experience.

## 2026-01-26 16:10

Made `HereBeginsAGI` a clean, core-only system and clarified the separation between problem-solving vs learning (including how to write the project diary).

Context / decisions:
- Core principles are now two always-loaded files: `core-principles/01-problem-solving.mdc` and `core-principles/02-continuous-learning.mdc`.
- Removed `domains/` and `projects/` to keep the repo focused on building the system itself.
- Assumption: domain/project-specific guidance can be reintroduced later as optional extensions when repeated evidence shows it’s needed.
- Open question: how much “system usage by others” belongs in `setup.md` vs referencing core only.

Changes made:
- Core refactor:
  - Removed `core-principles/00-principles.mdc` and folded remaining behavioral guidance into `core-principles/01-problem-solving.mdc`.
  - Expanded `core-principles/02-continuous-learning.mdc` into three tracks:
    - Fast iteration of execution documents (learning log + assumption lifecycle)
    - Project diary guidance (where/when/principle)
    - Slow, evidence-based core evolution (guardrails + safe evolution loop)
- Repo cleanup:
  - Removed `domains/` and `projects/` entirely (core-only for now).
  - Updated `setup.md` and Cursor rule wiring to reflect core-only structure and remove stale references.
  - Updated `project_diary.md` header and clarified where diary guidance lives.

Verification:
- Confirmed repo structure is core-only and documentation is consistent.

Notes for later:
- Keeping the repo “core-only” reduces maintenance overhead and forces higher-quality core abstractions.
- The separation “problem-solving behavior” vs “learning behavior” is useful: problem-solving stays stable and universal; learning covers doc iteration, diary, and careful evolution.

- Open loops (snapshot, not a task tracker):
  - Decide how minimal `setup.md` should be (e.g., keep high-level summaries vs reference-only to `core-principles/`).
  - When you start applying the system to a concrete domain/project again, reintroduce extensions with evidence-driven scope.

## 2026-01-26 18:00

Finalized core-only wiring for Cursor and made onboarding docs operationally complete. Also aligned the diary convention to chronological order (append new entries at the bottom).

What’s true now:
- Cursor loads rules for this repo from `HereBeginsAGI/.cursor/rules/`.
- Symlinks to the two core files are present in `.cursor/rules/` so they load automatically in this repo.
- Repo-specific intent should stay minimal and not duplicate core methodology.

Changes made:
- Documentation:
  - Replaced the repo entry doc with `setup.md` as the onboarding guide for using HereBeginsAGI in a new project.
  - Expanded `setup.md` to include: symlink setup patterns and the operational step to create `project_diary.md` in new repos.
- Cursor wiring:
  - Removed `.cursorrules` (one-time operational pointers).
  - Added `.cursor/rules/00-repo.mdc` to capture repo scope only (work on improving the system itself) and point to core.
  - Ensured `.cursor/rules/01-problem-solving.mdc` and `.cursor/rules/02-continuous-learning.mdc` resolve to the core rules.
- Diary:
  - Switched diary convention to chronological order (append entries at the bottom).
  - Updated guidance in `core-principles/02-continuous-learning.mdc` and `setup.md` to match.

Verification:
- Confirmed repo contains only: `core-principles/`, `.cursor/rules/`, `setup.md`, `project_diary.md`.
- Confirmed `.cursor/rules/01-problem-solving.mdc` and `.cursor/rules/02-continuous-learning.mdc` can be read and match core content.

Notes for later:
- Keeping repo-scoped intent in a tiny `.cursor/rules/00-repo.mdc` avoids polluting the always-on core.
- Operational completeness: setup isn’t complete unless the diary exists in the new repo.
