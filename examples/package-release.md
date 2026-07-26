# Example: Package Release That Only Works After a Retry

## Situation

A repository's `release` command reports success, but users have learned to run it twice. The first run uploads an artifact and exits with an error before the release record is finalized. The second run detects the uploaded artifact and finishes the release.

## Intended operating path

- **Goal:** publish one package version and one matching release record.
- **Actor:** repository maintainer.
- **Starting state:** clean branch, passing build, authenticated registry session, unused version.
- **Correct first action:** run the repository's documented `release` command once.
- **Owner route:** release command → package builder → registry publisher → release-record API.
- **State transitions:** prepared → built → uploaded → recorded → confirmed.
- **Side effects:** one artifact upload and one release record.
- **Authority boundaries:** registry publish authorization and release-record creation authorization.
- **Completion point:** both artifact and release record exist for the same version.
- **Authoritative readback:** registry API and release API return matching version and artifact digest.
- **Acceptance criteria:** one command invocation; ordered transitions; each side effect once; matching direct readback.
- **Disqualifying deviations:** retry, duplicate upload, manual record creation, direct lower-level API call, or success based only on command output.

## Actual route

The complete command trace shows:

1. The documented command builds and uploads the artifact.
2. A local state file is written with status `uploaded`.
3. The release-record client reads a different field name, treats the upload result as missing, and exits.
4. The second invocation sees the registry artifact, skips upload, translates the state, and creates the release record.
5. Registry and release APIs now show the desired final state.

The eventual outcome succeeded. The operating path failed because it required a retry and a compatibility translation.

## Earliest divergence

- **Intended step:** pass the successful upload result directly to the release-record client.
- **Actual step:** write one result shape and read a different result shape.
- **Classification:** contract defect.
- **Owning component:** the boundary between the publisher and release-record client.
- **Repair:** use one canonical result field and remove the retry-only translation.

The missing release record and misleading command status are downstream symptoms. Fixing either with another retry or guardrail would preserve the broken boundary.

## Clean rerun

From an unused version and clean local state:

1. The maintainer invokes `release` once.
2. The trace shows `prepared → built → uploaded → recorded → confirmed`.
3. One artifact upload and one release record occur.
4. Registry and release APIs return the same version and digest.
5. No retry, fallback, manual correction, or alternate entrypoint occurs.

Verdict: **Confirmed**.

## Preservation decision

A deterministic contract test for the publisher-to-release-record result shape is now earned because it preserves a cleanly proven boundary. A retry wrapper is not earned because it would reintroduce an alternate path instead of preserving the confirmed one.
