# Project 02 — AI Lead Notification Automation

AI-powered lead processing workflow built with n8n, OpenAI, Google Sheets, and WhatsApp.

## Overview

This project automates the first stage of lead qualification and notification.

When a potential customer submits a Google Form, the response is stored in Google Sheets. n8n detects the new row, sends the lead information to OpenAI for analysis, structures the AI response, and sends a WhatsApp notification containing the lead summary, priority, and recommended next action.

## Architecture

```text
Google Forms
     ↓
Google Sheets
     ↓
Google Sheets Trigger
     ↓
Edit Fields
     ↓
OpenAI — GPT-4.1-mini
     ↓
Parse Fields
     ↓
HTTP Request
     ↓
CallMeBot
     ↓
WhatsApp Notification
```

## Workflow

The automation performs the following steps:

1. Detects a new lead in Google Sheets.
2. Extracts and normalizes the relevant lead information.
3. Sends the lead's service interest and project description to OpenAI.
4. Generates:

   * A concise summary
   * A priority level: High, Medium, or Low
   * A recommended next action
5. Parses the AI response into structured fields.
6. Sends the original lead information and AI analysis through WhatsApp.

## Example Output

```text
🚨 New Lead

👤 Name: John Smith
📧 Email: john@example.com
🏢 Company: Example Company
🛠 Service: Automation Consulting

📌 Summary: The prospect is looking to automate
an internal lead management process.

⭐ Priority: High

💡 Recommendation: Contact the prospect to
clarify requirements and schedule a discovery call.
```

## Technologies

* n8n
* OpenAI API
* GPT-4.1-mini
* Google Forms
* Google Sheets
* HTTP APIs
* CallMeBot
* WhatsApp
* JSON
* n8n expressions

## Security

The workflow included in this repository has been sanitized for public use.

Personal identifiers, API keys, credentials, private resource IDs, and n8n instance metadata have been replaced or removed.

Before running the workflow, configure your own:

* Google Sheets credentials
* OpenAI credentials
* CallMeBot API key
* WhatsApp phone number
* Google Sheet ID and Sheet GID

## What I Learned

This project focuses on understanding how different automation components work together rather than simply connecting pre-built nodes.

Key concepts practiced:

* Event-driven automation
* API integrations
* LLM integration
* Prompt design
* JSON parsing
* Data transformation
* n8n expressions
* Workflow debugging
* Credential and secret management
* Automated operational notifications

## Future Improvements

Possible future iterations include:

* Structured output validation
* Error handling and retry logic
* Persistent lead storage
* CRM integration
* Lead scoring based on configurable business rules
* Human approval before contacting high-priority leads
* Direct WhatsApp Business API integration
* Logging and monitoring
