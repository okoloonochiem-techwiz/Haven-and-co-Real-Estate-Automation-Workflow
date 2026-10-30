# Haven & Co. system organogram

This is the high-level intended architecture. The Vapi connection is marked as planned because the assistant configuration and website embed are not yet confirmed complete.

```mermaid
flowchart TB
    USER[Property seeker]
    USER --> TG[Telegram bot]
    USER --> WEB[Haven & Co. website]
    USER -. planned .-> VAPI[Vapi voice agent]

    TG --> N8N[n8n automation layer]
    WEB --> CHAT[Website AI chat]
    WEB --> FEED[Property listings feed]
    CHAT --> N8N
    FEED --> N8N
    VAPI -. planned tool call .-> N8N

    N8N <--> GPT[OpenAI GPT-5-mini]
    N8N <--> AIR[(Airtable)]

    AIR --> LEADS[Leads table]
    AIR --> CLIENTS[Clients table]
    AIR --> PROPS[Properties table]

    N8N --> TGRESP[Telegram response]
    N8N --> WEBRESP[Website response / listings]
    N8N -. planned .-> VRESP[Vapi spoken response]
```

## Responsibility split

- **Antigravity website:** user-facing web experience.
- **Telegram:** messaging-based property search.
- **Vapi:** intended voice interface.
- **n8n:** orchestration, AI steps, matching logic and API/webhook handling.
- **OpenAI:** language understanding and response generation in configured AI nodes.
- **Airtable:** operational records for properties, leads and clients.
