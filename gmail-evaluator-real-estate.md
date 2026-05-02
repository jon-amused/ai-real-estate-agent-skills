---
name: gmail-inbox-evaluator
description: Evaluate Gmail inbox using multiple agentic lenses to surface follow-ups, leads, urgency, noise, and client experience gaps. Use this skill whenever the user asks to evaluate their inbox, review email, do inbox triage, find follow-ups, find leads in email, identify what to respond to, prioritize emails, or summarize their inbox — even if they don't use those exact words.
---

# 🧠 Gmail Inbox Evaluator (Real Estate Agent)

## 🎯 Purpose
Evaluate my Gmail inbox using multiple focused “agentic lenses” to surface:
- missed follow-ups  
- active opportunities  
- urgency  
- noise  
- client experience gaps  

---

# 🚦 Execution Rules

When this skill is triggered:

1. Default to analyzing:
   - Inbox (last 3 days)
   - Sent mail (last 7 days for follow-ups)

2. If the user specifies a timeframe, override defaults.

3. Run evaluators in this order:
   1. Human vs System Filter (reduce noise first)
   2. Follow-Up Gap Evaluator
   3. Active Lead Detection
   4. Urgency Evaluator
   5. Client Experience Evaluator

4. Prioritize:
   - High-value conversations (clients, leads, deals)
   - Actionable outputs over summaries

5. Keep output:
   - Structured
   - Concise
   - Skimmable

---

# 🔁 1. Follow-Up Gap Evaluator

## Objective
Identify conversations where I am waiting on a response and the thread may have stalled.

## Instructions
Search sent emails from the last 7 days.

### Include:
- I sent the last message  
- No reply for 3+ days  

### Exclude:
- Approval messages (“approved”, “looks good”)  
- Acknowledgements (“thanks”, “got it”)  
- Closed loops (“we’re all set”)  
- Purely informational messages  

### Only include:
- Threads where I’m waiting on a response or action  
- Conversations with implied next steps  
- Threads that appear stalled  

## Output
- Recipient  
- Subject  
- Last message date  
- What I’m waiting on  
- Urgency (low / medium / high)  
- Tone (gentle / nudge / direct)  

Then draft a follow-up and save it directly as a Gmail draft using the Gmail create_draft tool. Do NOT display the draft text on screen — just confirm it was saved with the recipient's name and subject line.

---

# 🏡 2. Active Lead Detection

## Objective
Identify real estate opportunities.

## Instructions
Scan inbox (last 3 days).

### Detect:
- Buying / selling intent  
- Showing requests  
- Pricing discussions  
- Relocation  

### Classify:
- New Lead  
- Active Client  
- Vendor  
- Noise  

## Output
- Classification  
- Urgency signals  
- Timeline  
- Financing indicators  

Then save response drafts directly to Gmail using the Gmail create_draft tool for any leads identified. Do NOT display draft text on screen — just confirm each draft was saved with the recipient and subject.

---

# ⏳ 3. Urgency Evaluator

## Objective
Surface time-sensitive emails.

## Instructions
Scan inbox (last 48 hours).

### Identify:
- Deadlines  
- Time-sensitive decisions  
- Dates within 3 days  

## Output
Rank:
1. Must act today  
2. Should act soon  
3. Informational  

Include reason for urgency.

---

# 🧾 4. Human vs System Filter

## Objective
Remove noise.

## Instructions
Separate:
- Human emails  
- System emails  

## Output

###