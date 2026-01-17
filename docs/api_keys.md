# API Keys

Create and manage API keys for your account.

## List API keys

- Method: GET
- Path: `/v1/api-keys`

### Parameters

- `page_size` (integer, optional): Page size, default 20.
- `page_token` (string, optional): Pagination token.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
keys = client.api_keys.list(page_size=20)
```

## Create API key

- Method: POST
- Path: `/v1/api-keys`

### Parameters

- `name` (string, required): Descriptive name for the key.
- `expiration_days` (integer, optional): Days until expiration (1-365). Default 30.
- `permissions` (list[string], optional): Permission scopes for the key.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "name": "Development API Key",
    "expiration_days": 30,
    "permissions": ["read", "write"],
}
key = client.api_keys.create(payload)
```

## Get API key

- Method: GET
- Path: `/v1/api-keys/{key_id}`

### Parameters

- `key_id` (string, required): API key identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
key = client.api_keys.get("key_id")
```

## Revoke API key

- Method: POST
- Path: `/v1/api-keys/{key_id}/revoke`

### Parameters

- `key_id` (string, required): API key identifier.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
key = client.api_keys.revoke("key_id")
```
