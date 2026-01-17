# Calls

Create and manage web and phone calls.

## Create web call

Create a new web call session for an AI agent.

- Method: POST
- Path: `/v1/calls/create-web-call`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier for the call.
- `override_ai_agent_id` (string, optional): Use a different agent for this call only.
- `metadata` (object, optional): Custom key-value data attached to the call.
- `pia_llm_dynamic_data` (object, optional): Dynamic data available to the agent.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "ai_agent_id": "agent_id",
    "metadata": {"source": "web", "campaign": "spring"},
}
call = client.calls.create_web_call(payload)
```

## Create public web call

Create a web call using a shared public key.

- Method: GET
- Path: `/v1/calls/public/create-web-call`

### Parameters

- `ai_agent_id` (string, required): AI agent identifier.
- `shared_key` (string, required): Public shared key for access.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
call = client.calls.create_public_web_call(ai_agent_id="agent_id", shared_key="shared_key")
```

## Dial outbound phone call

Start an outbound phone call from an agent.

- Method: POST
- Path: `/v1/calls/dial-outbound-phone-call`

### Parameters

- `from_number` (string, required): Caller phone number in E.164 format.
- `to_number` (string, required): Recipient phone number in E.164 format.
- `direction` (string, required): `inbound` or `outbound`.
- `call_id` (string, optional): Custom call identifier.
- `override_ai_agent_id` (string, optional): Use a different agent for this call.
- `metadata` (object, optional): Custom call metadata.
- `pia_llm_dynamic_data` (object, optional): Dynamic data available to the agent.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "from_number": "+12065551212",
    "to_number": "+14155551212",
    "direction": "outbound",
    "metadata": {"source": "crm"},
}
call = client.calls.dial_outbound_phone_call(payload)
```

## Get call

Retrieve a single call by ID.

- Method: GET
- Path: `/v1/calls/{call_id}`

### Parameters

- `call_id` (string, required): Call identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
call = client.calls.get("call_id")
```

## List calls

Retrieve calls with filters and pagination.

- Method: GET
- Path: `/v1/calls`

### Parameters

- `ai_agent_ids` (list[string], optional): Filter by agent IDs.
- `start_time_before` (string, optional): ISO-8601 time filter.
- `start_time_after` (string, optional): ISO-8601 time filter.
- `end_time_before` (string, optional): ISO-8601 time filter.
- `end_time_after` (string, optional): ISO-8601 time filter.
- `sort_direction` (string, optional): `asc` or `desc`. Default: `desc`.
- `page_size` (int, optional): 1-1000. Default: 100.
- `page_token` (string, optional): Pagination token.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
calls = client.calls.list(page_size=100, sort_direction="desc")
```
