# Module 06: Build a workflow in Microsoft Foundry

## Objective

Implemented a customer support ticket triage workflow using Microsoft Foundry. The workflow classifies inbound support tickets, applies conditional routing, and generates responses for non-billing issues using AI agents.

## Key Skills Demonstrated

- **Workflow design in Foundry:** Built a visual workflow that processes tickets with a loop, agent invocations, and conditional branches.
- **Agent orchestration:** Used a `Triage-Agent` to classify support tickets and a `Resolution-Agent` to generate suggested responses.
- **Decision logic:** Routed billing issues for human escalation and handled low-confidence predictions with a fallback message.
- **Local client integration:** Executed the same workflow from Python using the Azure AI Projects SDK and streamed workflow output to the console.

## Technical Implementation

The lab includes two main parts:

1. **Foundry workflow authoring**
   - Created a `Set variable` node containing sample support tickets.
   - Added a `For each` loop to process each ticket.
   - Invoked a triage agent to classify tickets into `Billing`, `Technical`, or `General` categories.
   - Added an `If/Else` branch to handle low-confidence classifications.
   - Routed billing issues to escalation and passed non-billing tickets to a resolution agent.

2. **Python client execution**
   - Used `workflow.py` to connect to the Azure AI Project endpoint and invoke the workflow by name.
   - Streamed response events from `openai_client.responses.create(..., stream=True)`.
   - Parsed the final workflow output and printed a ticket-by-ticket summary.

## Evidence of Work

### Local execution output

The workflow ran successfully from the local Python client and produced structured support ticket results. Example output:

- Ticket 1: Technical (93% confidence)
  - Issue: API returns a 403 error when creating invoices; API key unchanged.
- Ticket 2: General (96% confidence)
  - Issue: Wants to export all invoices as a CSV.
- Ticket 3: Billing (99% confidence)
  - Issue: Charged twice for the same invoice last Friday; customer sees two receipts; requesting a fix.

### Workflow success

The workflow was also validated in the Foundry portal, with the visual workflow running as expected and the local Python client successfully invoking the workflow.

## Supporting files

- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/workflow.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/workflow.py)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/requirements.txt](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/requirements.txt)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/.env](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/06-build-workflow-ms-foundry/Python/.env)

## Notes

- The local environment was created using `python -m venv labvenv` and the dependencies installed with `pip install -r requirements.txt`.
- The workflow was executed with `python workflow.py` after Azure CLI login.
- The output confirmed the workflow run completed and the conversation was deleted cleanly.
