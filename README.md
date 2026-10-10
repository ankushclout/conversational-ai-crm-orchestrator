# Coaching FAQ & Lead Capture Bot

An n8n workflow that answers Telegram coaching queries using a PDF brochure and records leads in Google Sheets.

[Try the Telegram bot](https://t.me/RajeshCoachingFAQ_bot)

## How it works

- Text messages download and extract the brochure, generate a contextual answer, save or update the lead, and send the reply.
- Shared contacts update the phone number and receive an acknowledgement.
- Chat ID identifies each lead; chat memory keeps a conversation history per chat.

## Setup

1. Import `workflow.json` into n8n.
2. Connect your Telegram credentials to the trigger and both send nodes. Use a separate bot for each active Telegram workflow.
3. Connect Google Sheets credentials to both CRM nodes. Replace `YOUR_GOOGLE_SHEET_ID` with your own spreadsheet ID.
4. Create a `Leads` tab with these headers: `Chat ID`, `Name`, `Username`, `Phone Number`, `Last Question`, `Timestamp`.
5. Connect your OpenAI credentials or a supported n8n AI Gateway connection. Check model availability in your account.
6. Set your public brochure PDF URL in `Download Brochure PDF`. The included public URL is a Drishti IAS demo brochure; this project is not affiliated with the institute.
7. Test a text message and a contact share separately, then publish the workflow.

## Validation and limitations

The original configured workflow completed a successful text-message execution, including CRM save and Telegram reply. This sanitized export has not been run with new credentials. The text and contact branches need separate tests.

The full brochure is sent to the model for each question, which can add latency and token cost. Model and hosting availability affect the live demo. The bot can miss details or produce incorrect answers; verify important admission information against the brochure. Sharing a phone number is optional and stores it in the configured CRM spreadsheet.

## Export contents

This export omits credential references, instance metadata, workflow identifiers and pinned data. The import is inactive until you configure and publish it. No API tokens or real CRM spreadsheet links are included.
