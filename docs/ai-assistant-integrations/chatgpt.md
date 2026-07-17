---
description: Connect Open Referral to ChatGPT via Developer Mode and pilot your referral program in natural language.
---

# ChatGPT

Connect Open Referral to **ChatGPT** as a custom MCP connector using **Developer Mode**.
Once connected, ask ChatGPT about your referral program in plain language; it reads live
data from Open Referral — read-only, and privacy by design.

!!! success

    **What you get:** program metrics, monthly trends, pending team actions, recent referrals
    and best-practice playbooks — without leaving ChatGPT.

## Prerequisites

* An **Open Referral account** on an eligible plan (**Essential** or **Scale**), with an
  **Admin** or **Recruiter** role.
* A **ChatGPT** plan that supports custom connectors: **Plus, Pro, Team, Enterprise or Edu**.
  Custom MCP connectors are **not available on the Free plan**.

!!! info

    Custom connectors live behind **Developer Mode**, which is currently in beta. On
    **Team/Enterprise/Edu**, a workspace admin may need to enable it for members first.

## Step 1 — Enable Developer Mode

**Individual (Plus/Pro):** go to **Settings → Connectors → Advanced → Developer mode** and turn it on.

**Team / Enterprise / Edu:** an admin enables it in **Workspace Settings → Permissions & Roles**
(*Developer mode / Create custom MCP connectors*), then members turn it on in their own settings.

!!! info

    :camera: *Screenshot to add: the Developer mode toggle in Connectors settings.*

## Step 2 — Create the connector

In **Settings → Connectors**, click **Create** (the **+** button) to add a developer-mode connector.

!!! info

    :camera: *Screenshot to add: the "Create connector" dialog.*

## Step 3 — Enter the Open Referral details

1. **Name:** `Open Referral`
2. **Description:** *Pilot your employee referral program from ChatGPT.*
3. **MCP server URL:** `https://mcp.openreferral.io`
4. **Authentication:** choose **OAuth**.
5. Click **Create**.

!!! info

    :camera: *Screenshot to add: the dialog filled with the Open Referral URL and OAuth selected.*

## Step 4 — Authorize

ChatGPT opens an Open Referral sign-in window:

1. Sign in with your Open Referral account.
2. Review the access requested and click **Authorize**.

If the connection succeeds, ChatGPT shows the list of tools Open Referral advertises.

!!! info

    :camera: *Screenshot to add: the Open Referral consent screen, then the tool list.*

## Step 5 — Use it in a conversation

A saved connector is **not active until you enable it per chat**. In a new conversation,
turn on Open Referral (Developer Mode / tools menu), then ask:

* *"How is our referral program doing this quarter?"*
* *"What's waiting on my team right now?"*
* *"Show me recent referrals with unpaid bonuses."*
* *"What are best practices to relaunch a referral program that's losing steam?"*

## What ChatGPT can access

Open Referral exposes **7 read-only tools**. ChatGPT can read, but never modifies your data.

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
    phone numbers and direct identifiers are never sent to ChatGPT. See our
    [Privacy Policy](https://openreferral.io/privacy.html).

## Troubleshooting

* **No "Developer mode" option.** It's unavailable on Free, or your workspace admin hasn't enabled it (Team/Enterprise/Edu). Check your plan and with your admin.
* **The connector does nothing in a chat.** Connectors must be enabled **per conversation** — turn Open Referral on in the tools/Developer Mode menu first.
* **"No organisations found."** Your Open Referral account has no Admin or Recruiter role.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan.
* **The sign-in window doesn't complete.** Allow pop-ups, finish sign-in and consent, then retry.
