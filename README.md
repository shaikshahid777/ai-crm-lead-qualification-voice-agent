# AI CRM Lead Qualification Voice Agent

An end-to-end AI voice agent that qualifies CRM leads using the BANT framework, scores prospects, updates HubSpot, checks meeting availability, schedules qualified meetings, and sends confirmation emails.

## 🎥 Project Demo

**Loom Demo:** https://www.loom.com/share/708291dc1b7d4dcabace007593e9dc4c

The demo shows the AI voice-agent qualification flow and the connected automation workflow.

## 🚀 Project Overview

This project was built as an AI CRM Lead Qualification Voice Agent capstone using **Vapi + n8n** with integrations for **HubSpot CRM, Google Calendar, and Gmail**.

The agent conducts a natural voice conversation with a prospective customer, collects:

- **Budget**
- **Authority**
- **Need**
- **Timeline**

It then qualifies the lead, updates the CRM, and—when the lead is eligible—offers meeting slots, schedules the selected time, and sends a confirmation.

## 🧩 Architecture

```text
Caller
  ↓
Vapi Voice Agent
  ↓
Vapi Tool Calls
  ↓
n8n Webhook / Workflow
  ├── qualify_lead
  ├── update_crm → HubSpot
  ├── check_calendar_slots → Calendar
  ├── schedule_meeting → Google Calendar
  └── send_confirmation → Gmail
```

## 📊 BANT Lead Scoring

| Lead Score | Rule |
|---|---|
| **High** | Budget ≥ $5,000 **AND** Timeline ≤ 3 months |
| **Medium** | Budget ≥ $2,000 |
| **Low** | All other cases |

### Scheduling Rules

- **High:** Qualified and eligible for scheduling
- **Medium:** Qualified and eligible for scheduling
- **Low:** Not offered meeting booking

## 🔧 Tools

### `qualify_lead`
Evaluates the collected BANT information and returns the lead score and qualification status.

### `update_crm`
Creates or updates the lead/contact in HubSpot.

### `check_calendar_slots`
Retrieves available meeting slots for the requested date.

### `schedule_meeting`
Books the slot selected by the lead.

### `send_confirmation`
Sends the meeting confirmation by email after a successful booking.

## 🛠️ Technology Stack

- **Vapi** — Voice AI assistant
- **n8n** — Workflow orchestration and tool routing
- **HubSpot** — CRM contact management
- **Google Calendar** — Meeting scheduling
- **Gmail** — Confirmation email
- **Twilio** — Optional PSTN telephony integration

## 🧪 Demo Test Scenario

A High-score test scenario can use:

- **Name:** Shaik Shaheed
- **Company:** Apex Technologies
- **Budget:** $10,000
- **Authority:** Decision maker
- **Need:** AI CRM automation solution
- **Timeline:** Within 1 month

Expected flow:

```text
BANT Collection
      ↓
Lead Qualification
      ↓
HubSpot CRM Update
      ↓
Calendar Availability
      ↓
Meeting Booking
      ↓
Email Confirmation
      ↓
Professional Call Closure
```

## 📁 Suggested Repository Structure

```text
ai-crm-lead-qualification-voice-agent/
├── README.md
├── n8n/
│   └── workflow.json
├── vapi/
│   ├── assistant-prompt.md
│   └── tool-definitions.md
├── screenshots/
└── docs/
    └── implementation-notes.md
```

## 🔐 Security

Do not commit API keys, OAuth secrets, passwords, webhook secrets, or other credentials to this repository. Store credentials in the respective platform's secure credential manager or environment variables.

## ⚠️ Assumptions & Limitations

The demonstrated capstone call can be run as a simulated Vapi web call when PSTN/Twilio setup is not available. Scheduling behavior depends on the configured calendar workflow and business-hour assumptions.

## 🎓 Capstone Deliverable

This repository documents the implementation of an AI CRM Lead Qualification Voice Agent with BANT-based qualification, automated CRM updates, meeting scheduling, and confirmation dispatch.
