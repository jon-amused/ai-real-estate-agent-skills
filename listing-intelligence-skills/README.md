# Listing Intelligence Skills — Quick Start

These five Markdown skills are designed for ChatGPT Projects, Claude Projects, Gemini Gems, or another AI workspace that can read uploaded files and browse public webpages.

## Required project files

Upload:

1. Your `Listing Intelligence Tracker.xlsx`
2. All five `.md` skill files in this folder

## Weekly workflow

Run this instruction:

> Run the Weekly Listing Update Coordinator for all active listings. Stop before sending anything and give me the completed seller updates for review.

The coordinator will:

1. Read the `Listings`, `Market History`, `Showing Feedback`, and `Settings` tabs.
2. Inspect each listing's AreaPro public link.
3. Inspect each listing's public listing page.
4. Summarize showing feedback.
5. Draft a seller update in Markdown.
6. Produce suggested spreadsheet rows for the agent to paste into the workbook.

## Important limitation

Uploading an Excel or Google Sheet usually gives the AI read access, not permission to modify the original Google Sheet. Unless the platform has an enabled Google Drive/Sheets connector with write access, the skills should return a clearly labeled row or table for manual paste.

## Identifier rule

The workbook may use either:

- `Listing ID`, such as `LST-26-1`
- `MLS Number`, such as `SRMLS-2187565`

When matching Showing Feedback to a listing, the AI must try both values.

## Recommended live-teaching sequence

1. Run `01-area-market-research.md` for one listing.
2. Run `02-showing-feedback-summary.md` for the same listing.
3. Run `03-public-listing-page-review.md`.
4. Run `04-seller-update-generator.md`.
5. Show that `05-weekly-listing-update-coordinator.md` combines the first four.
