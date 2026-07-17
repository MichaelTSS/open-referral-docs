---
description: Connect Open Referral to Mistral's Le Chat as a custom MCP connector and pilot your referral program in natural language.
---

# Le Chat (Mistral)

Connect Open Referral to **Le Chat** (Mistral) as a *custom MCP connector*. Once connected,
ask Le Chat about your referral program in plain language; it reads live data from Open
Referral — read-only, and privacy by design.

!!! success

    **What you get:** program metrics, monthly trends, pending team actions, recent referrals
    and best-practice playbooks — without leaving Le Chat.

## Prerequisites

* An **Open Referral account** on an eligible plan (**Essential** or **Scale**), with an
  **Admin** or **Recruiter** role.
* A **paid Le Chat plan**. Le Chat's 20+ built-in connectors are available on the free tier,
  but adding your **own custom MCP connector** requires a paid plan.

## Step 1 — Open the Connectors page

In Le Chat, open **Connectors** and click **+ Add Connector**, then switch to the
**Custom MCP Connector** tab.

!!! info

    :camera: *Screenshot to add: the "Add Connector" panel with the Custom MCP Connector tab.*

## Step 2 — Enter the Open Referral server URL

1. **Server URL:** `https://mcp.openreferral.io`
2. **Description** (optional): *Pilot your employee referral program from Le Chat.*
3. Click **Connect**.

!!! info

    :camera: *Screenshot to add: the dialog filled with the Open Referral URL.*

## Step 3 — Authorize

Le Chat detects the authentication method automatically. Open Referral uses **OAuth 2.1**
(with dynamic client registration), so you'll be guided through the consent flow:

1. Sign in with your Open Referral account.
2. Review the access requested and click **Authorize**.

The connector is now connected.

!!! info

    :camera: *Screenshot to add: the Open Referral consent screen.*

## Step 4 — Use it

You can choose whether Le Chat asks permission each time it calls a connector function, or
pre-authorize it. Then ask:

* *"How is our referral program doing this quarter?"*
* *"What's waiting on my team right now?"*
* *"Show me recent referrals with unpaid bonuses."*
* *"What are best practices to relaunch a referral program that's losing steam?"*

## What Le Chat can access

Open Referral exposes **7 read-only tools**. Le Chat can read, but never modifies your data.

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
    phone numbers and direct identifiers are never sent to Le Chat. See our
    [Privacy Policy](https://openreferral.io/privacy.html).

## Troubleshooting

* **No "Custom MCP Connector" option.** Adding custom connectors requires a paid Le Chat plan.
* **"No organisations found."** Your Open Referral account has no Admin or Recruiter role.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan.
* **The consent step doesn't complete.** Allow pop-ups, finish sign-in and consent, then retry **Connect**.
