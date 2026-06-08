# n8n Lead Capture & Follow-up Automation

An AI-powered lead automation system built with n8n and OpenAI that captures inbound leads, scores them automatically, sends personalized AI-written replies, and follows up with cold leads — all without any manual work.

## Demo

> 📺 [Watch the demo video](https://www.linkedin.com/posts/dzakies_n8n-automation-aiautomation-ugcPost-7467088712825475072-wD-K/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAEkGSHQBQ8_SUmtEy8OMzAQ6je8LEhFimDU)

---

## The Problem It Solves

Most small businesses lose leads simply because nobody replies fast enough. The average response time for a small business to a new lead is over 17 hours. The ideal response time to maximize conversion is under 5 minutes. This system closes that gap completely.

---

## What It Does

```
Candidate fills form
       ↓
Lead scored 1–10 (urgency, budget, source signals)
       ↓
AI writes a personalized reply email (OpenAI GPT-4o-mini)
       ↓
Lead saved to Google Sheets CRM with score + timestamp
       ↓
Hot leads (score 5+) → instant Telegram alert to team
       ↓
No reply after 24 hours → automatic follow-up email sent
       ↓
Status updated → no duplicate emails ever sent
```

---

## Features

- **Automatic lead scoring** — each lead scored 1–10 based on urgency keywords, budget mentions, and traffic source
- **AI-personalized replies** — OpenAI reads the lead's message and writes a unique response for each person, not a template
- **Google Sheets CRM** — every lead saved with name, email, phone, message, source, score, status, and timestamp
- **Hot lead alerts** — Telegram notification fires instantly when score is 5 or above
- **24-hour follow-up** — scheduled workflow checks for unresponded leads daily and sends a follow-up automatically
- **Status tracking** — leads move from `new` → `followed up` automatically, preventing duplicate outreach

---

## Tech Stack

| Tool | Purpose |
|---|---|
| n8n | Workflow automation engine |
| OpenAI GPT-4o-mini | AI-personalized email generation |
| Gmail | Sending automated emails |
| Google Sheets | CRM / lead database |
| Telegram Bot API | Hot lead notifications |
| JavaScript | Lead scoring logic |

---

## Workflows

| File | Description |
|---|---|
| `lead-capture.json` | Main workflow — form → score → AI email → Sheets → Telegram |
| `lead-followup.json` | Scheduled follow-up — runs daily at 9am, emails cold leads |

---

## How to Use

1. Import both JSON files into your n8n instance
2. Connect your credentials: Gmail, Google Sheets, OpenAI, Telegram Bot
3. Update the Google Sheets node to point to your spreadsheet
4. Update the Telegram Chat ID to your group or personal chat
5. Activate both workflows
6. Share the form URL with your audience

---

## Lead Scoring Logic

```javascript
let score = 1; // base score

if (message.includes("urgent"))     score += 3;
if (message.includes("budget"))     score += 2;
if (message.includes("asap"))       score += 3;
if (message.includes("this week"))  score += 1;
if (source === "referral")          score += 2;
if (source === "instagram")         score += 1;
```

Scores 1–2 = cold lead, reply when available
Scores 3–4 = warm lead, reply today
Scores 5+  = hot lead, instant Telegram alert

---

## Results

- ✅ Response time reduced from hours to under 10 seconds
- ✅ Zero leads fall through the cracks
- ✅ Every lead gets a unique, personalized reply
- ✅ Runs 24/7 including weekends
- ✅ Near-zero operating cost (self-hostable)

---

## Author

**Dzaki Endraghani Sunarko**
AI Automation Specialist | n8n & OpenAI Workflow Developer

- LinkedIn: [linkedin.com/in/dzakies](https://linkedin.com/in/dzakies)
- GitHub: [github.com/DzakiES](https://github.com/DzakiES)
- Email: dzakies2003@gmail.com

---

> Built as a portfolio project demonstrating production-ready AI workflow automation.
