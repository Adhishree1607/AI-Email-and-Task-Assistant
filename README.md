# AI Email & Task Assistant

An AI-powered email and task assistant built with **n8n**, **Gmail**, **Google Gemini**, **Google Sheets**, and **Telegram**.

## What it does

1. Watches Gmail for incoming emails.
2. Passes email sender, subject, and preview to an AI Agent.
3. Uses Google Gemini to summarize the email, classify priority, extract tasks and deadlines, and recommend an action.
4. Appends the analysis to a Google Sheets task tracker.
5. Sends the result to a configured Telegram chat.

## Workflow

```text
Gmail Trigger
     |
     v
  AI Agent <--- Google Gemini Chat Model
     |
     v
Google Sheets (append task record)
     |
     v
Telegram (send notification)
```

## Requirements

- An n8n instance
- Gmail OAuth2 credentials
- Google Gemini API credentials
- Google Sheets OAuth2 credentials
- Telegram Bot credentials and a Telegram chat ID
- A Google Sheet with columns matching the fields used by the workflow

## Import and configure

1. In n8n, import `AI-Email-Assistant.json`.
2. Open each Gmail, Gemini, Google Sheets, and Telegram node.
3. Create or select the corresponding credentials in n8n.
4. In the Google Sheets node, replace `REPLACE_WITH_YOUR_GOOGLE_SHEET_ID` with your own spreadsheet ID and select the correct sheet tab.
5. In the Telegram node, replace `REPLACE_WITH_YOUR_TELEGRAM_CHAT_ID` with your own chat ID.
6. Review the node connections and test with a non-sensitive sample email before activating the workflow.

## Google Sheets columns

The workflow expects these columns:

- Received At
- Sender
- Subject
- Summary
- Priority
- Task
- Deadline
- Recommended Action
- Status

## Security

- Never commit API keys, OAuth tokens, bot tokens, passwords, private email contents, or real customer/patient data.
- Configure credentials inside n8n; do not paste secrets into this repository.
- Replace all placeholder values with your own settings only inside your private n8n instance.
- Review workflow exports before publishing them.

## Notes

This repository contains a sanitized workflow template. Credential references and account-specific identifiers have been removed. You must reconnect credentials and configure your own Google Sheet and Telegram chat before running it.
