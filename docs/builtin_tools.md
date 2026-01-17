# Built-in Tools

List, create, update, and delete built-in tools for an AI agent.

## Endpoints

- List: `GET /v2/ai-agents/{ai_agent_id}/builtin-tools`
- Get: `GET /v2/ai-agents/{ai_agent_id}/builtin-tools/{tool_id}`
- Create: `POST /v2/ai-agents/{ai_agent_id}/builtin-tools`
- Update: `PUT /v2/ai-agents/{ai_agent_id}/builtin-tools/{tool_id}`
- Delete: `DELETE /v2/ai-agents/{ai_agent_id}/builtin-tools/{tool_id}`

## SDK examples

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")

tools = client.builtin_tools.list("agent_id", page_size=20)
tool = client.builtin_tools.get("agent_id", "tool_id")
created = client.builtin_tools.create(
    "agent_id",
    {"tool_name": "send_email", "from_email": "you@example.com", "app_password": "app_password"},
)
updated = client.builtin_tools.update("agent_id", "tool_id", {"tool_description": "Updated"})
client.builtin_tools.delete("agent_id", "tool_id")
```

## Common parameters

- `tool_name` (string): Tool identifier, e.g. `send_email`, `transfer_call`, `book_calendar`.
- `tool_description` (string): Tool description.
- `tool_start_message` (string): Message shown when tool starts.
- `tool_delayed_message` (string): Message shown when tool is delayed.
- `tool_complete_message` (string): Message shown when tool completes.
- `tool_failed_message` (string): Message shown when tool fails.

### Email tool

- `from_email` (string): Sender email address.
- `app_password` (string): App password for email authentication.

### Transfer call tool

- `transfer_to` (string): Destination phone number or target.
- `transfer_type` (string): `cold_transfer` or `warm_transfer`.
- `display_phone_number` (boolean): Show the number during transfer.

### Calendar tools

- `event_type_id` (string): Calendar event type identifier.
- `cal_api_key` (string): Calendar API key.
- `timezone` (string): Timezone for booking or availability.
