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

## Browsing method — AreaPro links (read this before opening any AreaPro URL)

AreaPro share links (`app.areapro.com/s/...`) are JavaScript apps. The market
numbers are not present in the initial HTML — they load client-side after
the page mounts. A plain HTTP fetch (curl, `requests`, a fetch tool that
only reads raw response bodies) will return an empty app shell with no
numbers in it. **Do not treat that empty shell as "AreaPro is unreachable."**
It means the page needs to render first.

Default procedure for every AreaPro URL:

1. Open the URL in a headless browser (e.g. Playwright with Chromium).
2. Wait for network activity to settle — use a "networkidle" wait condition
   (or equivalent), not just initial page load. Add a short fixed delay
   (2-3 seconds) after that as a safety margin, since some client-side data
   fetches complete just after the network-idle signal fires.
3. Read the numbers from the rendered page. Prefer taking a full-page
   screenshot and reading the values visually in addition to extracting
   text — the flattened text of a card-based dashboard layout can put
   adjacent numbers in a confusing order (e.g. multiple percentage labels
   stacked together), and the screenshot resolves that ambiguity.
4. Only if the rendered page still shows no data after step 2-3 (e.g. an
   error state, a login wall, or the numbers genuinely blank) should you
   treat AreaPro as unreachable for this run and fall back to the last
   verified `Market History` row, per the Exceptions rule below.

Do not guess at or call undocumented backend/API endpoints as a shortcut —
this includes URLs referenced in page metadata (og:image, share IDs, etc.)
that look like they might expose an API. Rendering the page is the correct
and sufficient method; probing for hidden endpoints is not.

**Environment note:** this rendering step requires a tool environment with
code execution and a headless browser available (this is the case in
Claude's code environment; ChatGPT Projects and Gemini Gems do not
currently support this, so in those environments AreaPro links should be
treated as unreachable and the fallback rule applies immediately).

## Procedure

For each qualifying listing:

1. Open the `AreaPro Public Share URL` using the browsing method above.
2. Identify the market represented by the page.
3. Capture the most current available values for:
   - Inventory
   - Pending Ratio
   - Months Supply of Inventory
   - Median Sale Price
   - Median Days on Market
   - Original Price to Sold Price
4. Record the reporting date shown by AreaPro (usually in the page footer, e.g. "Market data as of [date]"). If no reporting date is displayed, use today's date and state that choice in `Notes`.
5. Search the web for the current average 30-year fixed mortgage rate. Prefer a reputable national source. Record the rate and source date.
6. Compare the new values with the most recent prior `Market History` row for the same `Market Name` or `AreaPro URL`.
7. Write a one- or two-sentence factual trend note. Mention only material changes.
8. Never overwrite a prior row. Prepare one new row for manual paste.

## Calculation and formatting rules

- Preserve percentages as percentages, not whole numbers.
- Example: 30% should be stored as `30%` or `0.30`, consistent with the workbook.
- Do not confuse months supply with absorption rate — AreaPro shows both side by side; Months Supply of Inventory and Absorption Rate are different metrics, only Months Supply of Inventory goes in the workbook.
- "Median Days on Market" maps to AreaPro's "DoM (Sold)" figure, not "DoM (Active)" — the workbook has consistently tracked the sold-side DOM.
- "Original Price to Sold Price" maps to the ratio spanning Original List Price → Sold Price (the outer bracket on AreaPro's Median Prices card), not the Original List Price → Final List Price or Final List Price → Sold Price sub-brackets.
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

- AreaPro was rendered (not just fetched raw) before being marked unreachable.
- The values came from the correct AreaPro link.
- Median Days on Market and Original Price to Sold Price were read from the correct AreaPro fields, not adjacent lookalike figures.
- The mortgage rate is current and dated.
- The market row does not duplicate an existing row for the same reporting date.
- Every comparison uses the same market and metric definitions.
