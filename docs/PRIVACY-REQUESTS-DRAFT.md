# Quack Mayhem — Privacy request handling (DRAFT)

**Status:** Review-only procedure. Not implemented or validated end-to-end. Do not claim the deletion workflow is operational until the checks below pass. No user data or scores were deleted to create this document.

**Public support/privacy contact:** buffstersquest-support.skating711@passfwd.com (Robert's tested forwarding alias). Do not expose his personal inbox address on the public policy.

## Intake and scope

1. Receive the request through the public alias. Record the date, the nature of the request (access, correction, deletion) and a minimal internal case reference. Do not ask for passwords, login tokens, app secrets, date of birth or other unnecessary sensitive information.
2. Explain the possible data categories:
   - Local settings, best scores and diagnostic information: stored on the user's headset, not on a separate BuffstersQuest server.
   - Meta-managed Quack Mayhem leaderboard entry: score, associated Meta account identity, rank and optional 1H/2H label.
   - Temporary session information: Meta entitlement/age category and leaderboard views, not retained in a separate persistent developer database.
   - Support email: stored by the developer's email service for handling the request.
3. Before making any account-specific change, verify that the requester owns or is authorized to act for the affected Meta account. **A supplied display name or unverified email claim alone is insufficient.** Design a suitable identity-verification method; its implementation is still pending.

## Handling

### A. Local-only game data

Guide the player to use applicable Quest app-data clearing or uninstall options. Explain that this removes local preferences and personal-best records (subject to the headset's backup behavior). Confirm the current Quest menu wording before publishing detailed user instructions.

### B. One Meta leaderboard entry

Meta documents a **server-side single-entry deletion** API. For an authorized, verified request:

1. Identify the correct Quack Mayhem leaderboard (currently `quack_timed_60s_v3`) and the specific requesting account.
2. Using an approved developer administration workflow, find **that account's entry ID** through Meta's leaderboard-entries API, with access credentials kept in a secure environment.
3. Double-check the app, leaderboard, account and exact entry ID; require explicit approval of the intended target before any actual deletion.
4. Delete **only that entry ID** with the documented single-entry DELETE operation. Verify Meta's response and, where feasible, confirm the entry no longer appears.
5. Confirm completion to the requester without disclosing secrets or another user's information. Keep only the minimum necessary record.

**Never use Meta's "delete all leaderboard entries" endpoint for an individual request.** Never run untested deletion calls against Robert's actual `22,850 / 1H` record or any live user score.

Meta documentation: https://developers.meta.com/vr/documentation/spatial-sdk/ps-leaderboards-s2s/

### C. Meta account or other Meta-managed records

For data beyond the developer's app/leaderboard control, refer the requester to Meta's account/privacy controls and help them identify an appropriate support channel. Do not promise that BuffstersQuest can delete Meta's entire account records.

### D. Support messages

Review and delete email data that is no longer necessary for the request, consistent with legal record-retention duties; do not retain passwords, tokens or identity proofs.

## Before approving the public privacy policy

- [ ] Test that a privacy request reaches the alias and that Robert can reply.
- [ ] Confirm the current local-data deletion steps on Quest 3.
- [ ] Determine a practical, privacy-respecting account-ownership verification method.
- [ ] Validate the **single-entry** deletion process against an explicitly authorized test score only; do not use the developer's actual leaderboard best or unrelated scores.
- [ ] Confirm any procedural requirements with Meta if API access, permissions or verification remain uncertain.
- [ ] Review wording in the draft privacy policy so it accurately reflects the tested process; set the effective date at actual publication.
- [ ] Robert explicitly approves merging the draft policy into the published branch.

## Source and scope

Meta Developer Data Use Policy: https://developers.meta.com/vr/policy/data-use/

Meta Privacy Policy Requirements: https://developers.meta.com/vr/policy/privacy-policy/

This document is an internal implementation checklist, not legal advice. It contains no app secrets or credentials.
