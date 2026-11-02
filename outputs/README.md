# Newsletter Outputs

This folder is reserved for generated editions. Do not place reusable logos, design mockups or agent definitions here. No edition is created merely by opening the workspace.

## Naming And Contents

Create one folder per confirmed edition month using `YYYY-MM`. Within it, use the next unused revision number:

```text
YYYY-MM/
  newsletter-draft-v01.html
  newsletter-draft-v01.json
  review-v01.md
  newsletter-draft-v02.html
  newsletter-draft-v02.json
  review-v02.md
  newsletter-final.html
  newsletter-final.json
```

This tree is an example, not existing generated content. Final files are created only after explicit approval of the latest revision and resolution of blocking gaps.

## Artifact Responsibilities

- HTML is the reviewable rendered copy. It must agree with the corresponding saved data and contain no unintentional template examples.
- JSON records source facts separately from calculated growth, chart positions and insight, along with open questions and approval state.
- Review notes summarize changes, pending questions and validation actually performed. They are separate from public-facing newsletter content.
- References to shared logos from a monthly HTML file use `../../ui-assets/<filename>`. Verify image loading rather than copying mockup-relative paths unchanged.

Retain previous revisions. Never overwrite an existing final without asking. A post-approval change starts another draft and needs fresh approval. Direct edits in a browser are temporary and do not persist to these files.

## Sharing And Delivery

These records may contain internal financial updates, team information and private links. Review them before sharing and apply your organization's access and retention requirements.

Editorial approval is not Outlook certification or permission to send. Do not distribute local HTML as an email without the separate email packaging and client checks described in the [workspace README](../README.md).