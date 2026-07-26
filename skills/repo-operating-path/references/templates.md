# Templates

## Operating-path definition

```md
# Operating path: <name>

- Goal:
- Actor:
- Starting state:
- Correct first action:
- Owner route:
- State transitions:
- Side effects:
- Authority boundaries:
- Completion point:
- Authoritative readback:
- Acceptance criteria:
- Disqualifying deviations:
```

## Divergence finding

```md
# Earliest divergence

- Intended step:
- Actual step:
- Evidence:
- Classification: path | ownership | contract | implementation | evidence | environment | operator
- Owning component:
- Cause:
- Repair or simplification:
- Downstream symptoms retained as evidence:
- Complete path to rerun:
```

## Proof report

```md
# Operating-path proof

- Verdict: Confirmed | Not confirmed | Failed
- Exact goal:
- Correct first action:
- Intended route:
- Real operation performed:
- Execution evidence reviewed:
- Authoritative surfaces read back:
- Chronology:
- Acceptance evidence:
- Contradictory evidence:
- Disqualifying deviations:
- Reported-path assessment, if scenario-based:
- Repair and clean rerun:
- Runtime proof verdict and limiting conditions:
- Earned preservation mechanism: none | <mechanism and boundary>
```

## Lesson record

Use this only when a completed case has reusable value.

```md
# Lesson: <short title>

- Attempted goal:
- Intended path:
- Earliest divergence:
- Why it existed:
- Owner able to remove it:
- Repair or simplification:
- Complete-rerun result:
- Complexity removed:
- Repeated evidence supporting generalization:
- Proposed promotion: local repair | operating rule | preservation mechanism | no promotion yet
```

One incident does not automatically justify a global rule, test, fallback, or guardrail.
