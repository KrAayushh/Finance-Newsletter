---
name: "newsletter-intake"
description: "Request newsletter content from confirmed recipients through authorized email tools or a prepared email draft, collect scoped replies, and create a complete Markdown handover."
argument-hint: "Start content collection for an edition, collect replies from its request thread, or prepare the completed newsletter handover."
user-invocable: true
disable-model-invocation: true
agents: []
---

# newsletter-intake

Read and follow `agents/newsletter-intake.agent.md` from the workspace root before acting. That file contains this agent's complete workflow, email approval requirements, collection state and handover contract.

If that file is unavailable, report the error and stop. Do not send email or generate a handover using guessed instructions.
