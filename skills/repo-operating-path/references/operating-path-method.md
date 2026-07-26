# Operating Path Method

## Definition

An operating path is the smallest intended sequence through which a specific actor starts from a defined state, invokes the owning system, crosses required authority and side-effect boundaries, reaches an exact goal, and reads the result back from the authoritative owner surface.

Define these fields before changing or proving the route:

1. **Goal:** the exact real-world result requested.
2. **Actor:** the person, agent, process, or external system initiating the operation.
3. **Starting state:** conditions that must be true before the first action.
4. **First action:** the correct entrypoint selected from the original request.
5. **Owner route:** the responsible component and legitimate downstream owners in order.
6. **State transitions:** meaningful states through which the operation moves.
7. **Side effects:** artifacts, messages, processes, records, or external state changed.
8. **Authority boundaries:** surfaces that authorize or cause consequential actions.
9. **Completion point:** the moment the requested goal is actually achieved.
10. **Authoritative readback:** the owner surface that independently confirms the result.
11. **Acceptance criteria:** observable facts required for confirmation.
12. **Disqualifying deviations:** behavior that requires repair and a complete rerun.

Determine the intended route from explicit user intent, the documented user-facing contract, the owning component's API or command contract, and current implementation evidence, in that order. Record conflicts rather than silently choosing one source. A route whose authority is unresolved is `Not confirmed`.

## Readiness conditions

A path is ready for proof only when the working run shows:

1. the exact goal was achieved;
2. the correct first action selected the correct owner;
3. execution followed the intended owner route;
4. required state transitions occurred in order;
5. each side effect occurred once at its owning boundary;
6. authoritative readback confirms the resulting state;
7. no contradictory or unexplained evidence remains; and
8. completion did not depend on a redirect, fallback, retry, restart, duplicate action, manual correction, wrong-owner detour, or avoidable side investigation.

## Earliest divergence

The earliest meaningful divergence is the first action, state, owner choice, contract exchange, or evidence boundary after which the actual route no longer matches the intended route.

Start remediation there. Preserve downstream symptoms as evidence, but do not build compensating mechanisms around them unless they remain after the earliest cause is removed.

## Divergence classes

- **Path defect:** the intended sequence is incomplete or wrong. Repair the definition and owning implementation together.
- **Ownership defect:** execution entered through or delegated to the wrong owner. Repair the entrypoint or call direction.
- **Contract defect:** legitimate owners disagree about inputs, outputs, state, or completion. Repair the shared boundary contract.
- **Implementation defect:** the intended route is sound but malfunctioned. Repair the responsible component.
- **Evidence defect:** the operation lacks authoritative confirmation. Repair owner-surface readback.
- **Environment defect:** a required external condition was unavailable. Restore it or redefine the starting condition explicitly.
- **Operator defect:** the actor selected an action outside the defined route. Repair the routing cue or procedure at its owning surface.
- **Incidental finding:** the observation did not affect the route. Record it separately.

Every material finding should answer:

1. Where did the actual route first diverge?
2. Which owner can remove the divergence?
3. What should that owner simplify or repair?
4. What complete path must be rerun afterward?

## Simplification standard

Prefer:

- fewer accepted states;
- fewer route branches;
- fewer owner transitions;
- fewer result meanings;
- fewer duplicate signals;
- fewer compatibility translations;
- fewer manual decisions; and
- clearer authority and completion boundaries.

The smallest change is not always the smallest diff. It is the change that removes the causal complexity at the earliest legitimate owner boundary without broadening scope.
