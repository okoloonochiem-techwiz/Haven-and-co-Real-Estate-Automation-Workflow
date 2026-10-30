# 01 — Telegram property search

## Purpose
Allow a property seeker to send a natural-language request to the Haven & Co. Telegram bot and receive relevant property listings.

## Intended flow
1. Telegram Trigger receives the message.
2. The workflow identifies the requester and searches for an existing lead.
3. An AI step extracts search criteria such as maximum budget, location, property type, bedrooms, bathrooms and requested features.
4. If important details are missing, the bot asks a clarification question.
5. Airtable is queried for available properties.
6. Matching logic ranks suitable properties and can progressively relax criteria when exact matches are unavailable.
7. The workflow formats and sends up to five property results, including images where available.
8. The lead branch creates a new lead or updates an existing lead.

## Matching approach
The build notes describe progressive matching: exact criteria first, then relaxing bedroom/type constraints, considering a budget allowance of up to 30%, considering other locations for the same type, and finally considering other options within budget. Clearly communicate when a result is an approximate match rather than an exact match.

## Data
- Properties are read from Airtable's Properties table.
- Lead records are stored in Leads.
- Telegram Chat ID is a channel-specific identifier and should not be used as a universal identity for website or voice users.
- Lead Source should identify Telegram for this channel.

## Validation notes
A previous Clients search configuration lacked the intended filter and could return an unrelated record. Verify the search filter before using client-specific preferences. Test new lead, existing lead, clarification, exact match, relaxed match and no-match paths.

## Files in this folder
- `workflow-export/` — add a sanitised n8n JSON export here.
- `screenshots/` — add screenshots of the Telegram bot conversation and relevant n8n nodes here.

## Screenshot suggestions
Use filenames such as `01-telegram-search-request.png`, `02-criteria-extraction.png`, `03-airtable-property-search.png`, `04-matching-results.png`, `05-telegram-property-response.png`, and `06-lead-created-or-updated.png`.

**Status:** Built during the project; repeatable end-to-end testing is recommended.
