# Job Application Automation for n8n

An n8n workflow that collects remote-job leads, screens them against defined criteria, tailors a truthful CV, estimates ATS fit, and records the outcome in a Google Sheets tracker.

## What it does

- Runs on a daily Lagos-time schedule or manually.
- Collects job alerts from Gmail and searches Remotive, Jobicy, and Himalayas.
- Removes duplicates and applies role/remote-eligibility checks.
- Uses locally supplied CV facts to tailor a CV and estimate ATS fit with Ollama.
- Renders and uploads an approved CV PDF, then tracks the application route and status.

## Requirements

- An n8n instance (self-hosted recommended for the local Ollama/PDF steps).
- Google credentials configured in n8n for Gmail, Google Drive, and Google Sheets.
- An Ollama instance with the model selected in the workflow, or an equivalent replacement node.
- A Google Sheet for the application tracker and a Drive folder for rendered CVs.

## Import and configure

1. In n8n, choose **Workflows → Import from File** and select `n8n-job-application-workflow.json`.
2. Open the imported workflow and replace every `__REPLACE_*__` placeholder with your own configuration.
3. Attach your own n8n credential records to the Gmail, Sheets, and Drive nodes; credential records are intentionally not included here.
4. Set the job search terms, CV facts, tracker sheet, Drive folder, and Ollama URL/model.
5. Run it manually with sample data before activating the daily schedule.

## Security

This repository contains no credential exports, OAuth tokens, client secrets, private webhook URLs, or local profile data. Keep those values in n8n credentials or environment variables—not in workflow JSON or source control.

## Notes

The workflow is designed to support reviewable, truthful applications. Validate every tailored CV and application route before submitting an application.
