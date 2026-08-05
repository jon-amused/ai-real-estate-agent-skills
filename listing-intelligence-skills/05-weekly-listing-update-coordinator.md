# Skill: Weekly Listing Update Coordinator

## Purpose

Run the complete weekly listing intelligence workflow for all qualifying listings by coordinating the four supporting skills.

## Supporting skills

Run these in order:

1. `01-area-market-research.md`
2. `02-showing-feedback-summary.md`
3. `03-public-listing-page-review.md`
4. `04-seller-update-generator.md`

## Default command

When the user says any equivalent of:

> Run the weekly listing updates.

perform this workflow for every listing with status:

- Active
- Pending
- Under Contract

Do not run Sold, Withdrawn, or Cancelled listings unless requested.

## Operating rules

- Read the workbook before starting.
- Process one listing at a time.
- Match showing feedback using either `Listing ID` or `MLS Number`.
- Use public URLs from the workbook; do not search for substitute listing pages unless the stored URL fails.
- Browse current sources where required.
- Never invent missing data.
- Do not overwrite workbook history.
- Unless a connected Google Sheets tool with write permission is available, return rows for manual paste.
- Do not send emails or contact sellers.
- Stop with drafts ready for agent review.

## Workflow

### Step 1 — Validate inputs

For each qualifying listing, confirm the presence of:

- Property Address
- Seller Name
- Status
- AreaPro Public Share URL
- Listing Website URL

If a required URL is missing or inaccessible, continue with the remaining data and record the issue.

### Step 2 — Run Area Market Research

Capture the current market snapshot, mortgage rate, trend comparison, and proposed `Market History` row.

When multiple listings use the same AreaPro URL and market, research that market once and reuse the same verified snapshot. Do not create duplicate `Market History` rows for the same market, AreaPro URL, and reporting date.

### Step 3 — Run Showing Feedback Summary

Summarize all matching showing feedback, emphasizing the current reporting period and repeated themes.

### Step 4 — Run Public Listing Page Review

Capture current public facts and identify verified discrepancies from the `Listings` tab.

### Step 5 — Generate Seller Update

Create the seller-facing Markdown update. Create a PDF too only when file generation is supported.

### Step 6 — Produce a review package

Return all results grouped by listing.

## Final output format

# Weekly Listing Update Run

**Run date:** [date]  
**Listings processed:** [count]  
**Markets researched:** [count]  
**Drafts created:** [count]  
**Listings skipped:** [count]

## Workbook Updates to Paste

### Market History rows

Return one combined Markdown table using the exact workbook columns:

| Week Ending | Market Name | Inventory | Pending Ratio | Months Supply of Inventory | Median Sale Price | Median Days on Market | Original Price to Sold Price | Mortgage Rate | AreaPro URL | Notes |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|

### Verified Listings corrections

| Listing ID | Field | Existing Value | Verified Value | Source |
|---|---|---|---|---|

Do not include unverified or inferred changes.

## Listing Review Packages

For each listing, include:

### [Listing ID] — [Property Address]

**Workflow status:** Complete / Partial / Skipped  
**Issues:** None or concise explanation

#### Market findings

Concise research summary.

#### Showing feedback findings

Concise seller-facing summary followed by agent-only interpretation.

#### Public listing findings

Current price, status, DOM or calculated age, and discrepancies.

#### Seller update draft

Insert the complete Markdown seller update.

#### Files

List the PDF filename/link if generated. Otherwise provide the Google Docs export instruction.

## Exceptions and failure handling

- If AreaPro cannot be opened after both a direct fetch and a rendered-page read, do not guess market values.
- If the public listing page cannot be opened, use workbook facts and label DOM as unavailable or calculated listing age.
- If no showing feedback exists, say so plainly and do not imply buyer sentiment.
- If multiple values conflict, present the conflict for agent review.
- Continue processing other listings when one listing fails.

## Final agent checklist

End with a short checklist:

- Review each draft for tone and accuracy.
- Approve any workbook corrections.
- Paste new Market History rows.
- Remove internal source notes.
- Copy the approved update into Google Docs.
- Export PDF.
- Send manually.

## Quality check

Before completing the run:

- Confirm each active listing was processed or explicitly skipped.
- Confirm shared markets were researched only once.
- Confirm no duplicate market-history rows were proposed.
- Confirm all seller drafts use the correct seller, address, price, and status.
- Confirm nothing was sent automatically.
