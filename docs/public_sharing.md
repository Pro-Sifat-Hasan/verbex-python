# Public Sharing

Create and manage public sharing keys for AI agents.

## Create share

- Method: POST
- Path: `/v1/public-sharing`

### Parameters

- `ai_agent_id` (string, required): AI agent to share publicly.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
share = client.public_sharing.create("agent_id")
```

## Get share

- Method: GET
- Path: `/v1/public-sharing/{ai_agent_id}`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
share = client.public_sharing.get("agent_id")
```

## Delete share

- Method: DELETE
- Path: `/v1/public-sharing/{share_id}`

### Parameters

- `share_id` (string, required): Share identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
client.public_sharing.delete("share_id")
```
