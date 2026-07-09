# Module 07: AI Agent Framework for Expense Claims

## Objective

Implemented an expense claim assistant using the Agent Framework and Foundry chat integration. The agent reads local expense data, generates an itemized expense claim, and uses a tool to submit the claim via an email-like plug-in function.

## Key Skills Demonstrated

- **Agent Framework usage:** Initialized and ran an async agent with `Agent`, `FoundryChatClient`, and `AzureCliCredential`.
- **Custom tool integration:** Defined a `submit_claim` tool with schema validation for `to`, `subject`, and `body` fields.
- **Local data processing:** Loaded expense data from a local file and passed it as part of the agent prompt.
- **Prompt-driven automation:** Built an agent that converts user intent into a formatted expense claim and confirms submission.

## Technical Implementation

The lab code is located in `Labfiles/07-agent-framework/python/agent-framework.py`.

- `data.txt` contains the expense data in CSV format.
- `agent-framework.py` reads the data and prompts the user:
  - "What would you like me to do with it?"
- The agent uses the expense data and user request to build an email body for `expenses@contoso.com`.
- The `submit_claim` tool is decorated with `@tool(approval_mode="never_require")` so the agent can submit the claim without additional approval prompts.

## Evidence of Work

### Completed local run

Your local run produced the expected result from the expense claim agent:

- The agent loaded this data:
  - `07-Mar-2025, taxi, 24.00`
  - `07-Mar-2025, dinner, 65.50`
  - `07-Mar-2025, hotel, 125.90`
- User intent: `Submit an expense claim`
- The tool output printed the email fields and body.
- The agent response confirmed:
  - `Your expense claim has been submitted to expenses@contoso.com with the itemized expenses and a total of 215.40.`

### Command sequence

- `python -m venv labvenv`
- `.
labvenv\Scripts\Activate.ps1`
- `pip install -r requirements.txt`
- `python agent-framework.py`

## Supporting files

- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/agent-framework.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/agent-framework.py)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/data.txt](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/data.txt)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/requirements.txt](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/07-agent-framework/python/requirements.txt)

## Notes

- The agent uses Azure CLI credentials via `AzureCliCredential()`.
- The tool output is printed directly in the terminal so the expense claim email contents are visible during execution.
- The total expense was correctly computed as `215.40`.
