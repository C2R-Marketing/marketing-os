---
name: c2r-marketing-production
description: Operate C2R Marketing across Zeffy email/CRM, social distribution, YouTube production, research, measurement, and adversarial review. Use to start, resume, hand off, or recover production marketing work across any LLM or agent harness without relying on provider-specific memory or orchestration.
license: MIT
compatibility: Harness- and model-neutral. Requires file/state access plus whichever external capabilities the active job needs; tool names are mapped to canonical capabilities at runtime.
metadata:
  c2r-authority: company-os
  state-contract: v1
  portability: harness-and-model-neutral
---

# C2R Marketing Production

## Authority
Tov Rose is final owner. `C2R-Marketing/company-os` is the company-wide operational source of truth. Marketing is a department. This repository is the Marketing department implementation surface, not a competing Company OS. Paperclip is inactive/historical and has no authority or execution role.

## Production state is not model state
Never use a chat, harness session, provider memory, hidden scratchpad, or model identity as the authoritative production state. A job must be resumable from persisted state, immutable/sanitized artifacts, receipts, current Company OS authority, and this package alone.

## Cold start on every model or harness
1. Read `contracts/capabilities.schema.json` and map this harness's real tools to canonical capabilities.
2. Read and validate the current job state against `contracts/state.schema.json`.
3. Load only the active employee contract from `references/employee-registry.json`.
4. Resolve the current Company OS campaign contract/owner authorization before any material external action.
5. Resume from the persisted `checkpoint` and `revision`; never from memory.
6. If a required capability is unavailable, persist `BLOCKED` with the exact resumable next action.

## Capability abstraction
Express dependencies only as capabilities, never vendor-specific tool names. Examples: `browser.read`, `browser.act`, `email.read`, `social.publish`, `video.render`, `youtube.publish`, `metrics.read`, `state.compare-and-swap`, `judge.run`.

A capability mapping is valid only if the mapped tool can perform that action on the intended account/environment. A similar name or documentation claim is not proof.

## Employees
- `marketing-department-director`: prioritization, delegation, GTM diagnosis, economics.
- `zeffy-email-operations-lead`: authenticated Zeffy/email/CRM/fundraising execution.
- `social-distribution-operator`: cross-platform scheduling/publishing/read-back.
- `youtube-growth-producer`: source-grounded YouTube/Shorts production and publishing.
- `marketing-performance-adversarial-judge`: independent read-only qualification and SCALE/REPAIR/HOLD/KILL verdicts.

The workflow coordinator dispatches specialists; it does not become a giant do-everything prompt.

## State machine
Normal phases:

`INTAKE -> QUALIFY -> PREPARE -> EXECUTE -> VERIFY -> MEASURE -> JUDGE -> LEARN -> COMPLETE`

`BLOCKED` may be entered from any non-complete phase. `OWNER_GATE` is used only when current Company OS/owner authorization requires owner authority. Resume from the prior checkpoint after resolution.

An external action is never a production fact at `EXECUTE`. It becomes factual only after `VERIFY` obtains target-system read-back or independent evidence.

## Continuity invariants
- Stable `campaign_id` across all channel work for one campaign.
- Stable `job_id` for one resumable unit of work.
- Monotonic integer `revision`; writes are compare-and-swap.
- `checkpoint` names the last completed deterministic step.
- Every external side effect has an `idempotency_key`.
- Receipts contain sanitized evidence references, never credentials/cookies/raw donor or customer PII.
- `next_action` must be executable by a fresh model with zero chat history.
- Before a model/harness switch, finish or roll back the current atomic action, persist artifacts and receipts, update checkpoint/next action, then atomically increment revision.

## External action authorization
Routine reversible work and external actions may execute automatically when they are inside an explicit current standing authorization that bounds brand, audience, offer/content, frequency, send/post windows, volume, and stop thresholds. Do not repeatedly ask for approval for work already inside that authorization.

New spend, new legal/contractual commitments, account/credential/permission changes, destructive actions, or material deviations from approved boundaries return to `OWNER_GATE`.

## Zeffy
Zeffy is the fixed email/CRM/fundraising platform unless Tov explicitly changes that decision. The operator must learn the authenticated live backend from the owner-controlled account and use live/official evidence for current UI behavior. Do not invent a send API, platform limit, authenticated session, or successful send.

## Social
Prefer mature API/CLI/agent-native publishing rails and platform-native APIs over brittle bespoke browser posting. A returned command/API success is not proof of publication; require platform/scheduler read-back plus post identifiers.

## YouTube
Keep research, scripting, factual/theological QA, asset provenance, rendering, packaging, publishing, repurposing, and measurement as explicit checkpoints so any component/model/harness can be swapped without restarting completed work.

## Adversarial review
A producer does not verify itself. At `JUDGE`, use a fresh read-only context and, where available, a different model/provider lineage. If only the same model/provider is available, disclose that limitation; never call it independent multi-model review.

## Unsupported harnesses
If the harness does not implement Agent Skills, point the LLM directly at this `SKILL.md`, expose this folder and current persisted state, then map the harness's actual tools to the canonical capabilities. Do not rewrite this workflow into a provider-specific prompt; that creates drift and a second source of behavior.
