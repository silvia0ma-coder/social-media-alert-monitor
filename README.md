# social-media-alert-monitor

Real-time keyword & trend monitoring automation that alerts teams via Slack and logs to Google Sheets using n8n workflows.


---

## Workflow Diagram

![Workflow Diagram](workflow.diagram)

---

## How It Works

The automation follows three main branches:

- 🟢 *Create* — Detects a new record and appends it to Google Sheets
- 🔵 *Update* — Sends a Slack notification and updates the Sheet
- 🟡 *Fallback* — Logs the item to Google Sheets only

### Flow Steps

1. *Schedule Trigger* — Runs automatically at set intervals
2. *HTTP Request* — Fetches latest trends/news for tracked keywords
3. *Split Out* — Breaks response into individual items (up to 10)
4. *Code in JavaScript* — Processes and classifies each item
5. *Switch* — Routes each item to Create, Update, or Fallback
6. *HTTP Request / Airtable* — Creates or updates records
7. *Append/Update Row in Sheets* — Logs everything to Google Sheets

---

## Files

| File | Description |
|------|-------------|
| workflow.json | Main n8n workflow — import this into your n8n instance |
| workflow.diagram | Visual diagram of the automation flow |

---

## Setup

1. Import workflow.json into your n8n instance
2. Configure your credentials:
   - Google Sheets API
   - Slack API
   - Airtable API
3. Set your target *keywords/topics* in the HTTP Request node
4. Activate the workflow

---

## Built With

- [n8n](https://n8n.io/) — Workflow automation
- Google Sheets — Data logging
- Slack — Team alerts
- Airtable — Record management
