# Wizard Power Development Process

Four phases per wizard power, in order. Never skip ahead.

---

## Phase 1 — Research

Goal: understand the full landscape before writing a single line.

Deliverable: a filled-out research doc for this specific power (see `template.md`).

What to cover:
1. All viable providers — not just the obvious ones
2. Pricing model (per-use, subscription, tiered)
3. Sandbox / test environment availability
4. API maturity (stable vs beta, rate limits, uptime SLA)
5. Auth model (API key, OAuth, webhook, etc.)
6. Reversibility window — is there one? How long?
7. ToS restrictions (what's prohibited, what requires KYC/verification)
8. Compliance surface (legal, regulatory, fraud risk)
9. Real-world edge cases (what breaks in practice, not just in docs)
10. Existing MCP servers or Claude integrations (don't rebuild what exists)

Done when: you can answer any question about the power without opening a browser.

---

## Phase 2 — Prototype

Goal: prove that the action can actually be taken end-to-end in a real environment.

Deliverable: a working script (Python, usually) that executes one real call against the sandbox.

What to build:
1. Authenticate with the chosen provider
2. Execute the core action (e.g., actually queue a letter in Lob's test env)
3. Parse and print the response (confirmation ID, status, etc.)
4. Trigger at least one failure mode and confirm the error is readable

Done when: you've personally run the script and seen it work, including one error case.

---

## Phase 3 — Write the Skill

Goal: turn the prototype into a production-ready Claude skill.

Deliverable: a Claude skill file (.md) built using the anatomy in `skill-anatomy.md`.

Steps:
1. Fill out all 8 dimensions using the template in `skill-anatomy.md`
2. Score it — must be 8/8 before moving to Phase 4
3. Wire the prototype's API logic into the skill's execution step
4. Define the confirmation gate copy exactly as it will appear to the user
5. Define the receipt format exactly as it will appear

Done when: score is 8/8 and skill file is committed.

---

## Phase 4 — Test the Skill

Goal: confirm the skill behaves correctly when invoked naturally.

Deliverable: a short test log noting what passed and what needed fixing.

What to test:
1. Happy path — trigger it with natural language, confirm the action completes
2. Each failure mode from Phase 3 — trigger the error condition, confirm the message is clear
3. Cancellation path — if reversible, test the cancel command within the window
4. Edge inputs — missing required fields, malformed addresses, etc.
5. Receipt format — confirm the output is readable and contains everything needed to follow up

Done when: all failure modes hit at least once, happy path confirmed, no surprises.

---

## State Tracker

Each wizard power moves through phases. Track status here as powers are developed.

| Power | Phase 1 | Phase 2 | Phase 3 | Phase 4 |
|-------|---------|---------|---------|---------|
| Physical mail | | | | |
| LLC formation | | | | |
| E-signature | | | | |
| ACH payment | | | | |
| KYC/identity | | | | |
