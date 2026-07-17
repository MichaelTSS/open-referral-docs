---
description: Connect Open Referral to Gemini CLI with a personal token and pilot your referral program in natural language.
---

# Gemini CLI

Connect Open Referral to **Gemini CLI** as a custom MCP server. The most reliable path today
uses a **personal Open Referral token** via an HTTP header — it bypasses Gemini CLI's OAuth
auto-discovery (which currently fails, see [Troubleshooting](#troubleshooting)). Once
connected, ask Gemini about your referral program in plain language; it reads live data from
Open Referral — read-only, and privacy by design.

!!! success

    **What you get:** program metrics, monthly trends, pending team actions, recent referrals
    and best-practice playbooks — straight from your terminal.

## Prerequisites

* **Gemini CLI** installed and working.
* An **Open Referral account** on an eligible plan (**Essential** or **Scale**), with an
  **Admin** or **Recruiter** role.
* A **personal Open Referral API token** (it starts with `orf_`). Generate one in Open
  Referral under your API tokens / Copilot settings.

## Step 1 — Store your token

Put your token in an environment variable (never paste it directly into the config file):

```bash
export OPEN_REFERRAL_TOKEN="orf_your_personal_token"
```

Add that line to your shell profile (`~/.zshrc`, `~/.bashrc`, …) to make it permanent.

## Step 2 — Edit your Gemini CLI settings

Open `~/.gemini/settings.json` (or the project-level `.gemini/settings.json`) and add
Open Referral under `mcpServers`:

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

The `httpUrl` field tells Gemini CLI to use HTTP transport, so the `headers` block is applied.

## Step 3 — Verify the connection

Restart Gemini CLI and run:

```
/mcp list
```

`open-referral` should appear as **connected**. There's no `/mcp auth` step — the Bearer
token authenticates every request directly.

## Step 4 — Use it

Ask, for example:

* *"How is our referral program doing this quarter?"*
* *"What's waiting on my team right now?"*
* *"Show me recent referrals with unpaid bonuses."*
* *"What are best practices to relaunch a referral program that's losing steam?"*

## What Gemini can access

Open Referral exposes **7 read-only tools**. Gemini can read, but never modifies your data.

| Tool | What it returns |
| --- | --- |
| List My Organisations | Organisations where you are Admin or Recruiter |
| Get Program Overview | Total referrals, pipeline, hires, bonuses paid |
| Get Referral Trend | Monthly referral trends |
| List Pending Actions | Items awaiting your team |
| List Recent Referrals | Latest referrals (candidate names minimised) |
| List Knowledge Entries | Best-practice playbooks available |
| Get Knowledge Entry | Full text of a specific playbook |

!!! success

    **Privacy by design:** candidate identities are minimised to a first name + initial. Emails,
    phone numbers and direct identifiers are never sent to Gemini. See our
    [Privacy Policy](https://openreferral.io/privacy.html).

## Troubleshooting

* **`Cannot perform dynamic registration without issuer`** — this appears if you run
  `/mcp auth open-referral`. It's Gemini CLI's OAuth auto-discovery failing, not a server
  problem. Use the **Bearer-token method above** instead of `/mcp auth`.
* **`open-referral` shows as disconnected.** Check that `OPEN_REFERRAL_TOKEN` is set in the
  shell that launched Gemini CLI (`echo $OPEN_REFERRAL_TOKEN`), then restart.
* **"No organisations found."** Your Open Referral account has no Admin or Recruiter role.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan.
