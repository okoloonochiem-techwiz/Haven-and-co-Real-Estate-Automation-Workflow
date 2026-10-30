# 05 — Testing and limitations

This document records known validation needs. Update it when a test is repeated and its result is confirmed.

## Test checklist

| Test | Expected result | Current note |
|---|---|---|
| Telegram receives a message | Trigger starts workflow | Verify after deployment changes |
| AI extracts criteria | Structured budget/location/type/rooms | Test edge cases and clarification |
| Matching properties exist | Relevant listings are returned | Verify ranking and relaxation logic |
| No matching properties | Clear no-match response | Verify inquiry path |
| Lead already exists | Existing lead is updated | Verify Telegram Chat ID lookup |
| New lead | New Airtable lead is created | Verify required fields |
| Website listings endpoint | JSON list of available properties | Live feed needs validation |
| Property images | Each listing shows its own image | Duplicate-image issue has been reported |
| Website chat | Answers from listing data | End-to-end operation needs validation |
| Voice tool call | Vapi receives formatted result | Vapi setup/embed remains outstanding |

## Known issues / cautions

- The Telegram Clients search previously had a missing/incorrect filter and could return an unrelated client record. Confirm that it filters by the intended client identifier before relying on client preferences.
- Website property images have appeared duplicated across different listings. Check Airtable attachment mapping and the frontend's per-record image binding.
- The live property feed has not been consistently verified. Confirm the active production webhook, workflow activation and response payload.
- Website chat was configured to search listings; lead capture from website chat was not part of the last confirmed scope.
- The voice workflow contract was drafted, but Vapi assistant configuration and website embedding remain outstanding.
- After editing an n8n workflow, confirm that the production/active version includes the changes.
- If browser requests fail because of CORS, configure an appropriate allowed origin for the deployed website. Do not use an unrestricted wildcard without considering the endpoint's exposure.

## Test evidence

Add dated screenshots to the screenshots folder inside the relevant workflow. Screenshots should show actual results and should not expose credentials, private URLs or personal data.

## Status language

Use **Built** only for components that exist, **Tested** only after a repeatable test, **Needs validation** where behaviour is not confirmed, and **Planned** where implementation is incomplete. Do not describe the overall project as production-ready until security, reliability and end-to-end tests have passed.
