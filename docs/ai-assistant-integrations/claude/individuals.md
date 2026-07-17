---
description: Add Open Referral to Claude yourself on a Free, Pro or Max plan.
---

# Claude — for individuals (Free, Pro, Max)

This guide is for individual Claude plans, where you add and manage the connector yourself.
On **Team/Enterprise**, see [For Team & Enterprise](team-enterprise.md) instead.

!!! info

    **Free** plans can add **one** custom connector; **Pro** and **Max** allow more.

## Step 1 — Open the Connectors settings

Go to **Customize → Connectors**.

!!! info

    :camera: *Screenshot to add: the Connectors settings page with the "+" button.*

## Step 2 — Add a custom connector

Click **+** → **Add custom connector**.

!!! info

    :camera: *Screenshot to add: the "Add custom connector" dialog.*

## Step 3 — Enter the Open Referral server URL

1. **Name:** `Open Referral`
2. **Remote MCP server URL:** `https://mcp.openreferral.io`
3. Leave **Advanced settings** empty — no OAuth Client ID or Secret is required.
4. Click **Add**.

## Step 4 — Connect and authorize

Click **Connect** on the Open Referral connector, then in the window that opens:

1. Sign in with your Open Referral account.
2. Review the access requested and click **Authorize**.

The connector now shows as **Connected**.

!!! info

    :camera: *Screenshot to add: the Open Referral consent screen.*

## Step 5 — Use it

In a new chat, enable the Open Referral connector, then ask:

* *"How is our referral program doing this quarter?"*
* *"What's waiting on my team right now?"*
* *"Show me recent referrals with unpaid bonuses."*
* *"What are best practices to relaunch a referral program that's losing steam?"*

## Troubleshooting

* **"No organisations found."** Your account has no Admin or Recruiter role. Ask an admin to grant one.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan.
* **The sign-in window doesn't complete.** Allow pop-ups, finish sign-in and consent, then retry **Connect**.
* **Can't add another connector on Free.** Free is limited to one custom connector — upgrade to Pro/Max for more.
