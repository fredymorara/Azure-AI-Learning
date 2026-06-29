# Module 02: Orchestrating AI Agents with Custom Function Calling

## Objective

Engineered an AI agent capable of executing custom, local Python functions to bridge the gap between generative language models and external logic. The agent acts as an astronomical assistant, equipped with tools to query event datasets, calculate dynamic pricing, and generate formatted physical reports based on user constraints.

## Key Skills Demonstrated

- **Agentic Tool Calling (Function Calling):** Defined complex custom tools using JSON schemas to enforce strict parameter types (e.g., parsing strings for telescope tiers and integers for hours).
- **State & Context Management:** Managed multi-turn conversation threads where the agent synthesized outputs from previous tool calls to execute subsequent ones.
- **Local Execution Integration:** Seamlessly passed the model's structured JSON outputs back to local Python functions (`next_visible_event`, `calculate_observation_cost`, `generate_observation_report`) and returned the computed results to the agent.

## Technical Implementation

Rather than relying on pre-built cloud tools, the agent's capabilities were entirely custom-defined via the `azure.ai.projects.models.FunctionTool` class. The workflow handled the end-to-end lifecycle: intercepting a `function_call` from the model, mapping it to the correct local Python function, unpacking the arguments, and injecting the `function_call_output` back into the model's context window.

## Evidence of Work

### Terminal Execution Log

Demonstrating the agent handling a multi-tool prompt and a follow-up file-generation request:

```text
Enter a prompt for the astronomy agent. Use 'quit' to exit.
USER: Find me the next event I can see from South America and give me the cost for 5 hours of premium telescope time at normal priority.
AGENT: The next event visible from South America is the **Saturn-Mars Conjunction** on **07-10**.

Cost for **5 hours** of **premium** telescope time at **normal** priority: **$1,875.00**.

Enter a prompt for the astronomy agent. Use 'quit' to exit.
USER:  Generate that information in a report for Bellows College.
AGENT: Report generated for Bellows College.

Summary:
- Event: Saturn-Mars Conjunction
- Date: 07-10
- Visible from: South America
- Telescope: Premium
- Time: 5 hours
- Priority: Normal
- Cost: $1,875.00

Report file:
- report_saturn-mars_conjunction_2026-06-29_1941.txt
```

### Generated Artifacts

- The agent successfully triggered local file I/O operations, producing the physical report which can be found in the [assets/](./assets/) directory.
