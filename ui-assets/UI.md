# Finance Hub Newsletter UI

## Reference And Status

Paths in this guide are relative to the Finance Newsletter workspace root. Use `mockups/newsletter.html` as the authoritative visual and preview-control reference. It is the latest browser prototype, not an Outlook-certified email template. Its sample text, metrics and dashboard image are illustrative and must never become edition data by default. Keep the mockup unchanged when generating drafts under `outputs/`.

## Brand Assets

| Asset | File | Usage |
| --- | --- | --- |
| AB InBev symbol and wordmark | `ui-assets/ab-inbev-symbol-header.png`, `ui-assets/ab-inbev-wordmark-header.png` | Black masthead; symbol stays 26 px on desktop and scales with the header; wordmark is displayed 20% larger than the prior reduced size. |
| Finance Hub lockup | `ui-assets/finance-hub-new.png` | Black masthead; centered 130 x 28 px frame on desktop and 87 x 19 px on narrow layouts. |
| Command Center wordmark | `ui-assets/command-center-new-logo.png` | Black masthead; centered 150 x 28 px frame on desktop and 100 x 19 px on narrow layouts. |
| Footer megaphone illustration | `ui-assets/footer-megaphone.svg` | Reusable decorative footer artwork; the newsletter mockup references this shared asset. |

The AB InBev and Finance Hub lockups stay together near the left edge; Command Center remains on the right. Header frames compensate for internal whitespace, and images use `object-fit: contain` without stretching. The original AB InBev asset remains unchanged; its header-specific symbol and wordmark crops omit the lower tagline, while keeping the symbol its previous size and reducing only the wordmark.

## Color Tokens

These are the prototype's chosen colors, not certified corporate brand specifications.

| Token | Hex | Role |
| --- | --- | --- |
| Ink | `#080808` | Masthead, hero, and primary typography |
| Gold | `#D7B91B` | Brand accents and emphasis |
| Warm white | `#FCFAF0` | Featured content surfaces |
| Muted text | `#62666C` | Secondary body text |
| Divider | `#E1E6EC` | Borders and separators |
| Updates band | `#F3F5F8` | Live/upcoming cards |

## Layout And Typography

- Fluid dashboard-style newsletter width, capped at 1180px. Do not promise that this fits every Outlook reading pane.
- Use a warm-white canvas, light grey page background, black primary typography, refined gold accents, restrained borders and soft shadows. Keep the hero and masthead black for brand contrast.
- Use two desktop columns for the update cards and three for adoption metrics. Use a centered two-column metric layout on tablets, then stack below 680px; check 390px and 320px viewports.
- Hero: up to 50px desktop and 30px mobile; display stack is Abadi MT Condensed Light, Abadi, Arial Narrow, Segoe UI Light, Segoe UI, sans-serif. Abadi was not found in the initial local font check; never claim it renders without verification.
- Body stack: Segoe UI, Helvetica Neue, sans-serif. Main section headings: 23px desktop / 20px mobile. Supporting copy should remain readable and secondary to the section title and key values.
- Reuse the standard gold-rule eyebrow style for section labels; use the Now Live/Upcoming heading treatment for emphasized lines in the closing panels.
- Keep newly introduced copy compact and labels legible; retain the prototype's existing brand-label tracking where useful.
- Use subtle lift/shadow transitions for interactive cards and honor `prefers-reduced-motion`.

## Fixed Versus Monthly Content

Keep logo assets, brand colors and section structure fixed. Monthly text, dates, teams, destinations and metrics come from the user's confirmed inputs.

1. Masthead and hero: edition and concise editorial opening, not a claim copied from the sample.
2. Biggest win: title, impact, contributing teams, dashboard button and relevant dashboard image.
3. Now Live and Upcoming: short bullets, explicit actual/planned status, and a consistent card treatment for both.
4. Adoption Metrics: three KPI cards for users, report views and page views, with current totals and changes from a confirmed Go Live baseline.
5. Looking Ahead: biggest future priorities with outcome/timing and action if relevant.
6. Share Feedback: feedback copy and button.
7. Footer: closing message in the mockup's established treatment.

All monthly prose must remain real HTML text, not a screenshot. Do not add old featured-KPI or additional-progress panels. Ask for a relevant image; use an explicit placeholder in a partial draft if it is missing and resolve it before finalization.

## Adoption Metrics Cards

- Give each metric its own responsive card with a clear title, prominent current total, percent change or honest status, and Go Live comparison label.
- Use a small, distinct line icon for each metric while keeping the trend and comparison as the primary supporting indicators.
- Keep the section on a soft cool-grey surface; use white cards with refined borders, restrained shadows, consistent gold accents and clear number-first hierarchy.
- Use green, red and neutral trend treatments for increases, decreases and unchanged results; use an appropriate directional indicator and signed percentage or explicit direction so color is not the only signal. Undefined comparisons use a neutral status without a fabricated percentage or directional arrow.
- Compare the current period with a confirmed comparable Go Live baseline; verify definitions, scope and reporting windows or snapshot dates. Do not invent history or targets.
- Keep current totals, signed growth or an honest status, and comparison labels visible; do not add indexed bars, shared-volume scales or sparklines.
- With zero or missing baselines, show an honest comparison status and any known totals. Do not show a fabricated percentage change.
- Regenerate values, trend indicators and comparison labels together from the source data. Editing an HTML label does not recalculate the underlying data.

## Preview Controls

- Keep the mockup's editable text, KPI totals and percentages, CTA labels, dashboard and feedback link editors, and Biggest Win image picker.
- These browser changes are temporary: they do not save to disk or update the JSON or calculations. Ask the user to provide the edits, link destinations and actual image file to the agent for a new saved revision.
- Preserve the trusted template script and its required controls and selectors. Never use a sample dashboard image as the edition image without confirmation.

## Email Delivery Boundary

The reference uses Grid/Flexbox, CSS variables, pseudo-elements and absolute positioning. Classic Outlook cannot be assumed to reproduce it. Local relative images are not delivered to recipients automatically.

Before distribution, build and test a separate table-based, inline-styled email export with appropriately packaged CID or hosted images and email-safe KPI presentation/fallbacks. Verify classic/new Outlook, dark mode, image blocking, display scaling and relevant reading-pane sizes. Browser preview checks do not certify email rendering. Agent final approval is editorial only; sending is never automatic.