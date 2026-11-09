# The Exorcist - Automated AIOps Incident Response Pipeline
This is a Halloween-themed AIOps pipeline built by our team during the Sunderland GDG Hackathon to automate software debugging and incident response. It catches application crash reports, utilizes the Google Gemini API to analyze the root causes, suggest code patches and passes the data to a JavaScript node to format and sanitize the data and logs the data onto Google Sheets. We also implemented a bug-severity assessment that automatically sends emails and schedules emergency meetings for critical bugs.



## System Architecture And Data-Flow

### Workflow

[App Crash Payload] -> [n8n Webhook] -> [Gemini AI Analysis] -> [JavaScript Parsing] -> [Google Sheets Log] -> [IF Severity Check] -> [Gmail and Calendar Alerts]

### System Architecture

**Catching System Errors:** A flask web app sends diagnostic crash data to an n8n webhook node through an HTTP POST request.

**AI Analysis:** Google Gemini API reads the raw code, locates the error, assigns a haloween-themed severity level(Poltergeist, Wraith or Archdemon), and suggests a code patch.

**Data Formatting:** Custom JavaScript code cleans Gemini's output and formats it into a structured JSON payload.

**Logging:** The details about each error, the time they occurred, the severity level and the code patches are recorded into Google sheets

**Escalation:** If the bug severity is critical(Archdemon), n8n automatically schedules a Google Calendar meeting and sends an emergency Gmail alert to the team.




## Tech Stacks

n8n Cloud

Google Gemini API

Python (Flask)

Webhooks

JavaScript

Google Sheets API

Gmail API

Google Calendar API



## Key Features

**Real-time Incident Response:** Instantly captures errors through Webhooks.

**Automated Analysis:** Uses Gemini API to diagnose the code and suggest patches.

**Severity Classification:** Uses Gemini API to categorize these bugs into custom severity levels.

**Automated Alerting:** Utilizes Google Workspace APIs to automatically send emergency emails and schedule emergency meetings on Google calendar for high-severity bugs.



## Repository Structure

**my_workflow.json -** The complete exported n8n pipeline nodes.

**app.py -** The python flask app that triggers crash events.

**git.ignore -** Specifies files to keep sensitive API keys and cache out of Git

**readme.md -** Project documentation and architecture details.

