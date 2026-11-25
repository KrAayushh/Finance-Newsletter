# Newsletter Outputs

This folder is reserved for generated editions. Do not place reusable logos, design mockups or agent definitions here. No edition is created merely by opening the workspace.

## Naming And Contents

Create one folder per confirmed edition month using `YYYY-MM`. Within it, use the next unused revision number:

```text
YYYY-MM/
  intake/
    request-v01.md
    request-v01.html
    collection-v01.md
    assets/
      dashboard-intake-v01.png
    handover-v01.md                (only when completeness gate passes)
  newsletter-draft-v01.html
  newsletter-draft-v01.json
  review-v01.md
  newsletter-draft-v02.html
  newsletter-draft-v02.json
  review-v02.md
  assets/
    dashboard-v01.png
  newsletter-final.html
  newsletter-final.json
```

This tree is an example, not existing generated content. Final files are created only after explicit approval of the latest revision and resolution of blocking gaps.

## Artifact Responsibilities

- HTML is the reviewable rendered copy. It must agree with the corresponding saved data and contain no unintentional template examples.
- JSON records source facts, the confirmed Go Live baseline and dashboard image path separately from rendered copy and calculated KPI changes and trends, along with open questions and approval state.
- Review notes summarize changes, pending questions and validation actually performed. They are separate from public-facing newsletter content.
- References to shared UI assets, including logos and reusable artwork, from a monthly HTML file use `../../ui-assets/<filename>`. Verify image loading rather than copying mockup-relative paths unchanged.
- Store a uniquely named copy of each supplied or confirmed dashboard image under the edition's `assets/` folder. Keep the HTML-relative image path and descriptive alt text in the data record; do not overwrite an image used by an earlier revision.

## Content Collection Records

The [newsletter-intake workflow](../agents/newsletter-intake.agent.md) uses the production V3 reply-in-place table template ([intake-request-v3.html](../agents/templates/intake-request-v3.html)) and stores edition-specific `request-vNN.md` (with rendered `request-vNN.html`), `collection-vNN.md` and, only once required inputs are complete, `handover-vNN.md` under `YYYY-MM/intake/`. Each artifact uses its own next unused revision. Received dashboard images use unique names under `YYYY-MM/intake/assets/`; the newsletter authoring agent then copies the confirmed image into `YYYY-MM/assets/` when generating the HTML/JSON/review draft.

Requests record prepared content and actual delivery evidence, or explicit **not sent** status. Collection records track scoped reply sources, conflicts and missing information. Handovers carry confirmed facts, comparable source totals, asset paths and approved omissions for the authoring agent, not newsletter HTML or editorial approval. A blocked collection must not produce a ready handover.

These records can contain internal correspondence and recipient addresses. Do not include unrelated email content, credentials or unnecessary personal details. Handover files omit recipient addresses; no mailbox integration, background monitoring or retention automation is installed by creating these records.

Retain previous revisions. Never overwrite an existing final without asking. A post-approval change starts another draft and needs fresh approval. Browser text, link and image edits are temporary and do not persist to these files; provide the changes and actual image file to the agent for a new revision.

## Sharing And Delivery

These records may contain internal financial updates, team information and private links. Review them before sharing and apply your organization's access and retention requirements.

Editorial approval is not Outlook certification or permission to send. Do not distribute local HTML as an email without the separate email packaging and client checks described in the [workspace README](../README.md).