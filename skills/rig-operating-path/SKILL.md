---
name: rig-operating-path
description: Use when asked to map, simplify, repair, or prove an end-to-end repository operating path; when a workflow succeeds only after retries, fallbacks, restarts, manual fixes, duplicate actions, wrong-owner detours, or lower-level shortcuts; or when deciding whether reliability machinery preserves proven behavior or hides a broken route. Do not use for an isolated code, test, lint, CI, or refactoring problem with no operating-route, ownership, authority, side-effect, or end-to-end proof question.
---

# Rig Operating Path

Help the user make one repository workflow complete its exact goal through the intended route, cleanly from the correct first action.

## First action

Before making path-affecting changes or claiming success, write a concise operating-path definition with:

1. exact goal;
2. actor;
3. starting state;
4. correct first action;
5. owner route;
6. meaningful state transitions;
7. side effects;
8. authority boundaries;
9. completion point;
10. authoritative readback;
11. acceptance criteria; and
12. disqualifying deviations.

Scope the path to one actor, goal, starting condition, and owner route. Split broader claims into separate paths.

Establish the intended route from evidence in this order:

1. explicit user intent and constraints;
2. the documented user-facing contract;
3. the owning component's API, command, or state contract; and
4. current implementation evidence.

Do not invent a “correct” route. If authoritative sources conflict, state the conflict and use `Not confirmed` until the user or owning contract resolves it.

## Working loop

1. Determine whether the user asked for assessment, diagnosis, implementation, or proof. Do not implement during assessment or diagnosis unless the user also asked for a change.
2. Define the intended path before execution.
3. Enumerate consequential side effects before running the path. Run the real operation only within the user's authorization. Require explicit authorization for irreversible, external, credential, production, release, migration, billing, or destructive actions. Prefer a disposable or non-production environment only when it preserves the route semantics being proved. Do not substitute a lower-level shortcut.
4. Reconstruct the complete available execution record and read the resulting state directly from its authoritative owner surface.
5. Compare intended and actual routes and identify the earliest meaningful divergence.
6. Classify it as a path, ownership, contract, implementation, evidence, environment, or operator defect. Keep incidental findings separate.
7. Repair or simplify at the earliest owner-controlled boundary. Treat downstream symptoms as evidence until that cause is removed.
8. Rerun the complete path from a clean start.
9. Report one verdict: `Confirmed`, `Not confirmed`, or `Failed`.

Read [the operating-path method](references/operating-path-method.md) when defining a non-trivial path, classifying a divergence, or choosing a simplification.

Read [the proof protocol](references/proof-protocol.md) when the user asks to validate, confirm, prove, test end to end, or decide whether preservation machinery is earned.

Use [the templates](references/templates.md) when a durable path definition, finding, proof report, or lesson record will help the user or a later executor.

## Non-negotiable distinctions

- Eventual outcome success is not operating-path success.
- A generated success label is a claim, not proof.
- A user-described scenario may support a diagnosis of the path as reported, but it does not confirm the live runtime without primary execution evidence and authoritative readback.
- Missing or contradictory execution evidence produces `Not confirmed`.
- A proven route deviation or unmet goal produces `Failed`, even if a later attempt succeeds.
- Each proof run has its own verdict. An unmodified retry remains part of the failed attempt; a post-repair clean rerun is a new proof and may be `Confirmed`.
- Tests, linting, gates, retries, fallbacks, compatibility routes, detectors, and telemetry are preservation or boundary mechanisms. They do not substitute for repairing the core route.

## Repair standard

Prefer fewer accepted states, branches, owner transitions, result meanings, duplicate signals, compatibility translations, and manual decisions. Make authority and completion boundaries clearer.

Do not broaden the task to fix incidental findings. Do not add reliability machinery unless a clean, stable path is already known and a concrete remaining boundary or failure justifies it.

## Output

Return a self-contained operating-path packet with:

- intended route;
- actual route and evidence;
- earliest divergence and classification;
- owner able to remove it;
- repair or simplification made or recommended;
- complete clean-rerun result;
- reported-path assessment when working from a scenario;
- runtime proof verdict and limiting conditions; and
- any preservation mechanism that is now earned, or an explicit statement that none is.
