# Agency Core custom instructions with AgentKit

This example shows how to pass user-provided custom instructions into an `AgentKit` instance when using the `agency_core` framework.
The snippet below extends the base AgentKit configuration with a weekly email workflow instruction.

## Example

```python
from agency_core import AgentKit

llama_agent = AgentKit.from_agent(
    name="MVP-LLaMA-Agent-01",
    model="llama3-8b",  # or llama2, etc.
    scope=["data_sweep", "validation", "reporting"],
    permissions=["autonomous_task_execution", "logging"],
    report_to="aura-core"
)

llama_agent.activate()

# User-provided custom instructions
custom_instructions = [
    "Run workflow send email once weekly",
]

llama_agent.add_instructions(custom_instructions)
```

The `custom_instructions` list can include any additional guardrails or automations your user wants.
After activating the agent, call `add_instructions` to apply them before the workflow starts.
