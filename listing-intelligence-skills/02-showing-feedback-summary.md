# Skill: Showing Feedback Summary

## Purpose

For each listing, summarize raw showing feedback into a balanced, useful seller-facing analysis without exposing showing-agent names or overstating limited evidence.

## Inputs

Read:

- `Listings`
- `Showing Feedback`

Use these `Showing Feedback` columns:

- Date
- Listing ID
- Showing Source
- Agent Name
- Home Rank (1-5)
- Buyer Interested
- Feedback Category
- Comment

## Identifier matching

The `Showing Feedback.Listing ID` field may contain either:

- the listing's `Listing ID`, or
- the listing's `MLS Number`

Match feedback using either value. Do not exclude feedback merely because the identifier format differs.

## Procedure

For each listing:

1. Gather all matching feedback.
2. Separate feedback from the current reporting period from older feedback.
3. Count:
   - total feedback responses
   - responses during the current reporting period
   - `Buyer Interested = Yes`
   - `Buyer Interested = No`
4. Calculate the average `Home Rank (1-5)` only from nonblank numeric ratings.
5. Group comments by `Feedback Category`.
6. Identify repeated themes, especially themes appearing in two or more independent comments.
7. Distinguish:
   - recurring themes
   - isolated comments
   - positive signals
   - objections or concerns
8. Preserve important nuance. For example, an investor expressing interest at a discounted price is not the same as full-price retail interest.
9. Do not identify showing agents in seller-facing output.
10. Do not recommend a price change solely from one comment.

## Output

Return these sections for each listing.

### Showing activity snapshot

Include:

- Total feedback responses
- Feedback responses this period
- Average home rank
- Interested / not interested counts

### Seller-facing feedback summary

Write 100–180 words in a calm, professional tone. Include:

- overall buyer response
- repeated positive themes
- repeated objections
- whether interest appears to be strengthening, stable, or weakening
- a clear statement when the sample size is too small for a strong conclusion

### Agent-only interpretation

Write 2–4 concise sentences identifying what deserves attention. This section is private and may be more direct than the seller-facing summary.

### Evidence table

| Theme | Category | Number of Mentions | Representative Paraphrase | Confidence |
|---|---|---:|---|---|

Use confidence values:

- High: repeated across at least 3 independent responses
- Medium: repeated across 2 responses
- Low: based on 1 response

## Quality check

Verify that:

- Both Listing ID and MLS Number were checked.
- No showing-agent names appear in seller-facing text.
- Direct quotes are not used unless the user requests them.
- Counts and averages match the raw rows.
- One unusual response is not presented as broad market consensus.
