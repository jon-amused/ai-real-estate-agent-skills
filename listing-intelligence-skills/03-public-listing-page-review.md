# Skill: Public Listing Page Review

## Purpose

For each listing, inspect its public listing page and capture current public-facing facts such as price, status, days on market, property details, and marketing presentation.

## Inputs

Read the `Listings` tab, especially:

- Listing ID
- MLS Number
- Property Address
- City
- State
- ZIP
- Listing Date
- Original List Price
- Current List Price
- Status
- Listing Website URL
- Notes

## Procedure

For each listing:

1. Open the `Listing Website URL`.
2. Confirm that the page represents the correct property by checking the address and MLS number when available.
3. Capture public facts when displayed:
   - current price
   - listing status
   - days on market
   - bedrooms
   - bathrooms
   - square footage
   - lot size
   - year built
   - property type
   - price per square foot
   - open-house information
   - public remarks or description
4. Note any visible price reduction, status change, or open house.
5. Compare current public values to the corresponding values in `Listings`.
6. Flag discrepancies. Do not silently replace workbook values.
7. Briefly assess the public presentation:
   - Is the listing page available?
   - Are photos present?
   - Is the description complete?
   - Are obvious stale details visible?
8. Do not infer facts that are not displayed.

## Days-on-market rule

Prefer the DOM shown on the public page. If DOM is not shown, calculate calendar days from `Listing Date` to today and label it `Calculated listing age`, not official DOM.

## Output

Return these sections for each listing.

### Current public listing snapshot

| Field | Current Public Value | Workbook Value | Status |
|---|---|---|---|
| Price | | | Match / Different / Not available |
| Listing Status | | | Match / Different / Not available |
| Days on Market | | | Public / Calculated / Not available |
| Bedrooms | | | |
| Bathrooms | | | |
| Square Feet | | | |
| Lot Size | | | |
| Year Built | | | |
| Property Type | | | |
| Price per Square Foot | | | |
| Open House | | | |

### Public-page observations

Write 3–6 concise sentences describing meaningful changes, discrepancies, or presentation issues.

### Recommended workbook corrections

List only verified discrepancies. Use:

- `Field`: existing value → verified public value

If there are no verified discrepancies, state: `No verified workbook corrections.`

### Source

Include the public listing URL and access date.

## Quality check

Verify:

- The address matches the intended listing.
- Public values are clearly distinguished from calculated or inferred values.
- No workbook field is treated as updated until the agent approves it.
