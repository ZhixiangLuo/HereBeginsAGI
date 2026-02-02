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

## 2026-01-26 20:10

Shipped the first public version of HereBeginsAGI and tightened the repo into a clean “first-principles + learning” foundation.

What changed:
- Naming cleanup:
  - `core/` → `core-principles/`
  - `02-learning.mdc` → `02-continuous-learning.mdc`
- Diary guidance:
  - Removed rigid templates and “follow-ups” as a default (to avoid stale TODOs); kept diary as lightweight narrative record-keeping.
- Public readiness:
  - Wrote/iterated `README.md` to be more ambitious (autonomous agents that learn/evolve; first-principles framing; “why this exists”) while keeping learning mechanics intentionally high-level.
  - Added MIT `LICENSE`.
  - Added `HereBeginsAGI/.gitignore` and ignored `.cursor/` (so Cursor wiring stays an integration concern, not a tracked artifact).
- Release:
  - Created `ZhixiangLuo/HereBeginsAGI` and pushed `main` to GitHub.

Future impact:
- Because `.cursor/` is ignored, consumers should follow `setup.md` rather than expecting repo-internal Cursor wiring to exist in the public repo.
- Collaboration policy can evolve later (issues/PRs are the current “surface area”).

## 2026-01-26 20:40

Updated onboarding to avoid symlink-based Cursor rules because symlinked `.mdc` files are not reliably auto-loaded.

What changed:
- Updated `setup.md` to recommend **literal file copy** (`cp -f ...`) into the consumer repo’s `.cursor/rules/` (separate-folder and monorepo options).
- Added an explicit note that “copy” means `cp` (not manually recreating files by pasting contents).

Applied to OrcaEcho workspace:
- Copied `core-principles/01-problem-solving.mdc` and `core-principles/02-continuous-learning.mdc` into `/Users/zhixiangluo/git_repos/OrcaEcho.ai/.cursor/rules/` so Cursor auto-loads them for the workspace.

Future impact:
- Any upstream updates to core principles now require re-running the copy step in downstream repos/workspaces (manual sync, but reliable loading).

## 2026-02-02

Synced HereBeginsAGI core-principles from OrcaEcho.ai workspace `.cursor/rules/` (workspace had newer content).

What changed:
- **01-problem-solving.mdc**: Added “Complete the Change and Verify It Takes Effect” under Operating Principles (perform follow-up action so change is applied; verify it took effect; no dangling handoffs).
- **02-continuous-learning.mdc**: Added “Scope of ‘rules’” (Core vs workspace rules vs repo rules; how to choose target by scope). Added “Reflect and update rules (agent flow)” (reflect → identify target → draft → apply or propose; “update the rules” means making the edit, not only suggesting).

Verification:
- Compared `.cursor/rules/01-problem-solving.mdc`, `02-continuous-learning.mdc` with HereBeginsAGI `core-principles/`; applied missing sections to HereBeginsAGI. Did not copy `03-workspace-rules.mdc` (OrcaEcho-specific).

Future impact:
- HereBeginsAGI remains source of truth for the two core files; workspaces that copied from HereBeginsAGI should re-copy after core updates if they want the latest.
