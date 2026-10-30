# 04 — Vapi voice agent

## Purpose
Extend Haven & Co. property search to a voice conversation. The intended voice provider is Vapi, with n8n handling the property lookup.

## Intended flow
1. A caller speaks to the Vapi assistant.
2. Vapi extracts or sends the caller's property request through a tool call.
3. Vapi calls the n8n voice webhook.
4. n8n searches available Airtable listings and prepares a concise result.
5. n8n returns a tool response containing the matching tool-call identifier and result text.
6. Vapi speaks the response to the caller.

## Documented endpoint contract
The build notes describe a POST webhook path `/webhook/haven-voice`. The expected response shape was designed as:

```json
{
  "results": [
    {
      "toolCallId": "value-from-incoming-tool-call",
      "result": "Human-readable property search result"
    }
  ]
}
```

This is a contract illustration, not a live endpoint or credential. Confirm the exact Vapi tool schema and incoming payload before implementing the response mapping.

## Current status
The n8n webhook and response design have been discussed, but Vapi assistant configuration and website embedding are not confirmed complete.

## Validation
Test a clear request, missing criteria, no available property, multiple matches, malformed tool input and webhook timeout. Confirm the response uses the correct tool-call ID and does not invent listing details.

## Files in this folder
- `workflow-export/` — sanitised n8n JSON export.
- `screenshots/` — Vapi assistant/tool setup and n8n voice workflow evidence.

## Screenshot suggestions
`01-vapi-assistant-overview.png`, `02-vapi-tool-definition.png`, `03-n8n-voice-webhook.png`, `04-property-search-response.png`, `05-website-voice-widget.png`.

**Status:** Planned / partially designed; Vapi setup and embedding remain outstanding.
