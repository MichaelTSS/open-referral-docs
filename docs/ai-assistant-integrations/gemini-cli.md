# Gemini CLI

Connect Open Referral to Gemini CLI. The most reliable path today uses a personal
Open Referral token via an HTTP header (it bypasses Gemini CLI's OAuth auto-discovery).

!!! info

    🚧 Screenshots coming soon.

## Prerequisites

<!-- Open Referral account, Admin/Recruiter role, eligible plan. A personal API token (orf_...). -->

## Connect Open Referral

1. Open your Gemini CLI config file: `~/.gemini/settings.json`.
2. Add Open Referral under `mcpServers`:

```json
{
  "mcpServers": {
    "open-referral": {
      "httpUrl": "https://mcp.openreferral.io",
      "headers": {
        "Authorization": "Bearer ${OPEN_REFERRAL_TOKEN}"
      }
    }
  }
}
```

3. Put your token in the `OPEN_REFERRAL_TOKEN` environment variable (do **not** paste it directly in the file).
4. Restart Gemini CLI and run `/mcp list` — `open-referral` should show as connected.

## Try it

<!-- Example prompts once connected. -->

## Troubleshooting

**`Cannot perform dynamic registration without issuer`** — this is Gemini CLI's OAuth
auto-discovery failing. Use the Bearer-token method above instead of `/mcp auth`.
