# Webhook → n8n Automation Trigger Test

## Overview
This project is a focused test harness designed to verify that a configured webhook endpoint correctly triggers an n8n automation workflow. It provides a controlled, repeatable way to confirm that the webhook-to-n8n integration is functioning as expected, reducing reliance on manual checks and guesswork.

## Background
The system owner is a developer or QA engineer working with n8n — an open-source workflow automation platform. The goal is to validate that an incoming webhook event reliably activates the intended n8n workflow, ensuring the automation pipeline behaves correctly before it is used in a wider context.

## Problems
- **[CRITICAL]** No reliable, repeatable mechanism exists to confirm that a webhook is correctly triggering an n8n automation workflow.
- **[MINOR]** Manual verification of webhook triggers is time-consuming, inconsistent, and difficult to reproduce across environments.

## Stakeholders
| Stakeholder        | Role                  | Key Capabilities Needed                                                   |
|--------------------|-----------------------|---------------------------------------------------------------------------|
| Developer / QA     | Integration tester    | Send test webhook payloads, observe whether the n8n workflow is triggered  |
| n8n Workflow Owner | Automation maintainer | Confirm that workflow activations are triggered by the correct source      |

## Proposed Solutions
1. **Webhook Trigger Test** *(solves: No reliable confirmation mechanism — affects: Developer / QA, n8n Workflow Owner)*
   Send a sample HTTP POST request to the configured webhook URL and verify that the n8n automation workflow is activated in response. Validation can be done by checking n8n execution logs, a response payload, or a side effect produced by the workflow.

2. **Repeatable Test Script** *(solves: Manual verification is inconsistent — affects: Developer / QA)*
   Wrap the webhook call in a simple script so the test can be re-run consistently across environments without manual effort.

## Next Steps
- Configure the target webhook URL (store it in a local `.env` file — do not hardcode it)
- Define a sample payload that the webhook expects
- Write and run the test request (e.g., using `curl`, Postman, or a lightweight script)
- Verify the n8n workflow execution via the n8n dashboard or execution logs
- Document expected vs. actual behaviour for each test run
