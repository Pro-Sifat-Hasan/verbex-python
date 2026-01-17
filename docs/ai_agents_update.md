# Update AI Agent

Update an existing AI agent by ID.

## Endpoint

- Method: PUT
- Path: `/v2/ai-agents/{agent_id}`

## Common fields

- `agent_name` (string): Display name for the agent.
- `language_code` (string): BCP-47 language code.
- `llm` (object): Updated model config.
- `stt` (object): Updated STT config.
- `tts` (object): Updated TTS config.
- `knowledge_base_id` (string): Knowledge base ID.
- `enable_user_interruptions` (boolean): Allow interruptions.
- `minimum_speech_duration_for_interruptions` (number): Seconds before interruption allowed.
- `minimum_words_before_interruption` (integer): Words required before interruption.
- `wait_time_before_detecting_end_of_speech` (number): Silence timeout.
- `ambient_sound` (string): Background sound preset.
- `ambient_sound_volume` (number): 0-2 volume.
- `webhook_url` (string): Webhook URL for call events.
- `end_call_after_silence_seconds` (number): Silence timeout before ending call.
- `max_call_duration_seconds` (number): Max call length.
- `welcome_message` (string): Greeting message.
- `voicemail_detection_timeout_seconds` (number): Voicemail detection timeout.

## SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")

payload = {
    "agent_name": "Updated name",
    "welcome_message": "Hello, how can I help?",
}

agent = client.ai_agents.update("agent_id", payload)
```
