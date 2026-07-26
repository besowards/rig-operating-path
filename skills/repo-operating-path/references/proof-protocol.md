# Proof Protocol

Use this protocol when the user asks to confirm that an operating path works.

## Before the run

State:

- the exact goal;
- correct first action;
- intended owner route;
- falsifiable acceptance criteria; and
- route disqualifiers.

Identify every agent, process, or system that can materially affect the outcome and the evidence surfaces each one produces.

Enumerate side effects and authority boundaries before execution. Require explicit user authorization for irreversible, external, credential, production, release, migration, billing, or destructive actions. A disposable or non-production environment is valid only when it preserves the behavior and boundaries the proof claims to exercise.

## Perform the real operation

Exercise the same entrypoint and conditions normal use depends on. Use unique content or identifiers when needed to distinguish the run from earlier activity. Allow the operation and its recording lifecycle to settle before judging it.

Do not pre-correct intermediate state or replace the normal path with a lower-level shortcut unless that lower-level surface is the stated subject of the proof.

A clean start means the declared starting conditions are true and no residual artifact from an earlier attempt can alter the route. Prefer fresh identifiers, fixtures, branches, workspaces, or disposable environments when they preserve real semantics. Do not reset, delete, or overwrite consequential state merely to manufacture a clean start without authorization.

## Evidence hierarchy

1. **Execution evidence:** the complete available event trace, tool transcript, agent-session record, logs, or equivalent for every materially participating actor.
2. **Result evidence:** direct readback from the authoritative application, API, database, filesystem, process, host, or external provider that owns the result.
3. **Navigation and corroboration:** status commands, process listings, screenshots, summaries, and derived views.
4. **Generated claims:** success labels, health fields, reports, and agent assertions.

Use lower layers to locate or explain proof, never to replace missing higher-layer evidence.

If the runtime cannot expose enough execution chronology to rule out redirects, retries, fallbacks, corrections, or contradictions, the verdict is `Not confirmed`.

When the user supplies a hypothetical or reported scenario without primary evidence, distinguish two claims:

1. **Reported-path assessment:** classify the route exactly as described, such as “the described path is Failed because it requires a retry.”
2. **Runtime proof verdict:** use `Not confirmed` until primary execution evidence and authoritative result readback establish what the real system did.

Do not weaken a useful diagnosis merely because live evidence is absent, and do not promote reported facts into a confirmed runtime claim.

## Reconstruct and challenge

Build the material chronology from the first action through result readback. For each step record:

- actor and timestamp or ordering;
- event, action, or state transition;
- relevant identifier;
- what the evidence proves;
- what it does not prove; and
- competing or contradictory evidence.

Actively search for redirects, false starts, timeouts, retries, errors, fallbacks, restarts, duplicate actions, manual corrections, missing responses, wrong-owner work, avoidable side investigations, and unexplained gaps.

## Verdicts

- **Confirmed:** the exact goal completed through the intended route cleanly from the first action, and complete available execution evidence plus authoritative readback proves the sequence and result.
- **Not confirmed:** required evidence is missing, incomplete, unavailable, ambiguous, contradictory, or unsettled.
- **Failed:** the goal failed or the execution contained a proven disqualifying route deviation. Report any eventual successful outcome separately without changing the failed verdict.

After a failed proof, repair the earliest owning divergence and rerun the complete operation from a clean beginning. A repaired fragment does not confirm the full path.

Verdicts are scoped to individual proof runs. An unmodified retry, restart, or manual correction remains part of the original failed run. After an actual repair, a separate clean rerun begins a new proof and receives its own verdict.

## Reliability-mechanism admission

Before adding a test, linter, gate, guardrail, retry, fallback, compatibility path, detector, or telemetry assertion, answer:

1. Which confirmed operating path will it preserve?
2. What stable behavior has already been observed in clean runs?
3. What concrete failure remains after core-path simplification?
4. Why can that failure not be removed at its earliest owning boundary?
5. Which authority, integrity, security, consent, destructive-action, or side-effect boundary will it protect?
6. What states, branches, or ambiguity will it remove?
7. Which component owns the mechanism and its failure behavior?

If these answers are not concrete, return to path definition, simplification, repair, and a clean real-operation rerun.
