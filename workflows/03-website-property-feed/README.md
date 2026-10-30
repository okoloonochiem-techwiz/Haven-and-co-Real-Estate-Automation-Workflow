# 03 — Website property listings feed

## Purpose
Provide the Haven & Co. website with available property records from Airtable through an n8n webhook.

## Endpoint contract
The documented route is a GET webhook with the path `/webhook/haven-listings`. The intended response is JSON with a top-level `listings` array.

Example shape (illustrative only; actual property fields must match the live Airtable schema):

```json
{
  "listings": [
    {
      "title": "Demo property",
      "location": "Demo location",
      "price": 2500000,
      "images": []
    }
  ]
}
```

The workflow is intended to:
1. Receive the website request.
2. Retrieve Properties records whose availability status is Available.
3. Map the fields needed by the website.
4. Respond with HTTP 200 and JSON content.

## Image mapping
Each property's image data must be mapped from that property's own Airtable attachment field. Do not use a fixed image value or the first record's image for every listing. Confirm that the frontend iterates over each listing's own image URL.

## Validation
- Check that the workflow is active and the production endpoint is being called.
- Confirm the response is valid JSON and contains only available properties.
- Compare multiple returned records with their Airtable images.
- Check empty results and Airtable errors.
- Verify CORS configuration for the deployed website if browser calls are blocked.

## Files in this folder
- `workflow-export/` — sanitised n8n JSON export.
- `screenshots/` — webhook, Airtable retrieval, response mapping and website listing evidence.

## Screenshot suggestions
`01-listings-webhook.png`, `02-airtable-available-properties.png`, `03-response-mapping.png`, `04-json-response.png`, `05-website-property-cards.png`.

**Status:** Endpoint design/implementation documented; live feed and image mapping need validation.
