# Finance Hub Newsletter UI

## Reference And Status

Paths in this guide are relative to the Finance Newsletter workspace root. Use `mockups/newsletter.html` as the visual reference. It is the latest browser prototype, not an Outlook-certified email template. Its sample text and metrics are illustrative and must never become edition data by default. Keep the mockup unchanged when generating drafts under `outputs/`.

## Brand Assets

| Asset | File | Usage |
| --- | --- | --- |
| AB InBev symbol and wordmark | `ui-assets/ab-inbev-symbol-header.png`, `ui-assets/ab-inbev-wordmark-header.png` | Black masthead; symbol stays 26 px on desktop and scales with the header; wordmark is displayed 20% larger than the prior reduced size. |
| Finance Hub lockup | `ui-assets/finance-hub-new.png` | Black masthead; centered 130 x 28 px frame on desktop and 87 x 19 px on narrow layouts. |
| Command Center wordmark | `ui-assets/command-center-new-logo.png` | Black masthead; centered 150 x 28 px frame on desktop and 100 x 19 px on narrow layouts. |

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
- Use two desktop columns for distinct progress/update cards and three for adoption metrics. Use a centered two-column metric layout on tablets, then stack below 680px; check 390px and 320px viewports.
- Hero: up to 50px desktop and 30px mobile; display stack is Abadi MT Condensed Light, Abadi, Arial Narrow, Segoe UI Light, Segoe UI, sans-serif. Abadi was not found in the initial local font check; never claim it renders without verification.
- Body stack: Segoe UI, Helvetica Neue, sans-serif. Main section headings: 23px desktop / 20px mobile. Supporting copy should remain readable and secondary to the section title and key values.
- Reuse the standard gold-rule eyebrow style for section labels; use the Now Live/Upcoming heading treatment for emphasized lines in the closing panels.
- Keep newly introduced copy compact and labels legible; retain the prototype's existing brand-label tracking where useful.
- Use subtle lift/shadow transitions for interactive cards and honor `prefers-reduced-motion`.

## Fixed Versus Monthly Content

Keep logo assets, brand colors and section structure fixed. Monthly text, dates, teams, destinations and metrics come from the user's confirmed inputs.

1. Masthead and edition.
2. Hero: concise editorial opening, not a claim copied from the sample.
3. Biggest win: title, impact, contributing teams, dashboard/output link and a dashboard screenshot preview.
4. Additional progress: optional distinct wins, only when supported by inputs.
5. Now Live and Coming Next: short bullets, explicit actual/planned status, and a consistent card treatment for both.
6. Adoption Metrics: three KPI cards for users, report views and page views, with current totals and period-over-period changes.
7. Looking Ahead: biggest future priorities with outcome/timing and action if relevant.
8. Footer: confirmed Finance Hub/feedback links; no placeholder destinations in final copy.

All monthly prose must remain real HTML text, not a screenshot. In-browser `contenteditable` edits are temporary and do not save to disk; ask the user to request edits through the agent for persistent revisions.

## Adoption Metrics Cards

- Give each metric its own responsive card with a clear title, prominent current-period total, percent change and comparison period.
- Use a small, distinct line icon for each metric while keeping the trend and comparison as the primary supporting indicators.
- Keep the section on a soft cool-grey surface; use white cards with refined borders, restrained shadows, consistent gold accents and clear number-first hierarchy.
- Use green, red and neutral trend treatments for increases, decreases and unchanged results; keep the arrow and signed percentage visible so color is not the only signal.
- Compare the current period with a confirmed comparable prior period; do not invent history or targets.
- Keep current-period totals, signed growth and comparison labels visible; do not use indexed bars or shared-volume scales in the cards.
- Keep each KPI total and percentage directly editable in the browser preview; these `contenteditable` edits are temporary and do not save to disk.
- Keep CTA labels directly editable and provide a compact link-editor icon within each dashboard and feedback button. Link edits update the preview only and must be copied into the HTML before distribution.
- Let editors open the Biggest Win image picker from a subtle control overlaid on the image; local image changes are temporary browser previews and do not replace the source asset.
- Do not add illustrative sparklines unless real trend data is available.
- With zero or missing baselines, show an honest comparison status and any known totals. Do not show a fabricated percentage change.
- Regenerate values, trend indicators and comparison labels together from the source data. Editing an HTML label does not recalculate the underlying data.

## Email Delivery Boundary

The reference uses Grid/Flexbox, CSS variables, pseudo-elements and absolute positioning. Classic Outlook cannot be assumed to reproduce it. Local relative images are not delivered to recipients automatically.

Before distribution, build and test a separate table-based, inline-styled email export with appropriately packaged CID or hosted images and email-safe chart graphics/fallbacks. Verify classic/new Outlook, dark mode, image blocking, display scaling and relevant reading-pane sizes. Browser preview checks do not certify email rendering. Agent final approval is editorial only; sending is never automatic.