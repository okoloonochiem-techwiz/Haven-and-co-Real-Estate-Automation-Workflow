# 02 — Website AI chat

## Purpose
Provide a conversational assistant on the Haven & Co. website that can understand property questions and search listing data through n8n.

## Intended flow
1. A visitor sends a message through the website chat interface.
2. The website sends the message to the n8n chat/webhook integration.
3. The AI Agent uses the configured language model and recent conversation context.
4. The Airtable listing-search tool retrieves relevant property information.
5. The assistant formats a response for the website.

## Configuration notes
The build notes describe an n8n Chat Trigger, an AI Agent using OpenAI GPT-5-mini, memory covering the last ten messages and an Airtable `search_listings` tool.

## Scope note
The last confirmed scope did not include saving website chat enquiries as Leads or forwarding those enquiries to agents. Do not assume website chat lead capture is enabled.

## Validation
Test a property question, a follow-up question, an unavailable listing, an ambiguous request and an Airtable/API failure. Confirm that the assistant does not invent prices, locations or property availability.

## Files in this folder
- `workflow-export/` — sanitised n8n JSON export.
- `screenshots/` — website chat UI and n8n configuration/evidence.

## Screenshot suggestions
`01-website-chat-interface.png`, `02-chat-trigger.png`, `03-ai-agent-configuration.png`, `04-airtable-search-tool.png`, `05-chat-response.png`.

**Status:** Configured in the build; end-to-end validation required.
