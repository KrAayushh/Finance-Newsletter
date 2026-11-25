# About Finance Newsletter

## Purpose

Finance Newsletter is a reusable authoring workspace for the monthly Finance Hub newsletter. Its goal is to reduce the manual effort needed to gather updates, write consistent copy, explain adoption data and prepare a reviewable HTML edition, while retaining human control over facts, emphasis and approval.

It serves finance leadership and the teams delivering and operating the underlying capabilities: VPs, Global Directors, Tower Leads, Zonal Directors, their organizations, developers and operations leads.

## Editorial Principles

- Lead with the month's most meaningful achievement and its verified impact.
- Make the output discoverable with a confirmed dashboard or resource link.
- Recognize the teams that made the result possible without inventing contributions.
- Distinguish what is live, what is planned and what matters strategically next.
- Show adoption as a supported comparison against Go Live, not just a list of totals or an unsupported success claim.
- Keep branding stable and the copy concise, readable and easy to revise.

## Components And Responsibilities

| Component | Role |
| --- | --- |
| User/editor | Provides facts, metrics, definitions, links and team credits; resolves ambiguity; reviews and approves a specific revision. |
| newsletter-intake agent | Renders the production V3 Outlook-native reply-in-place table request, uses authorized email tools when available, parses scoped thread replies and attachments, and produces a complete Markdown handover. |
| V3 intake email template | Reusable inline-styled HTML table (`agents/templates/intake-request-v3.html`) allowing recipients to click Reply and fill inputs directly inside Outlook. |
| Finance Newsletter Updates agent | Interviews in short batches, asks follow-up questions, drafts copy, uses runtime calculations, populates HTML and produces revision records. |
| UI guide and logo assets | Define the reusable brand baseline, design choices and known limitations. |
| HTML mockup | Supplies the browser design reference; contains examples, not authoritative monthly facts. |
| Edition outputs | Preserve HTML drafts, structured source/derived data, open questions, review notes and approved copy. |

The [agent definition](.github/agents/finance-newsletter-updates.agent.md) is in the standard VS Code discovery folder. [UI assets](ui-assets/UI.md), the [mockup](mockups/newsletter.html) and [outputs guidance](outputs/README.md) have separate ownership and locations. See the [README](README.md) for the folder tree and operating instructions.

## Workflow

1. Start an edition with its month and year.
2. Gather the biggest win, teams, dashboard image and link, releases, future work, feedback link and adoption totals.
3. Clarify missing, conflicting or ambiguous inputs; do not silently assume facts.
4. Calculate valid comparisons with the confirmed Go Live baseline from supplied source values.
5. Create a versioned HTML draft, data record and review note.
6. Review and iterate, recalculating dependent KPI card values and trends after changes.
7. Record explicit approval and produce the final editorial copy.
8. Perform separate email packaging and actual client testing before distribution.

## Implemented Scope

The workspace includes a custom-agent definition, a reusable design guide, supplied logos, a browser mockup and conventions for generated editions. The agent can use the tools available in its session to ask questions, calculate values, write files and open previews. Model behavior and tool availability still require oversight.

The [intake workflow](agents/newsletter-intake.agent.md) can use authorized session email tools after approval of the exact request and recipients; otherwise it prepares a draft for manual sending and accepts supplied responses. It creates a handover only after required facts are complete. No background mailbox monitoring or automatic reminders are provided.

The workflow does not include a separate frontend form, deployed backend, enforced input schema, standalone renderer/calculation service, built-in mailbox integration, distribution-list management or unattended sending. The structured draft record supports a future integration but is not itself a running service.

## Quality And Trust

Only user-supplied or explicitly confirmed facts belong in an edition. Template examples must be removed or replaced. Unclear metric definitions, unsupported savings, ambiguous release dates and missing links require a follow-up question or an explicitly incomplete draft.

Missing data is distinct from zero. Growth from a zero baseline is not a finite percentage. Go Live and current totals need compatible definitions, scope and reporting windows or snapshot dates. Usage figures alone do not establish financial impact.

Drafts and approved versions remain separate. Approval authorizes the editorial version only, not mailbox access, recipient access or sending. The agent must never claim a browser preview proves Outlook rendering.

## Design And Delivery Status

The visual direction uses black/yellow branding, provided logo assets, a collaboration-led win with a dashboard image, update cards and three adoption KPI cards. The current mockup is authoritative for the layout and preview controls; its sample content is not edition data.

The current HTML is a design prototype. It uses browser layout techniques that require an email-specific alternative for classic Outlook, and some small labels still need readability hardening. Local logo paths work in the workspace but do not package images for an email recipient. Color tokens are prototype choices, not a certified corporate brand standard.

Actual Outlook rendering, dark mode and image-blocking behavior remain unverified. The next delivery milestone is an email-safe export followed by review of received test messages in the relevant Outlook clients. No certification, delivery guarantee or automatic distribution is implied.

## Future Direction

After the email export is validated, a frontend could collect the same inputs, a backend could validate and calculate them, and agents could draft the narrative inside a locked template. Saved drafts, preview, revision history and explicit approval should remain part of that experience. These are future components, not capabilities claimed by this workspace today.