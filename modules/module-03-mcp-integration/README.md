# Module 03: Extending AI Agents with MCP Tools

## Objective

Built an Azure AI agent that can connect to a local Model Context Protocol (MCP) server and use its exposed tools to answer inventory-related questions. The agent combines Azure AI Projects with a lightweight MCP server so it can reason over external tool results rather than relying only on its base model knowledge.

## Key Skills Demonstrated

- **MCP Integration:** Connected an agent to a local MCP server over a stdio transport.
- **Tool Grounding:** Wrapped MCP server capabilities as function tools that the agent could call during a conversation.
- **Multi-Turn Agent Reasoning:** Sent tool outputs back into the model context so follow-up prompts could be answered using fresh, grounded data.
- **Local Tool Execution:** Exposed inventory and sales logic through a FastMCP server and invoked it from the client application.

## Technical Implementation

The lab uses a small client/server pattern:

- The MCP server, implemented in [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/server.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/server.py), defines inventory-focused tools such as `get_inventory_levels()` and `get_weekly_sales()`.
- The client, implemented in [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/client.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/client.py), starts the server, lists available tools, registers them for the agent, and processes function-call responses.
- The agent is created with `PromptAgentDefinition` and uses `FunctionTool` definitions so it can call the MCP server tools during a conversation.

## Evidence of Work

### Representative Interaction Flow

Once the environment is configured and the lab dependencies are installed, the client can be run to start an interactive inventory assistant:

```text
Enter a prompt for the inventory agent. Use 'quit' to exit.
USER: Which products should I restock right now?
AGENT: The agent evaluates inventory and weekly sales data, then recommends items that are below the restock threshold.
```

### Supporting Files

- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/client.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/client.py)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/server.py](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/server.py)
- [Develop AI Agents in Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/requirements.txt](../Develop%20AI%20Agents%20in%20Azure/mslearn-ai-agents/Labfiles/03-mcp-integration/Python/requirements.txt)

### Assets

- The implementation artifacts for this module are stored in the [assets/](./assets/) directory.
