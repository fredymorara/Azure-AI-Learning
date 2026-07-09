# Azure AI Agents Learning Projects

This repository showcases my journey and practical projects in developing AI Agents using Azure AI services, Microsoft Foundry, and various agentic frameworks. The labs included here demonstrate a progressive understanding of building, deploying, and orchestrating intelligent agents capable of complex tool usage and remote routing.

## Project Status Overview

| Lab Module | Status | Description |
|---|---|---|
| **01. Build AI Agents with Portal and VS Code** | ✅ Completed | Built an AI support agent using the `AIProjectClient`, complete with functions for sandbox container interactions, local file saving, and text formatting. |
| **02. Use Custom Functions in an AI Agent** | ✅ Completed | Developed an astronomy observation assistant agent equipped with custom Python function tools (e.g., event reporting and cost calculation). |
| **03. MCP Integration** | ✅ Completed | Created an agent integrated with Model Context Protocol (MCP) tools (`api-specs`), successfully handling dynamic MCP approval requests. |
| **04. Integrate Agent with Foundry IQ** | 🚧 Partially Completed | Set up the Foundry IQ Knowledge Base and Search resources. *Pending*: Need to complete the `agent_client.py` script to establish the project connection, fetch the agent, manage the conversation lifecycle, and handle MCP approval requests for the knowledge base. |

| **06. Build Workflow in MS Foundry** | ✅ Completed | Engineered a multi-stage triage workflow leveraging Foundry's capabilities for customer support routing. |
| **07. Agent Framework** | ✅ Completed | Developed an asynchronous agent utilizing the `agent_framework` to process data inputs and execute designated tools (e.g., submitting simulated expense claims). |
| **08. Agent Orchestration** | ✅ Completed | Engineered a multi-agent orchestration architecture using `SequentialBuilder` to connect specialized agents (Summarizer, Classifier, Action Planner) in sequence. |
| **09. Build Remote Agents with A2A** | ✅ Completed | Built an advanced multi-agent system utilizing Agent-to-Agent (A2A) routing across decoupled endpoints (Title Agent, Outline Agent, Routing Agent) via local servers. |

## Next Steps

To fully complete the remaining pending items, I will need to finish the integration code in **Lab 04**. Specifically, I will add the necessary Azure connection instantiation and the tool-approval request handling block directly in `agent_client.py` as detailed in the instructions.

---
*Created as a showcase of applied knowledge in Azure AI and Agent Orchestration.*
