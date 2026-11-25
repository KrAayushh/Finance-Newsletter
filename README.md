# Finance Newsletter

A dedicated VS Code workspace for producing the monthly Finance Hub newsletter with the **Finance Newsletter Updates** custom agent. Users provide business facts and adoption totals in conversation; the agent clarifies gaps, prepares concise copy, calculates adoption changes and creates an HTML draft for review. Each revision is retained, and final copy requires explicit approval.

The audience includes finance executives, global and zonal directors, tower leads, their organizations, developers and operations leads. The newsletter emphasizes business impact, collaboration, releases, future priorities and adoption metrics.

**Current scope:** conversational content collection, authoring and browser preview, not a deployed backend, frontend application or unattended email sender. The intake agent can use separately available authorized email tools after message approval, or prepare an email draft when tools are absent. Actual Outlook rendering remains unverified. Read [ABOUT.md](ABOUT.md) for the purpose, responsibilities and delivery boundary.

## Workspace Structure

```text
Finance Newsletter/
	Finance Newsletter.code-workspace
	README.md
	ABOUT.md
	.github/
		agents/
			newsletter-intake.agent.md
			finance-newsletter-updates.agent.md
	agents/
		newsletter-intake.agent.md
		templates/
			intake-request-v3.html
	ui-assets/
		UI.md
		ab-inbev-symbol-header.png
		ab-inbev-wordmark-header.png
		command-center-new-logo.png
		control-atr-dashboard.png
		finance-hub-new.png
		finance-laptop-powerbi-v2.png
	mockups/
		newsletter.html
	outputs/
		README.md
		YYYY-MM/                         (created during use)
			newsletter-draft-v01.html
			newsletter-draft-v01.json
			review-v01.md
			assets/                       (edition dashboard images)
			newsletter-final.html          (only after approval)
			newsletter-final.json
```

| Area | Responsibility | Editing Rule |
| --- | --- | --- |
| [Agent](.github/agents/finance-newsletter-updates.agent.md) | Intake, clarifications, calculations, revisions and approval rules | Keep here for native VS Code discovery; do not duplicate it in another agents folder. |
| [Intake workflow](agents/newsletter-intake.agent.md) | V3 Outlook-native reply-in-place table requests, scoped thread collection and complete Markdown handover | Its small [VS Code entry](.github/agents/newsletter-intake.agent.md) loads this single workflow; do not duplicate the instructions. |
| [V3 intake email template](agents/templates/intake-request-v3.html) | Production Outlook-native 2-column fillable table HTML email template | Replace all `{{...}}` placeholders per edition; do not put edition facts into the reusable template. |
| [UI assets and guide](ui-assets/UI.md) | Reusable brand rules, colors, typography, logos and known design limitations | Change branding deliberately, not as part of routine monthly generation. |
| [Visual mockup](mockups/newsletter.html) | The authoritative newsletter design and preview controls, with illustrative content | Preserve while drafting; do not treat sample figures or the sample dashboard image as facts. |
| [Outputs](outputs/README.md) | Edition-specific drafts, saved data, review records and approved copies | Separate by month, retain revisions, never silently overwrite an approved edition. |

Native agent entries live inside `.github/agents/`, the standard VS Code discovery location. The root `agents/` folder holds the intake workflow loaded by its native entry. The original newsletter preview outside this workspace is not an output managed by this workflow.

## Requirements And Quick Start

You need VS Code with Copilot Chat/custom-agent support, an available model, permission to read and write this workspace, and a browser for preview. Calculation and browser checks use the tools available in the active session. There is no package installation or server required for the current HTML mockup.

1. Open [Finance Newsletter.code-workspace](Finance%20Newsletter.code-workspace) as a workspace in VS Code, not just as a text file. This makes this folder the workspace root.
2. Open Copilot Chat and select **Finance Newsletter Updates** from the agent selector.
3. Say: **Start my Finance Hub newsletter for November 2026. Ask me for the information you need.**
4. Answer short question batches with rough notes, bullets or pasted tables. The agent reuses known answers and asks relevant follow-ups.
5. Open the generated draft, review the wording, KPI cards, team credits, image and links, then request edits.
6. Approve a named revision explicitly when ready, for example: **Approve newsletter-draft-v03 as final for November 2026.**

If the agent is not listed, verify that this dedicated folder is the open workspace root and reload the VS Code window. Agent availability depends on your installed Copilot version and workspace policies.

