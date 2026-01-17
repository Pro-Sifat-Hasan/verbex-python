# Post-call Analysis

Configure and retrieve post-call analysis for an AI agent.

## Get configuration

- Method: GET
- Path: `/v2/ai-agents/{ai_agent_id}/postcall-analysis`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
config = client.postcall_analysis.get("agent_id")
```

## Create configuration

- Method: POST
- Path: `/v2/ai-agents/{ai_agent_id}/postcall-analysis`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.
- `items` (array, required): Analysis items for post-call processing.
  - `type` (string, required): `string`, `enum`, `boolean`, or `number`.
  - `name` (string, required): Stable identifier used in results.
  - `description` (string, required): Human-friendly explanation of the analysis.
  - `analysis_prompt` (string, required): Instructions for the analyzer.
  - `temperature` (number, optional): 0-1, default 0.1.
  - `model` (string, optional): Model name, default `gpt-4o`.
  - `response_format` (object, optional): JSON schema for structured responses.
  - `choices` (array, optional): Required when `type` is `enum`.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "items": [
        {
            "type": "string",
            "name": "summary",
            "description": "Short call summary for CRM.",
            "analysis_prompt": "Summarize the call in 2 sentences.",
            "temperature": 0.1,
        }
    ]
}
config = client.postcall_analysis.create("agent_id", payload)
```

## Update configuration

This replaces the existing configuration.

- Method: PUT
- Path: `/v2/ai-agents/{ai_agent_id}/postcall-analysis`

### Parameters

Same as create.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "items": [
        {
            "type": "enum",
            "name": "sentiment",
            "description": "Overall sentiment.",
            "analysis_prompt": "Classify sentiment.",
            "choices": ["positive", "neutral", "negative"],
        }
    ]
}
config = client.postcall_analysis.update("agent_id", payload)
```

## Delete configuration

- Method: DELETE
- Path: `/v2/ai-agents/{ai_agent_id}/postcall-analysis`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
client.postcall_analysis.delete("agent_id")
```

## Get analysis results

Retrieve analysis results for a specific call.

- Method: GET
- Path: `/v2/ai-agents/{ai_agent_id}/postcall-analysis/results/{call_id}`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.
- `call_id` (string, required): Call identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
results = client.postcall_analysis.results("agent_id", "call_id")
```
