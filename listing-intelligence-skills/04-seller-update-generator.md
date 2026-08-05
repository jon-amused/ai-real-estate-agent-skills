# Skill: Seller Update Generator

## Purpose

Create a clear, reassuring, fact-based weekly seller update for each listing using listing facts, AreaPro market history, public-page facts, and showing feedback.

## Inputs

Read:

- `Listings`
- `Market History`
- `Showing Feedback`
- `Settings`

Also use the outputs of:

- Area Market Research
- Showing Feedback Summary
- Public Listing Page Review

## Voice and audience

Write directly to the seller.

Use the following `Settings` values when available:

- Agent Name
- Brokerage
- Preferred Writing Style
- Preferred Seller Update Length
- Default Signature

Default style:

- friendly
- confident
- transparent
- conversational
- free of hype

## Content rules

1. Begin with a brief personal greeting using `Seller Name`.
2. State the reporting period or date.
3. Summarize the listing's current status and verified public facts.
4. Explain relevant market movement using current and prior `Market History` rows.
5. Summarize showing feedback without naming showing agents.
6. Distinguish facts from professional interpretation.
7. Include a practical `What this means` section.
8. Include `Recommended next steps`, but do not present a price reduction as mandatory.
9. If the listing is pending or under contract, adjust the update to focus on transaction progress and market context rather than new marketing recommendations.
10. Do not include irrelevant national news.
11. Do not expose private agent-only notes unless the agent explicitly approves them.
12. Never fabricate website traffic, showing counts, or market statistics.

## Required Markdown format

# Weekly Listing Update

**Property:** [Property Address]  
**Reporting date:** [Date]  
**Current status:** [Status]  
**Current price:** [Price]  
**Days on market:** [Public DOM or clearly labeled calculated listing age]

## This Week at a Glance

Write a 2–4 sentence executive summary.

## Market Update

Explain the most important current market numbers and changes from the prior period in plain English. Avoid dumping statistics without interpretation.

## Buyer and Showing Feedback

Summarize the volume and themes of feedback. State when the sample size is limited.

## What This Means

Explain whether the listing appears to be keeping up with, gaining on, or falling behind the current market. Make clear which statements are professional interpretation.

## Recommended Next Steps

Give 1–3 practical actions. Appropriate actions may include:

- continue current strategy
- improve a presentation issue
- adjust marketing
- gather more feedback
- review pricing
- prepare for pending milestones

## Questions or Decisions

List any item the seller and agent should discuss. Omit this section when there are none.

[Default Signature]

## Source note

At the bottom, include a short internal source note listing:

- AreaPro public link
- Public listing page
- Mortgage-rate source
- Number of showing-feedback records reviewed

Label this section `Internal source note — remove before sending` unless the user asks to include sources in the client version.

## PDF behavior

- Always produce the complete seller update in Markdown first.
- If the current platform can create files, also render a clean PDF titled:
  `[Property Address] - Weekly Listing Update - [YYYY-MM-DD].pdf`
- Use simple professional formatting and page breaks only when needed.
- If the platform cannot create a PDF, state: `PDF not created in this environment; copy this Markdown into Google Docs and choose File > Download > PDF.`

## Quality check

Before finalizing:

- Reconcile price and status against the public listing page.
- Verify each market statistic against the latest research row.
- Verify feedback counts against raw feedback.
- Remove showing-agent names.
- Mark calculated DOM accurately.
- Ensure recommendations follow from the evidence.