## Collecting Content By Email (Production V3 Flow)

The workspace uses a two-agent intake-to-output architecture built around the **V3 Outlook-native Reply-in-Place Fillable Table** ([intake-request-v3.html](agents/templates/intake-request-v3.html)):

```text
newsletter-intake (Stage 1: Collection)
  1. Render V3 table from agents/templates/intake-request-v3.html -> outputs/YYYY-MM/intake/request-vNN.md + .html
  2. Explicit send approval -> send HTML via authorized Outlook MCP (or save draft) -> collection-vNN.md (awaiting-replies)
  3. On user resume -> read confirmed thread -> parse V3 table cells & save image attachments -> collection-vNN.md
  4. Completeness gate passes -> outputs/YYYY-MM/intake/handover-vNN.md (ready-for-drafting)
        │
        ▼
Finance Newsletter Updates (Stage 2: Authoring & Output)
  5. Validate handover -> copy dashboard image to outputs/YYYY-MM/assets/ -> calculate adoption metrics
  6. Generate newsletter-draft-vNN.html + .json + review-vNN.md -> iterate -> explicit approval -> newsletter-final.html + .json
```

1. Select **newsletter-intake** and say: **Start content collection for December 2026. Ask me for the recipients and response deadline.**
2. Provide recipient addresses, edition and deadline/timezone (or explicitly no fixed deadline). The agent renders the V3 reply-in-place table from [intake-request-v3.html](agents/templates/intake-request-v3.html) and presents the exact request, sender and recipients for approval before sending.
3. With an authorized email tool (such as the local `outlook-com` MCP server), the agent sends the HTML table email and records the submission receipt. Without one it saves the prepared draft marked **not sent** for you to send. Recipients simply click **Reply**, type into the highlighted **Your Input** column, attach their dashboard image, and click **Send**.
4. Invoke **newsletter-intake** again to collect replies from the confirmed request thread (or supply pasted replies and local files if thread/attachment tools are unavailable). The agent parses the filled V3 table cells, deduplicates quoted rows, and saves attachments under `outputs/YYYY-MM/intake/assets/`. There is no background polling or automatic reminder.
5. Resolve all required gaps and conflicts. The agent creates `outputs/YYYY-MM/intake/handover-vNN.md` only when all newsletter requirements are complete, including the relevant dashboard image and comparable adoption totals.
6. Select **Finance Newsletter Updates** and say: **Create a newsletter draft from this handover**, supplying `handover-vNN.md`. It validates the inputs, copies the confirmed dashboard image into `outputs/YYYY-MM/assets/`, and calculates adoption changes before creating the versioned HTML/JSON/review draft; handover readiness is not final approval.

Requests, collection records and handovers are versioned separately under the edition's `intake/` folder. See the [intake workflow](agents/newsletter-intake.agent.md) for its completeness gate and handover format. Recipients are supplied at runtime, not hard-coded.

## Monthly Intake

| Topic | What To Provide | What The Agent Clarifies Or Produces |
| --- | --- | --- |
| Month and year | Edition month/year; current adoption period and Go Live baseline dates | Resolves relative dates and distinguishes the edition date from metric periods. |
| Biggest win | What changed, verified impact, teams, dashboard URL and a relevant dashboard image | Leads with the outcome, credits collaborators, and asks about ambiguous or unsupported claims. |
| What went live | Actual releases, dates/status, benefit and optional destination | Separates completed releases from planned work; avoids repeating the same copy across sections. |
| Upcoming | Near-term releases, expected timing, dependencies and owner if relevant | Uses planned/expected wording rather than inventing commitments. |
| Adoption | Current and comparable Go Live baseline totals for users, report views and page views | Calculates changes and populates the three KPI cards. |
| Looking Ahead | One or two largest future initiatives, intended outcome, timing, teams/owner and reader action | Distinguishes strategic priorities from routine Upcoming updates. |
| Feedback | Feedback destination and desired wording | Uses the mockup's feedback section and button. |

If the biggest win has a quantified impact, provide the metric, unit and period. The agent must not average percentages or aggregate stream values without a confirmed rule. The current mockup does not require a separate featured-KPI panel.

Supply a relevant local dashboard image or confirm an existing workspace image. If it is missing, a partial draft can show a placeholder, but the image must be resolved before finalization. Dashboard and feedback links may be pending in a draft; each must be resolved or deliberately omitted with your agreement before finalization. Do not provide passwords, tokens or other secrets.

