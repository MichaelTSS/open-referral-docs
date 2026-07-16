---
description: Connect Open Referral to Claude as a custom connector and pilot your referral program in natural language.
---

# Claude

Connect Open Referral to **Claude** (web, desktop, mobile and Cowork) as a *custom
connector*. Once connected, you can ask Claude about your referral program in plain
language and it will read live data from Open Referral — read-only, and privacy by design.

{% hint style="success" %}
**What you get:** program metrics, monthly trends, pending team actions, recent referrals
and best-practice playbooks — without leaving Claude.
{% endhint %}

## Prerequisites

Before you start, make sure you have:

* An **Open Referral account** on an eligible plan (**Essential** or **Scale**).
* An **Admin** or **Recruiter** role in at least one organisation.
* A **Claude account**. Custom connectors are available on Free (1 connector), Pro, Max,
  Team and Enterprise. On **Team/Enterprise**, an Owner must add the connector first (see below).

No client ID or secret to prepare: Open Referral registers with Claude automatically
(OAuth Dynamic Client Registration). You only sign in and approve access.

{% hint style="info" %}
Claude connects to Open Referral from **Anthropic's cloud**, not from your computer — so
there's nothing to install locally. Our server (`https://mcp.openreferral.io`) is publicly
reachable, which is all Claude needs.
{% endhint %}

## Step 1 — Open the Connectors settings

**On Pro or Max (individual):** go to **Customize → Connectors**.

**On Team or Enterprise:** an **Owner** goes to **Settings → Organization settings →
Connectors**. (Members: skip to [Step 4](#step-4-connect-your-account-team-enterprise).)

{% hint style="info" %}
📸 *Screenshot to add: the Connectors settings page.*
{% endhint %}
<!-- ![Connectors settings](../.gitbook/assets/claude-01-connectors.png) -->

## Step 2 — Add a custom connector

* **Pro / Max:** click **+** → **Add custom connector**.
* **Team / Enterprise (Owner):** click **Add → Custom → Web**.

{% hint style="info" %}
📸 *Screenshot to add: the "Add custom connector" dialog.*
{% endhint %}
<!-- ![Add custom connector](../.gitbook/assets/claude-02-add-connector.png) -->

## Step 3 — Enter the Open Referral server URL

1. **Name:** `Open Referral`
2. **Remote MCP server URL:** `https://mcp.openreferral.io`
3. Leave **Advanced settings** empty — no OAuth Client ID or Secret is required.
4. Click **Add**.

{% hint style="info" %}
📸 *Screenshot to add: the dialog filled with the Open Referral URL.*
{% endhint %}
<!-- ![Enter server URL](../.gitbook/assets/claude-03-url.png) -->

## Step 4 — Connect your account

Click **Connect** on the Open Referral connector. Claude opens an Open Referral sign-in
window:

1. Sign in with your Open Referral account.
2. On the consent screen, review the access requested and click **Authorize**.

The connector now shows as **Connected**.

{% hint style="info" %}
📸 *Screenshot to add: the Open Referral OAuth consent screen.*
{% endhint %}
<!-- ![Authorize](../.gitbook/assets/claude-04-consent.png) -->

{% hint style="warning" %}
**Team/Enterprise members:** once your Owner has added the connector (Steps 1–3), you
connect your own account here via **Customize → Connectors → Connect**.
{% endhint %}

## Step 5 — Use it in a conversation

In a new chat, make sure the Open Referral connector is enabled (via the connector/tools
menu), then ask a question. Claude calls the relevant read-only tool and answers.

Try:

* *"How is our referral program doing this quarter?"*
* *"What's waiting on my team right now?"*
* *"Show me recent referrals with unpaid bonuses."*
* *"What are best practices to relaunch a referral program that's losing steam?"*

{% hint style="info" %}
📸 *Screenshot to add: Claude answering a program-overview prompt.*
{% endhint %}
<!-- ![Example answer](../.gitbook/assets/claude-05-answer.png) -->

## What Claude can access

Open Referral exposes **7 read-only tools**. Claude can read, but never modifies your data.

| Tool | What it returns |
| --- | --- |
| List My Organisations | Organisations where you are Admin or Recruiter |
| Get Program Overview | Total referrals, pipeline, hires, bonuses paid |
| Get Referral Trend | Monthly referral trends |
| List Pending Actions | Items awaiting your team |
| List Recent Referrals | Latest referrals (candidate names minimised) |
| List Knowledge Entries | Best-practice playbooks available |
| Get Knowledge Entry | Full text of a specific playbook |

{% hint style="success" %}
**Privacy by design:** candidate identities are minimised to a first name + initial. Emails,
phone numbers and direct identifiers are never sent to Claude. See our
[Privacy Policy](https://openreferral.io/privacy.html).
{% endhint %}

## Troubleshooting

* **"No organisations found."** Your account has no Admin or Recruiter role. Ask an admin to grant one.
* **"Copilot not available on your plan."** The connector requires an **Essential** or **Scale** Open Referral plan. Contact your organisation administrator.
* **The sign-in window doesn't complete.** Allow pop-ups, finish the sign-in and consent steps, then retry **Connect** from the Connectors settings.
* **"Add custom connector" is missing.** On Team/Enterprise, only an Owner can add connectors. Ask your Owner to complete Steps 1–3, then connect your account.
