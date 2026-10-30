# 04 — Setup and configuration

## Prerequisites
- n8n instance
- Airtable account and the **Real Estate Leads** base
- Telegram bot token
- OpenAI API connection
- Antigravity website project
- Vapi account if implementing voice

## Airtable
1. Confirm the Leads, Clients and Properties tables.
2. Verify exact field names and types against [03 — Airtable database](03-airtable-database.md).
3. Add demo properties with distinct images, prices, locations and availability values.
4. Use fictional lead/client details for testing.

## n8n credentials
Create credentials inside n8n for Airtable, Telegram and OpenAI. Select those credentials in the relevant nodes. Never commit API keys, bot tokens, credential exports or private webhook URLs.

## Importing workflows
When sanitised n8n JSON exports are added to each workflow's `workflow-export/` directory:
1. Import the JSON into n8n.
2. Re-select credentials.
3. Verify Airtable base, table and field mappings.
4. Review webhook paths and response settings.
5. Test before activating the workflow.

The export folders are placeholders until the actual exports are supplied.

## Telegram
1. Confirm the Telegram Trigger receives a test message.
2. Verify request understanding returns structured criteria.
3. Verify property search uses the actual Airtable field names.
4. Test matching and no-match requests.
5. Test both creating a new lead and updating an existing lead.
6. Confirm each result's image belongs to the correct property.

## Website
1. Configure the Antigravity frontend to call the appropriate n8n endpoint.
2. Confirm the website property feed returns JSON.
3. Check browser network responses and CORS if the request fails.
4. Verify image URLs are mapped per property, not reused across records.
5. Re-publish/activate the n8n workflow after making changes where required.

## Voice
The Vapi assistant, tool definition, webhook connection and website embed are not yet confirmed complete. Configure these only after validating the n8n voice endpoint's request and response contract.

## Environment-specific values
Keep deployment URLs, API credentials, Airtable identifiers and account-specific settings in private configuration. Use placeholders in public documentation and screenshots.