## Adoption Inputs And Calculations

The minimum data for all three KPI cards is six totals:

| Measure | Current Period | Comparable Go Live Baseline |
| --- | --- | --- |
| Users | User-provided total | User-provided total |
| Report views | User-provided total | User-provided total |
| Page views | User-provided total | User-provided total |

Confirm the actual Go Live date and baseline period, what users means (for example, distinct active users), the source, coverage/filters, reporting windows or snapshot dates, and whether numbers are exact or rounded. Compare like-for-like windows or snapshots; do not assume an arbitrary previous period is Go Live. Missing values are not zero, and distinct users across streams cannot be summed without deduplication.

- Absolute change is current minus the Go Live baseline.
- With a positive baseline, percent change is the absolute change divided by the baseline, multiplied by 100.
- Baseline zero and current positive displays **New from zero**, not an infinite percentage. Both zero displays **No recorded activity**. Missing or non-comparable data displays **Comparison unavailable** in a partial draft and must be resolved before finalization.
- Current totals, signed change, trend indicators and comparison labels are recalculated together. Declines retain their minus signs, or explicit decline wording for changes too small to display numerically; unclear changes from rounded data require clarification.
- Usage growth may suggest more browsing per user; it does not prove efficiency, financial savings, adoption across additional teams or improved business outcomes.

The agent is instructed to use runtime calculations from saved source data. These are agent workflow rules, not a standalone enforced calculation service.

## Drafts, Review And Approval

Each edition goes under `outputs/YYYY-MM/`, using the edition month. Each revision has a matching HTML draft, JSON record and review note. The JSON separates source facts from rendered copy and derived values, and records open questions and approval state.

The review note summarizes changes, source data, unresolved items, checks actually run and delivery limitations. The agent asks for clarification whenever an uncertain answer would change the published meaning. If you request an early preview, gaps may be marked explicitly instead of filled with invented content.

Request changes through the agent so they persist in a new revision. In-browser text, KPI, link and image edits are temporary and do not update the saved HTML, JSON or calculations. Provide the actual image file to the agent; a temporary picker selection is not saved. If you edit files directly, tell the agent to reconcile those changes before it regenerates anything.

Finalization requires explicit approval of the latest revision and no blocking gaps. A correction after approval returns the edition to draft and requires fresh approval. **Final means editorially approved, not certified for Outlook or authorized to send.**

## Validation And Delivery

Before a draft handoff, the agent checks saved-data parsing, source-to-copy consistency, calculated card values and trends, image paths, accessible descriptions, preview controls and desktop/mobile layout when tools permit. Checks that cannot run must be disclosed. A syntactically valid private URL does not establish that recipients can access it.

The reference uses browser features such as Grid/Flexbox, CSS variables and positioned preview controls. Some small labels also remain a readability limitation. Classic Outlook cannot be assumed to reproduce this layout. A browser screenshot is not an Outlook rendering test.

Before distribution, build and test an email-specific export with table layouts, inline styles, email-safe KPI presentation/fallbacks and appropriately packaged hosted or CID images. Verify classic/new Outlook, dark mode, image blocking, display scaling and relevant reading-pane widths. Relative local image links will not deliver image files to recipients automatically.

No mailbox integration or unattended sending service is implemented in this repository. The intake agent relies on authorized session tools and explicit message approval, with a saved-draft/manual-reply fallback. No frontend form or deployed agent backend is implemented. The saved JSON is a starting point for future form integration, not a validated API contract.

## Maintenance And Troubleshooting

- **Missing logos:** keep `ui-assets/` alongside `mockups/` and `outputs/`. The mockup uses `../ui-assets/`; monthly HTML under `outputs/YYYY-MM/` uses `../../ui-assets/`.
- **Unchanged trend after editing a KPI:** request regeneration from source totals; browser edits do not recalculate other card values or save to disk.
- **New branding or layout:** update the UI guide and mockup together, then verify both narrow and desktop previews. Do not modify the agent's intake facts to force a desired story.
- **Outlook differences:** retain the browser prototype as a design reference and test a separate email-safe export. Do not mark the prototype as email-tested.
- **Sensitive content:** obtain the appropriate internal approvals before sharing drafts, team details or private dashboard links. This workflow does not configure access controls, retention or distribution lists.