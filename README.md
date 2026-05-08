# ConnectHub Triage — Claude Code Skill

![Version](https://img.shields.io/badge/version-1.2.0-blue)
![Platform](https://img.shields.io/badge/platform-Claude%20Code-blueviolet)
![License](https://img.shields.io/badge/license-MIT-green)
![Category](https://img.shields.io/badge/category-Customer%20Support-orange)

Instantly triage ConnectHub customer complaints. Paste a raw complaint — get a structured urgency tier, complaint category, routing team, governing rules, compliance flags, and a ready-to-send response draft in seconds.

---

## Overview

ConnectHub Triage is a Claude Code skill built for support agents. It turns unstructured customer complaint text into a complete, actionable triage output without the agent having to manually classify, route, or draft a response from scratch.

The skill applies a strict 6-step framework on every complaint:

| Step | What it does |
|------|-------------|
| 1 | Detects Layer 1 intent — Cancel/Churn, Escalation, or Get Help |
| 2 | Classifies into one of 5 complaint categories with subtypes |
| 3 | Assigns urgency tier — Critical, Standard, or Low |
| 4 | Reads emotional tone level (1–5) to shape the response style |
| 5 | Applies 6 governing rules and states which fired and why |
| 6 | Handles thin/vague tickets with a structured clarification prompt |

---

## Output

Every triage run produces this exact structure:

```
════════════════════════════════════════
CONNECTHUB TRIAGE OUTPUT
════════════════════════════════════════

URGENCY TIER      : CRITICAL
COMPLAINT CATEGORY: Fraud & Security — SIM Swap Fraud
TONE LEVEL        : 3 — Clearly Angry
ROUTING TEAM      : Security / Fraud Team
                    Retention Team (parallel)

RULES TRIGGERED:
→ Fraud Is Always Critical — Category 4 signal detected; tier is automatic
→ Retention Always Wins    — Churn signal present; Retention notified in parallel

RECOMMENDED ACTION:
Escalate to Security / Fraud Team immediately. Notify Retention in parallel.
Do not make account changes until Security confirms identity.

SPECIAL FLAGS:
COMMITMENT FLAG — Response draft does not confirm any refund or credit.
Agent must confirm with Billing before sending any compensation language.

RESPONSE DRAFT:
Subject: Urgent: Your Account Security — We're Acting Now

[Full ready-to-send agent response]

════════════════════════════════════════
```

---

## Complaint Categories

| # | Category | Routes To |
|---|----------|-----------|
| 1 | Network & Connectivity | Network Operations / Field Engineers |
| 2 | Billing & Charges | Billing / Finance Team |
| 3 | Service Delivery | Provisioning / Scheduling Team |
| 4 | Fraud & Security | Security / Fraud Team — always Critical |
| 5 | Service Quality & Experience | QA / Customer Experience Team |

---

## Urgency Tiers

| Tier | When it applies |
|------|----------------|
| **Critical** | Fraud, total outage, churn intent, billing error >RM200 on 2+ bills, legal/regulatory threat, refund pending >15 working days |
| **Standard** | Billing errors below threshold, speed issues, broken promises, installation delays within SLA |
| **Low** | Appointment confirmations, minor informational queries, no active service failure |

> Urgency is determined by the nature of the issue — never by the customer's tone.

---

## Scope

**The skill will:**
- Classify complaints and assign urgency tiers
- Detect customer intent and route to the correct team
- Flag compliance, fraud, and regulatory risks
- Generate a response draft for agent review

**The skill will not:**
- Approve or confirm refunds, credits, or compensation
- Make account changes or plan adjustments
- Access, verify, or retrieve live account data
- Send responses — every draft requires agent review before sending
- Handle general product FAQs, sales requests, or upgrade questions
- Process complaints in languages other than English

> This skill assists agents — it does not replace agent judgment. Every triage output must be reviewed before action is taken.

---

## Installation

**Via Claude Code plugin system:**

```bash
/plugin install gh:rashadulnafisriyad/connecthub-triage
```

**Or clone and install locally:**

```bash
git clone https://github.com/RashadulRD786/AI-powered-Triage-Response-system-.git
/plugin install ./connecthub-triage
```

---

## Usage

Once the skill is installed, paste a raw customer complaint into your Claude Code session. The skill activates automatically when it detects a customer complaint or support ticket.

**Example trigger:**

```
My internet has been completely down for 3 days. 
I called twice and nobody fixed it. I'm switching to another provider.
```

**The skill will:**
1. Detect churn intent → route to Retention
2. Classify as Category 1, Total Outage → Critical tier
3. Apply Dual Classification if needed
4. Produce a full triage output with response draft

---

## Repository Structure

```
connecthub-triage/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
└── skills/
    └── connecthub-triage/
        └── SKILL.md         # Skill instructions and framework
```

---

## Requirements

- Claude Code (latest version)
- Agent access to Claude.ai or Claude Code environment

---

## Author

**Rashadul NafiS Riyad**
Built for the Teleperformance Claude Skills Assessment.

---

## License

MIT — see [LICENSE](LICENSE) for details.
