# 03 — Airtable database

## Base
The project uses an Airtable base named **Real Estate Leads**, with three tables: **Leads**, **Clients** and **Properties**.

The following lists reflect the schema described during the build. Verify exact live field names, field types and select options in Airtable before changing workflows.

## Leads table
| Field | Intended use |
|---|---|
| Lead ID | Lead identifier |
| Full Name | Enquirer's name |
| Phone Number | Contact number |
| Email | Email address |
| Lead Source | Originating channel |
| Property Type | Requested category |
| Budget (NGN) | Stated budget |
| Preferred Location | Preferred area |
| Lead Status | Enquiry stage |
| Lead Temperature | Hot / Warm / Cold |
| Last Contact Date | Most recent contact |
| Next Follow-Up Date | Planned follow-up |
| Viewing Date | Scheduled viewing |
| Viewing Feedback | Feedback after viewing |
| AI Summary | Conversation/request summary |
| Created At | Record creation time |
| Assigned Client | Linked/assigned client |
| Interested Property | Linked property |
| Telegram Chat ID | Telegram-specific identifier |

## Clients table
| Field | Intended use |
|---|---|
| Client ID | Auto-number primary identifier |
| Client Name | Client or agent name |
| Phone Number | Contact number |
| Email | Email address |
| Client Type | Client classification |
| Client Status | Configured status |
| Linked Lead | Linked lead record |
| Interested Property | Linked property |
| Notes | Additional context |
| Lead Source | Origin where applicable |
| Created At | Creation timestamp |

## Properties table
The Properties table supports listing search and should contain fields for property title, property type, location, price, bedrooms, bathrooms, description, property images/attachments and availability status.

**Confirm exact column names and attachment structure in the live base.** Matching code and website mapping must use the actual field names.

## Relationships
A lead may link to a client and an interested property. A client may link to one or more leads or properties depending on the configured linked-record fields. Property search uses availability and user preferences.

## Data quality
- Store prices numerically where possible.
- Map each property's own attachment field to its image.
- Use consistent location and property-type values.
- Populate Lead Source consistently.
- Do not use Telegram Chat ID as a universal identifier.
- Use fictional data in public screenshots.

## Privacy
Do not publish real names, phone numbers, emails, Telegram identifiers or private enquiry details. Redact personal data in screenshots.
