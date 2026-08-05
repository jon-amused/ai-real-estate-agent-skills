# Skill: Area Market Research

## Purpose

For each listing, use its AreaPro public share URL to capture the current market snapshot, compare it with prior entries in `Market History`, and prepare one new row for the workbook.

## Inputs

Read these workbook tabs:

- `Listings`
- `Market History`
- `Settings`

Use these listing fields:

- Listing ID
- MLS Number
- Property Address
- City
- State
- Status
- AreaPro Public Share URL

Use these `Market History` columns exactly:

- Week Ending
- Market Name
- Inventory
- Pending Ratio
- Months Supply of Inventory
- Median Sale Price
- Median Days on Market
- Original Price to Sold Price
- Mortgage Rate
- AreaPro URL
- Notes

## When to run

Run weekly for listings whose status is `Active`, `Pending`, or `Under Contract`, unless the user specifies otherwise.

## Procedure

## Browsing method

Try in this order, and don't stop at the first failure:

1. Fetch the URL directly.
2. If the page returns mostly empty content, a JS app shell, or a loading state,
   render it with a headless browser instead: load the page, wait for network
   activity to settle (not just initial page load), then read the rendered
   text/DOM. AreaPro share links specifically require this — they load their
   numbers client-side after the initial page load.
3. Only mark AreaPro as "unreachable" and fall back to the last verified
   Market History row if both direct fetch and the rendered-page read fail.

Do not guess at or call undocumented backend/API endpoints as a workaround.
If the rendered page still doesn't expose the numbers, treat it as
unreachable and use the fallback rule below.

For each qualifying listing:

1. Open the `AreaPro Public Share URL`.
2. Identify the market represented by the page.
3. Capture the most current available values for:
   - Inventory
   - Pending Ratio
   - Months Supply of Inventory
   - Median Sale Price
   - Median Days on Market
   - Original Price to Sold Price
4. Record the reporting date shown by AreaPro. If no reporting date is displayed, use today's date and state that choice in `Notes`.
5. Search the web for the current average 30-year fixed mortgage rate. Prefer a reputable national source. Record the rate and source date.
6. Compare the new values with the most recent prior `Market History` row for the same `Market Name` or `AreaPro URL`.
7. Write a one- or two-sentence factual trend note. Mention only material changes.
8. Never overwrite a prior row. Prepare one new row for manual paste.

## Calculation and formatting rules

- Preserve percentages as percentages, not whole numbers.
- Example: 30% should be stored as `30%` or `0.30`, consistent with the workbook.
- Do not confuse months supply with absorption rate.
- Do not invent missing values.
- If a field is unavailable, leave it blank and explain why in `Notes`.
- Cite the AreaPro page and the mortgage-rate source in the research summary.

## Output

Return the following sections for each listing.

### Market research summary

- Listing: `[Listing ID] — [Property Address]`
- Market: `[Market Name]`
- As of: `[date]`
- Current snapshot: concise bullet-free paragraph
- Change from prior period: concise paragraph
- Sources: AreaPro URL and mortgage-rate source

### Row to paste into `Market History`

Return a Markdown table with columns in the exact workbook order:

| Week Ending | Market Name | Inventory | Pending Ratio | Months Supply of Inventory | Median Sale Price | Median Days on Market | Original Price to Sold Price | Mortgage Rate | AreaPro URL | Notes |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|---|

## Quality check

Before finishing, verify:

- The values came from the correct AreaPro link.
- The mortgage rate is current and dated.
- The market row does not duplicate an existing row for the same reporting date.
- Every comparison uses the same market and metric definitions.
