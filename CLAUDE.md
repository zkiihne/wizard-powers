# Wizard Powers

## Vision
A toolkit that hooks AI agents into real-world APIs — things with genuine physical, legal, or financial impact that can be triggered entirely digitally. Think: form an LLC, send certified mail, file a tax document, bind an insurance policy, buy a domain — all from a prompt.

## Goal
Build agent-ready integrations for the most impactful real-world APIs, each exposed as a Claude skill with a tested, documented flow.

## Stack
Prefer existing MCP servers over building from scratch. Each power = one MCP server + one skill file.

## Source of Truth
- `docs/research-landscape.md` — full API landscape research (18 categories, 3 tiers)
- `plan.json` — work phases and completion state per integration
- `<power>/README.md` — per-integration requirements, gotchas, setup
- `~/.claude/skills/<power>/SKILL.md` — skill file (also synced to `~/projects/claude-config/skills/<power>/SKILL.md`)
- GitHub: `zkiihne/wizard-powers`

---

## How to Add a New Wizard Power

Every integration follows this exact sequence. Do not skip or reorder steps.

### Step 1 — Research
- Find the best MCP server for this API (check npm, GitHub). Prefer existing servers over writing one.
- Read the MCP server's README fully. Note every required field, auth setup, and mode flag.
- Identify the tool names exactly as they appear in the server (not guessed from docs).

### Step 2 — Wire the MCP server
- Run `claude mcp add <name> ...` with all required env vars.
- Restart Claude Code. Verify with `claude mcp list` — must show `✓ Connected`.

### Step 3 — Define the test plan
Before writing any code or skill, write down the exact atomic test steps with pass/fail criteria:
- One line per call to make
- Expected field in response that proves it worked
- Example: `lob_us_verifications_create({...}) → deliverability: "deliverable"`

### Step 4 — Run all tests first
Execute every test step in order. Discover all required fields, gotchas, and error cases now — before the skill captures incorrect examples. Do not write the skill until all tests pass.

Minimum test coverage for any send/create flow:
1. Validation call (address, identity, etc.)
2. Preview call → confirm token returned
3. Commit call → confirm `status: processed` (or equivalent)

### Step 5 — Write the skill
- Path: `~/.claude/skills/<power>/SKILL.md` (directory format, not a flat `.md` file)
- Use only tool names verified in Step 4
- Every code example must include all required fields (no assumed defaults)
- Document gotchas discovered in Step 4 in a dedicated "Gotchas" section

### Step 6 — Sync the skill
- Copy to `~/projects/claude-config/skills/<power>/SKILL.md`
- Commit both the skill and `wizard-powers/<power>/README.md` together

### Step 7 — Update the plan
- Mark the integration's steps complete in `plan.json`
- Update `<power>/README.md`: requirements table should show current status (not stale "NEEDED")
- Commit to `wizard-powers` repo

### Step 8 — Mark done
A power is only "complete" when:
- [ ] All test steps pass end-to-end (including commit, not just preview)
- [ ] Skill is in correct directory format and synced to claude-config
- [ ] README requirements table is accurate
- [ ] `plan.json` phase status is `complete`
- [ ] Both repos pushed to GitHub

---

## Completion Criteria Cheat Sheet

| API type | Minimum test coverage |
|----------|-----------------------|
| Send/create (mail, payments, filing) | validate → preview → commit → `status: processed` |
| Query/lookup (address check, identity) | call → expected field in response |
| Webhook/async (e-signature, tracking) | send → confirm webhook event received |

---

## Lessons from Physical Mail (first integration)

- `use_type` was required but missing from all examples — discovered only at commit time
- Tool was named `lob_us_verifications_create`, not `lob_us_verifications_verify` — wrong name in skill
- Commit payload must exactly match preview payload for token validation in live mode
- Proof PDF URL is `null` in test mode — document this, don't treat as a failure
- Skill was initially created as a flat `mail.md` instead of `mail/SKILL.md`
- Phase was marked complete after preview only — should require commit step

These are now addressed in the process above (Steps 3–4 catch all of them before writing the skill).
