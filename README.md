# Finance Newsletter

A dedicated VS Code workspace for producing the monthly Finance Hub newsletter with the **Finance Newsletter Updates** custom agent. Users provide business facts and adoption totals in conversation; the agent clarifies gaps, prepares concise copy, calculates chart values and creates an HTML draft for review. Each revision is retained, and final copy requires explicit approval.

The audience includes finance executives, global and zonal directors, tower leads, their organizations, developers and operations leads. The newsletter emphasizes business impact, collaboration, releases, future priorities and adoption momentum.

**Current scope:** a conversational authoring workflow and browser preview, not a deployed backend, frontend application or automatic email sender. Actual Outlook rendering remains unverified. Read [ABOUT.md](ABOUT.md) for the purpose, responsibilities and delivery boundary.

## Workspace Structure

```text
Finance Newsletter/
	Finance Newsletter.code-workspace
	README.md
	ABOUT.md
	.github/
		agents/
			finance-newsletter-updates.agent.md
	ui-assets/
		UI.md
		ab-inbev-symbol-gold.png
		command-center-logo-yellow-white-2line.png
	mockups/
		newsletter.html
	outputs/
		README.md
		YYYY-MM/                         (created during use)
			newsletter-draft-v01.html
			newsletter-draft-v01.json
			review-v01.md
			newsletter-final.html          (only after approval)
			newsletter-final.json
```

| Area | Responsibility | Editing Rule |
| --- | --- | --- |
| [Agent](.github/agents/finance-newsletter-updates.agent.md) | Intake, clarifications, calculations, revisions and approval rules | Keep here for native VS Code discovery; do not duplicate it in another agents folder. |
| [UI assets and guide](ui-assets/UI.md) | Reusable brand rules, colors, typography, logos and known design limitations | Change branding deliberately, not as part of routine monthly generation. |
| [Visual mockup](mockups/newsletter.html) | The latest newsletter design reference with illustrative content | Preserve while drafting; do not treat sample figures as facts. |
| [Outputs](outputs/README.md) | Edition-specific drafts, saved data, review records and approved copies | Separate by month, retain revisions, never silently overwrite an approved edition. |

The agents folder intentionally lives inside `.github/`: this is the standard discovery location when this folder is opened as a VS Code workspace. The original newsletter preview outside this workspace is not an output managed by this workflow.

## Requirements And Quick Start

You need VS Code with Copilot Chat/custom-agent support, an available model, permission to read and write this workspace, and a browser for preview. Calculation and browser checks use the tools available in the active session. There is no package installation or server required for the current HTML mockup.

1. Open [Finance Newsletter.code-workspace](Finance%20Newsletter.code-workspace) as a workspace in VS Code, not just as a text file. This makes this folder the workspace root.
2. Open Copilot Chat and select **Finance Newsletter Updates** from the agent selector.
3. Say: **Start my Finance Hub newsletter for November 2026. Ask me for the information you need.**
4. Answer short question batches with rough notes, bullets or pasted tables. The agent reuses known answers and asks relevant follow-ups.
5. Open the generated draft, review the wording, figures, charts, team credits and links, then request edits.
6. Approve a named revision explicitly when ready, for example: **Approve newsletter-draft-v03 as final for November 2026.**

If the agent is not listed, verify that this dedicated folder is the open workspace root and reload the VS Code window. Agent availability depends on your installed Copilot version and workspace policies.

## Monthly Intake

| Topic | What To Provide | What The Agent Clarifies Or Produces |
| --- | --- | --- |
| Month and year | Edition month/year; adoption reporting and comparison periods if different | Resolves relative dates and distinguishes the edition date from the metric period. |
| Biggest win | What changed, verified impact, teams, dashboard/output URL and leading KPI with units | Leads with the outcome, credits collaborators, and asks about ambiguous or unsupported claims. |
| What went live | Actual releases, dates/status, benefit and optional destination | Separates completed releases from planned work; avoids repeating the same copy across sections. |
| Upcoming | Near-term releases, expected timing, dependencies and owner if relevant | Uses planned/expected wording rather than inventing commitments. |
| Adoption | Current and previous comparable totals for users, report views and page views | Calculates growth and chart geometry, then proposes a supported takeaway. |
| Looking Ahead | One or two largest future initiatives, intended outcome, timing, teams/owner and reader action | Distinguishes strategic priorities from routine Coming Next updates. |

