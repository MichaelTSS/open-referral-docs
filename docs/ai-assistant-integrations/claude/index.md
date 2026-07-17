---
description: Connect Open Referral to Claude and pilot your referral program in natural language. Two guides — pick the one that matches your Claude plan.
---

# Claude

Connect Open Referral to **Claude** (web, desktop, mobile and Cowork) as a *custom
connector*. Ask Claude about your referral program in plain language; it reads live data
from Open Referral — read-only, and privacy by design.

!!! success

    **What you get:** program metrics, monthly trends, pending team actions, recent referrals
    and best-practice playbooks — without leaving Claude.

## Prerequisites

* An **Open Referral account** on an eligible plan (**Essential** or **Scale**).
* An **Admin** or **Recruiter** role in at least one organisation.
* A **Claude account**. Custom connectors work on every plan — even **Free** (limited to one
  custom connector); **Pro, Max, Team and Enterprise** allow more.

No client ID or secret to prepare: Open Referral registers with Claude automatically
(OAuth Dynamic Client Registration). You just sign in and approve access.

!!! info

    Claude connects to Open Referral from **Anthropic's cloud**, not from your computer — so
    there's nothing to install locally.

## Which guide should I follow?

* **Individual plan (Free, Pro, Max)** — you manage your own connectors:
  follow **[For individuals (Free, Pro, Max)](individuals.md)**.
* **Team or Enterprise** — an Owner adds the connector once, then each member connects:
  follow **[For Team & Enterprise](team-enterprise.md)**.

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

!!! success

    **Privacy by design:** candidate identities are minimised to a first name + initial. Emails,
    phone numbers and direct identifiers are never sent to Claude. See our
    [Privacy Policy](https://openreferral.io/privacy.html).
