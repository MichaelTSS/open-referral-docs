---
description: Add Open Referral to Claude for your whole organisation (Team & Enterprise).
---

# Claude — for Team & Enterprise

On Team and Enterprise, connectors are added in two moves: an **Owner** adds Open Referral
once for the organisation, then **each member** connects their own Open Referral account.
Individual plans: see [For individuals (Free, Pro, Max)](individuals.md).

## Part A — Owner: add the connector (one-time)

Only an **Owner** or **Primary Owner** can do this.

1. Go to **Settings → Organization settings → Connectors**.
2. Click **Add → Custom → Web**.
3. **Name:** `Open Referral` · **Remote MCP server URL:** `https://mcp.openreferral.io`.
4. Leave Advanced settings empty (no Client ID/Secret — Open Referral uses DCR). Click **Add**.

!!! info

    :camera: *Screenshot to add: Organization settings → Connectors → Add custom connector.*

## Part B — Each member: connect your account

Once the Owner has added it, every member links their own Open Referral account:

1. Go to **Customize → Connectors**.
2. Find **Open Referral** and click **Connect**.
3. Sign in to Open Referral and click **Authorize** on the consent screen.

!!! info

    :camera: *Screenshot to add: member view — Open Referral with the "Connect" button.*

## Use it

In a new chat, enable the Open Referral connector, then ask e.g.
*"How is our referral program doing this quarter?"* or *"What's waiting on my team right now?"*

## Troubleshooting

* **"Add custom connector" is missing.** Only an Owner can add connectors on Team/Enterprise. Ask your Owner to complete Part A.
* **Open Referral doesn't appear under Customize → Connectors.** Your Owner hasn't added it yet, or it's restricted — check with your admin.
* **"No organisations found."** Your Open Referral account has no Admin or Recruiter role.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan.
