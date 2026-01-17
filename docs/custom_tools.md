# Custom Tools

List, create, update, and delete custom tools for an AI agent.

## Endpoints

- List: `GET /v2/ai-agents/{ai_agent_id}/custom-tools`
- Get: `GET /v2/ai-agents/{ai_agent_id}/custom-tools/{tool_id}`
- Create: `POST /v2/ai-agents/{ai_agent_id}/custom-tools`
- Update: `PUT /v2/ai-agents/{ai_agent_id}/custom-tools/{tool_id}`
- Delete: `DELETE /v2/ai-agents/{ai_agent_id}/custom-tools/{tool_id}`

## SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")

payload = {
    "openai_tool": {
        "name": "get_delivery_date",
        "description": "Get the delivery date for a customer's order",
        "parameters": {
            "type": "object",
            "properties": {
                "order_id": {"type": "string", "description": "Order ID"},
            },
            "required": ["order_id"],
            "additionalProperties": False,
        },
    },
    "additional_tool_info": {
        "api": {
            "endpoint": "https://api.example.com/test",
            "headers": {"Content-Type": "application/json"},
            "method": "POST",
            "parameters": {
                "fixed_params": {
                    "api_key": {"description": "API key for authentication", "value": "test-api-key"}
                },
                "runtime_params": {},
            },
        },
        "tool_type": "custom",
    },
}

tool = client.custom_tools.create("agent_id", payload)
```

## Parameters overview

- `openai_tool` (object, required): Tool interface definition.
  - `name` (string): Tool name used by the model.
  - `description` (string): What the tool does.
  - `parameters` (object): JSON schema for inputs.
- `additional_tool_info` (object, required): API integration details.
  - `api.endpoint` (string): Full API URL.
  - `api.method` (string): HTTP method.
  - `api.headers` (object): HTTP headers.
  - `api.parameters.fixed_params` (object): Constant parameters.
  - `api.parameters.runtime_params` (object): Runtime parameters.
  - `tool_type` (string): Must be `custom`.
- `tool_start_message` (string): Message shown on tool start.
- `tool_delayed_message` (string): Message shown on tool delay.
- `tool_complete_message` (string): Message shown on completion.
- `tool_failed_message` (string): Message shown on failure.
