# Repo Operating Path

Repo Operating Path is an Agent Skill for making repository workflows work cleanly from their intended first action.

It helps Claude and Codex users:

- define the exact route a workflow should take;
- distinguish a successful outcome from a healthy operating path;
- find the earliest meaningful divergence;
- repair the component that owns that divergence;
- rerun the complete path from a clean start;
- decide whether tests, guardrails, retries, or telemetry are actually earned.

The method is useful when a workflow eventually succeeds only after retries, fallbacks, manual fixes, lower-level shortcuts, duplicate actions, or detours through the wrong owner.

## What is included

```text
skills/repo-operating-path/
├── SKILL.md
└── references/
    ├── operating-path-method.md
    ├── proof-protocol.md
    └── templates.md
examples/
└── package-release.md
```

The skill has no scripts, external calls, or machine-specific configuration.

## Install

Clone the repository:

```sh
git clone https://github.com/besowards/repo-operating-path.git
REPO_OPERATING_PATH="$(pwd)/repo-operating-path"
```

For Claude Code, copy the skill into the project skill directory:

```sh
TARGET_PROJECT="/path/to/your/project"
mkdir -p "$TARGET_PROJECT/.claude/skills"
cp -R "$REPO_OPERATING_PATH/skills/repo-operating-path" "$TARGET_PROJECT/.claude/skills/"
```

Or install it for the current Claude Code user:

```sh
mkdir -p "$HOME/.claude/skills"
cp -R "$REPO_OPERATING_PATH/skills/repo-operating-path" "$HOME/.claude/skills/"
```

For Codex, install it at project scope:

```sh
TARGET_PROJECT="/path/to/your/project"
mkdir -p "$TARGET_PROJECT/.agents/skills"
cp -R "$REPO_OPERATING_PATH/skills/repo-operating-path" "$TARGET_PROJECT/.agents/skills/"
```

Or install it for the current Codex user:

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R "$REPO_OPERATING_PATH/skills/repo-operating-path" "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Restart or open a fresh agent session if the runtime does not discover newly installed skills immediately.

Verify the copied skill and trigger behavior:

```sh
test -f "$TARGET_PROJECT/.agents/skills/repo-operating-path/SKILL.md"
```

In a fresh session, ask “Map the operating path for our release command before we add retries.” The response should define the path before proposing changes. A near-miss such as “Diagnose why the lint job fails on Node 22” should remain ordinary debugging unless route ownership, side effects, or end-to-end proof are also at issue.

## Use

Ask the agent naturally, for example:

- “Map and repair the operating path for our release command.”
- “This migration works after a retry. Find the earliest path defect.”
- “Prove this end-to-end workflow is clean before adding a regression test.”
- “Decide whether this guardrail protects a proven path or hides a broken one.”

The agent should return an operating-path packet containing the intended route, actual route and evidence, earliest divergence, owning repair, clean-rerun verdict, and any earned preservation recommendation.

See [the repository's generic package-release example](examples/package-release.md) for a complete worked case.

## Core principle

An operating path is confirmed only when the exact goal completes through the intended route from the correct first action, and the complete available execution record agrees with authoritative result-state readback.

An eventual successful outcome reached through a redirect, retry, fallback, restart, duplicate action, manual correction, wrong-owner detour, or avoidable side investigation is not a confirmed operating path.

## License

MIT. See [LICENSE](LICENSE).
