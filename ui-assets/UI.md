# Finance Hub Newsletter UI

## Reference And Status

Paths in this guide are relative to the Finance Newsletter workspace root. Use `mockups/newsletter.html` as the visual reference. It is the latest browser prototype, not an Outlook-certified email template. Its sample text and metrics are illustrative and must never become edition data by default. Keep the mockup unchanged when generating drafts under `outputs/`.

## Brand Assets

| Asset | File | Usage |
| --- | --- | --- |
| AB InBev gold symbol | `ui-assets/ab-inbev-symbol-gold.png` | Black masthead, 28px square on desktop, 23px on narrow layouts; preserve aspect ratio. |
| Command Center wordmark | `ui-assets/command-center-logo-yellow-white-2line.png` | Black masthead, 138px wide on desktop, 112px on narrow layouts; preserve aspect ratio. |

Finance Hub and AB InBev wording beside the symbol are text, not an extracted combined logo. Use supplied assets without recoloring, cropping or reconstructing the marks.

## Color Tokens

These are the prototype's chosen colors, not certified corporate brand specifications.

| Token | Hex | Role |
| --- | --- | --- |
| Ink | `#080808` | Masthead, hero and adoption band |
| Yellow | `#F5DF00` | Key accents, current-period chart bars |
| White | `#FFFFFF` | Main canvas, light text, prior-period markers |
| Pale yellow | `#FFFBEA` | Featured win background |
| Muted text | `#626262` | Secondary body text |
| Divider | `#DEDBD0` | Separators |
| Chart track | `#343434` | Indexed comparison background |
| Updates band | `#F4F3EE` | Live/upcoming updates |

## Layout And Typography

- Fluid newsletter width, capped at 820px. Do not promise that this fits every Outlook reading pane.
- Preserve the compact email-like hierarchy; use two/three desktop columns only where the reference does. Stack below 680px and check a 390px viewport.
- Hero: 36px desktop, 30px mobile, weight 500; display stack is Abadi MT Condensed Light, Abadi, Arial Narrow, Segoe UI Light, Segoe UI, sans-serif. Abadi was not found in the initial local font check; never claim it renders without verification.
- Body stack: Segoe UI, Helvetica Neue, sans-serif. Main section headings: 18px desktop / 17px mobile, weight 600. Preserve the lighter visual direction; no Impact or oversized heavy numerals.
- Keep zero letter spacing for newly introduced copy and avoid enlarging typography without user agreement. The reference has legacy tracking on some small labels.
- Some reference labels are only 7-9px. Treat them as a known readability limitation, not an approved minimum. Do not shrink labels further; raise this during email hardening.
- Do not add marketing sections, decorative cards, new themes, or extra counters. Keep public-facing copy brief and specific.

## Fixed Versus Monthly Content

Keep logo assets, brand colors and section structure fixed. Monthly text, dates, teams, destinations and metrics come from the user's confirmed inputs.

1. Masthead and edition.
2. Hero: concise editorial opening, not a claim copied from the sample.
3. Biggest win: title, impact, contributing teams, dashboard/output link, leading KPI and applicable ATR/OTC/IC/Others breakdown.
4. Additional progress: optional distinct wins, only when supported by inputs.
5. Now Live and Coming Next: short bullets, explicit actual/planned status.
6. Adoption Momentum: calculated comparison chart and one supported takeaway.
7. Looking Ahead: biggest future priorities with outcome/timing and action if relevant.
8. Footer: confirmed Finance Hub/feedback links; no placeholder destinations in final copy.

All monthly prose must remain real HTML text, not a screenshot. In-browser `contenteditable` edits are temporary and do not save to disk; ask the user to request edits through the agent for persistent revisions.

## Adoption Visualization

- Compare the current period with a confirmed comparable prior period; do not invent history or targets.
- A yellow bar is the current indexed value. A white marker is the prior baseline (index 100).
- All three charts share one zero-based axis determined from the source values. The default ceiling is 140, expanded when needed. Raw user counts, report views and page views do not share a common volume scale.
- Keep growth and secondary totals visible; show minus signs for declines. Do not rely on color alone.
- With zero/missing baselines, replace the indexed chart with an honest status and any known totals. Accessible chart descriptions must match the rendered calculation.
- Values, geometry, axis labels, markers and insight must be regenerated together. Editing an HTML label does not recalculate its chart.

## Email Delivery Boundary

The reference uses Grid/Flexbox, CSS variables, pseudo-elements and absolute positioning. Classic Outlook cannot be assumed to reproduce it. Local relative images are not delivered to recipients automatically.

Before distribution, build and test a separate table-based, inline-styled email export with appropriately packaged CID or hosted images and email-safe chart graphics/fallbacks. Verify classic/new Outlook, dark mode, image blocking, display scaling and relevant reading-pane sizes. Browser preview checks do not certify email rendering. Agent final approval is editorial only; sending is never automatic.