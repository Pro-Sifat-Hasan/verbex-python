# Create AI Agent

Create a new AI agent with the provided configuration.

## Endpoint

- Method: POST
- Path: `/v2/ai-agents`

## Required fields

- `agent_name` (string): Display name for the agent.
- `llm` (object): Language model configuration.
- `tts` (object): Text-to-speech configuration.
- `stt` (object): Speech-to-text configuration.

## Common optional fields

- `language_code` (string): BCP-47 language, default `en-US`.
- `knowledge_base_id` (string): Optional knowledge base ID.
- `enable_user_interruptions` (boolean): Allow user interruptions.
- `minimum_speech_duration_for_interruptions` (number): Seconds before interruption allowed.
- `minimum_words_before_interruption` (integer): Words required before interruption.
- `wait_time_before_detecting_end_of_speech` (number): Silence timeout before end-of-speech.
- `ambient_sound` (string): Background sound preset.
- `ambient_sound_volume` (number): 0-2 volume.
- `webhook_url` (string): Webhook URL for call events.
- `end_call_after_silence_seconds` (number): Silence timeout before ending call.
- `max_call_duration_seconds` (number): Max call length.
- `welcome_message` (string): Greeting message for the call.
- `voicemail_detection_timeout_seconds` (number): Voicemail detection timeout.

## SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")

payload = {
    "agent_name": "Example Agent",
    "llm": {
        "llm_type": "simple",
        "model_provider": "openai",
        "model_name": "gpt-4",
        "system_prompt": "You are helpful.",
        "model_temperature": 0,
    },
    "tts": {
        "provider": "elevenlabs",
        "voice_id": "voice_id",
        "voice_name": "Default",
        "model_name": "eleven_turbo_v2_5",
        "voice_temperature": 0.2,
    },
    "stt": {"provider": "deepgram", "model": "nova-2-general"},
}

agent = client.ai_agents.create(payload)
```
