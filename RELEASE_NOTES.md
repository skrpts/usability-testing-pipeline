# Release Notes

## v1.0.16
GH#844 — migrate the gate step from node-meta (`metadata.gate: true` in the skill) to the canonical execution-entry `gate: true` on the workflow step. Single source of truth; the engine + app read the execution entry. No behaviour change — `IsGate` is identical. Also re-pin the `gate-test-results` shared dep 1.0.1 → 1.0.3 (the migrated gate skill). Fix a pre-existing type defect: `execution[0]` declared `skill: "plan-usability-tests"`, but that slug is a shared **prompt** (not a skill) — corrected to a prompt-only generation step (`execution_skill_wrong_type`, #790 class).

## v1.0.15
GH#745 — declare per-step `output: {name, type}` on every execution step (test_plan/text, test_results/text, findings/text, recommendations/text, polished_report/text, consistency_verdict/decision). Lights up the #744 rich flow-map. Content-only; no bindings or logic changes.

## v1.0.14
Fix-forward after Row 3b v1.0.13 publish failure. The v1.0.13 per-skrpt CI's "Register version with Hub API" step failed because the consumer's source `manifest.id` (41adb99c…) did not match the D1 catalog row's id (b0c07870…) — a legacy drift from before Action 6 (`0bcc5ae0`) made publish-skrpt.mjs Step 2 INSERT use `manifest.id` for the D1 id column. v1.0.14 reconciles the source `manifest.id` to the catalog authoritative value (Row-5-equivalent for consumers) and republishes. Per Adj-1: no re-tag of v1.0.13; the orphaned GitHub release artefact stays inert (no D1 versions row, no consumer pinned it).

## v1.0.13
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 8 inline shared-content files and declare 7 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Internal slug references rewritten for E2 rename/mirror-drop pair(s): test-planning→plan-usability-tests, test-execution→gate-test-results, plan-tests→plan-usability-tests. Closes pre-Step-3 inline-vendoring for this bundle.

## v1.0.12
Wave 2: re-signed with canonical engine signing pipeline.

## v1.0.11
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.0.10
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.0.9
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.0.8
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
