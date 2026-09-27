# Custom providers

Koder can use any model server that speaks the OpenAI-compatible Chat Completions API. That includes hosted providers, a gateway run by your team, or a server on your own machine such as vLLM, llama.cpp, LM Studio or Ollama.

## Add one in the app

Open **Settings → Providers** and choose **Connect** next to **Custom provider**.

| Field | What to enter |
| --- | --- |
| Provider ID | A short name for the provider. Use lowercase letters, numbers, hyphens or underscores, for example `mygateway`. |
| Display name | The name shown in the model picker. |
| Base URL | The API root, usually ending in `/v1`. Example: `https://api.example.com/v1` or `http://localhost:8000/v1`. |
| API key | Optional. It is saved in Koder's credential store, not in your configuration file. To read it from an environment variable instead, enter `{env:VARIABLE_NAME}`. |
| Allow self-signed certificate | Turns off TLS verification for this provider. Use it only for a private endpoint you trust, because the connection is no longer protected against interception. |
| Models | One row per model. **ID** is the exact model name the server expects. **Name** is what you see in the picker. |
| Headers | Optional extra HTTP headers, for servers that authenticate with a custom header. |

Choose **Save**. The models appear in the model picker right away.

## Or edit the configuration file

The app writes the same settings you can write by hand. Global configuration lives in `~/.config/koder/koder.json` (or `koder.jsonc`):

```jsonc
{
  "provider": {
    "mygateway": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "My gateway",
      "env": ["MYGATEWAY_API_KEY"],
      "options": {
        "baseURL": "https://api.example.com/v1",
        "headers": { "X-Team": "research" }
      },
      "models": {
        "my-model-id": {
          "name": "My model",
          "limit": { "context": 131072, "output": 16384 }
        }
      }
    }
  }
}
```

- `env` lists environment variables that hold the API key.
- `limit.context` is the model's context window in tokens and `limit.output` its maximum reply length. Set them to what the server actually allows. Koder uses them to decide when to summarize a long conversation, so a value larger than the server's real limit leads to rejected requests.
- Provider settings in a project folder's configuration are ignored until you trust that folder. Settings you want everywhere belong in the global file.

## Check that it works

Run `koder models` and look for your provider's models, or start a session and pick one from the model picker. If a request fails, the error shown in the session includes the status code and the server's message.
