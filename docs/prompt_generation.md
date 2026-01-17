# Prompt Generation

Generate a refined prompt from raw input and optional instructions.

## Generate prompt

- Method: POST
- Path: `/v1/prompt-generation/prompt/generate`

### Parameters

- `raw_prompt` (string, required): The raw prompt input.
- `instructions` (string, optional): Guidance for how to rewrite the prompt.

### SDK example

```python
import verbex

client = verbex.Verbex(api_key="YOUR_API_KEY")
payload = {
    "raw_prompt": "Make a support agent prompt for returns.",
    "instructions": "Be concise and friendly.",
}
result = client.prompt_generation.generate_prompt(payload)
```