For the featured KPI, provide the metric name, unit, result, period and applicable ATR/OTC/IC/Others values. The agent must not average percentages or assume different stream measures share one scale. An overall result needs either a confirmed value or an agreed aggregation rule.

Supply or confirm the Finance Hub and feedback links as well. A dashboard link may be pending in a draft; it must be resolved or deliberately omitted with your agreement before finalization. Do not provide passwords, tokens or other secrets.

## Adoption Inputs And Calculations

The minimum data for all three month-over-month charts is six totals:

| Measure | Current Period | Previous Comparable Period |
| --- | --- | --- |
| Users | User-provided total | User-provided total |
| Report views | User-provided total | User-provided total |
| Page views | User-provided total | User-provided total |

Also confirm what users means (for example, distinct active users), the source, coverage/filters, reporting windows and whether numbers are exact or rounded. Missing values are not zero, and distinct users across streams cannot be summed without deduplication.

- Absolute change is current minus previous.
- With a positive previous total, percent growth is the change divided by previous, multiplied by 100.
- The prior period has index 100; current index is current divided by previous, multiplied by 100. All valid charts use one common zero-based axis, expanding beyond 140 when needed.
- Previous zero and current positive displays **New from zero**, not an infinite growth rate. Both zero displays **No recorded activity**. Missing/non-comparable data displays an honest comparison-unavailable state.
- Growth, visible labels, accessible chart descriptions, bar widths and baseline markers are recalculated together. Declines must retain their minus signs and shorter bars.
- Usage growth may suggest more browsing per user; it does not prove efficiency, financial savings, adoption across additional teams or improved business outcomes.

The agent is instructed to use runtime calculations from saved source data. These are agent workflow rules, not a standalone enforced calculation service.

## Drafts, Review And Approval

Each edition goes under `outputs/YYYY-MM/`, using the edition month. Each revision has a matching HTML draft, JSON record and review note. The JSON separates source facts from derived values and records open questions and approval state.

The review note summarizes changes, source data, unresolved items, checks actually run and delivery limitations. The agent asks for clarification whenever an uncertain answer would change the published meaning. If you request an early preview, gaps may be marked explicitly instead of filled with invented content.

Request changes through the agent so they persist in a new revision. In-browser editable text is temporary and does not update the saved JSON, chart calculations or HTML file. If you edit files directly, tell the agent to reconcile those changes before it regenerates anything.

Finalization requires explicit approval of the latest revision and no blocking gaps. A correction after approval returns the edition to draft and requires fresh approval. **Final means editorially approved, not certified for Outlook or authorized to send.**

## Validation And Delivery

Before a draft handoff, the agent checks saved-data parsing, source-to-copy consistency, calculated chart geometry, actual logo paths, accessible descriptions and desktop/mobile layout when tools permit. Checks that cannot run must be disclosed. A syntactically valid private URL does not establish that recipients can access it.

The reference uses browser features such as Grid/Flexbox, CSS variables and positioned chart markers. Some small labels also remain a readability limitation. Classic Outlook cannot be assumed to reproduce this layout. A browser screenshot is not an Outlook rendering test.

Before distribution, build and test an email-specific export with table layouts, inline styles, email-safe chart graphics/fallbacks and appropriately packaged hosted or CID images. Verify classic/new Outlook, dark mode, image blocking, display scaling and relevant reading-pane widths. Relative local image links will not deliver logo files to recipients automatically.

No mailbox access or automatic sending is implemented. No frontend form or deployed agent backend is implemented. The saved JSON is a starting point for future form integration, not a validated API contract. Keep human approval in the loop when those components are added.

## Maintenance And Troubleshooting

- **Missing logos:** keep `ui-assets/` alongside `mockups/` and `outputs/`. The mockup uses `../ui-assets/`; monthly HTML under `outputs/YYYY-MM/` uses `../../ui-assets/`.
- **Unchanged graph after editing text:** request regeneration from source totals; visible labels alone do not control bar lengths.
- **New branding or layout:** update the UI guide and mockup together, then verify both narrow and desktop previews. Do not modify the agent's intake facts to force a desired story.
- **Outlook differences:** retain the browser prototype as a design reference and test a separate email-safe export. Do not mark the prototype as email-tested.
- **Sensitive content:** obtain the appropriate internal approvals before sharing drafts, team details or private dashboard links. This workflow does not configure access controls, retention or distribution lists.