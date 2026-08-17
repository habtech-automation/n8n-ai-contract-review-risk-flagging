# AI Contract Review & Risk Flagging System

An AI-powered contract review system built in n8n that automatically
reads contracts the moment they are uploaded, identifies risky clauses,
and delivers a structured risk report to Slack and email without any
human review needed.

---

## The Problem

Reviewing contracts manually takes hours and risks missing critical
clauses. Legal teams and business owners either pay expensive lawyers
for routine reviews or skip the review entirely. This system reads
every contract automatically and flags risks in minutes.

---

## Business Impact

- Contract review time reduced from hours to under 5 minutes
- Every contract reviewed consistently with no clauses missed
- Risk reports delivered instantly to Slack and email
- Full audit trail of every review logged to Google Sheets

---

## Architecture

Watch Contracts Folder (Google Drive)
↓
Download Contract PDF (Google Drive)
↓
Extract Text from PDF
↓
Prepare Contract Data
↓
AI Agent (OpenRouter Chat Model + Structured Output Parser)
↓
Parse & Format Risk Report
↓
├── Slack — Risk Report Alert
├── Log Review to Google Sheets
└── Gmail — Full Risk Report Email

---

## How It Works

1. A new contract PDF is uploaded to a watched Google Drive folder
2. n8n downloads the file and extracts all text from the PDF
3. Contract data is prepared and passed to the AI Agent
4. The AI Agent reads the contract and identifies risky clauses,
   unfavourable terms, and areas needing attention
5. The structured output parser formats the findings into a clean
   risk report
6. The report is sent to Slack as an alert, emailed in full via
   Gmail, and logged to Google Sheets for record keeping

---

## Stack

| Layer | Tool |
|---|---|
| Automation | n8n (self-hosted) |
| AI/LLM | OpenRouter Chat Model |
| Document Source | Google Drive |
| PDF Processing | PDF Extract Node |
| Output | Slack · Gmail · Google Sheets |

---

## Setup Instructions

1. Import `workflow.json` into your n8n instance
2. Add credentials:
   - Google Drive OAuth
   - OpenRouter API Key
   - Slack Bot Token
   - Gmail OAuth
   - Google Sheets OAuth
3. Set your Google Drive folder ID in the Watch Contracts Folder node
4. Set your Google Sheets ID in the Log Review node
5. Update your Slack channel in the Risk Report Alert node
6. Activate the workflow
7. Upload a sample contract PDF to your watched folder to test

---

## Files

| File | Description |
|---|---|
| `workflow.json` | Importable n8n workflow — all credentials removed |
| `assets/screenshot.png` | Workflow canvas screenshot |

---

Built by [Sulyman Habeebullah](https://github.com/yourusername) —
AI Automation Engineer
