# LLC Formation Wizard Power Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Wire the Lovie MCP server into Claude Code and write a skill that guides the model through Delaware LLC formation: auth → name check → entity setup → certificate review → filing.

**Architecture:** Lovie's npm MCP server (`@lovie-ai/formation-mcp-server@latest`) exposes 14+ tools over stdio. We discover exact tool schemas by running non-destructive tools first, then write the skill using only verified tool names and required fields — same process as the physical mail (lob-mcp) integration.

**Tech Stack:** Lovie MCP (npm, stdio), Claude Code MCP wiring, Markdown skill file

---

## File Structure

| File | Action | Purpose |
|------|--------|---------|
| `~/.claude/skills/llc-formation/SKILL.md` | Create | Skill that teaches the model the Lovie tool flow |
| `~/projects/wizard-powers/llc-formation/README.md` | Create | Requirements table, gotchas, setup command |
| `~/projects/wizard-powers/plan.json` | Modify | Mark LLC formation phase complete |
| `~/projects/claude-config/skills/llc-formation/SKILL.md` | Create (sync) | Copy of skill in source-controlled config repo |

---

### Task 1: Wire Lovie MCP and verify connection

**Files:**
- No files created — verifying MCP wiring only

- [ ] **Step 1: Add the MCP server**

```bash
claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest
```

Expected output: `Added MCP server lovie-formation`

- [ ] **Step 2: Verify it appears in the server list**

```bash
claude mcp list
```

Expected: `lovie-formation` appears in the list. If status shows `disconnected`, run `claude mcp restart lovie-formation` or start a new session.

- [ ] **Step 3: Confirm the MCP server actually connects in a session**

Start a Claude Code session and run `/mcp` inside it. Expected: `lovie-formation` shows `✓ Connected` with a tool count > 0.

- [ ] **Step 4: Commit the MCP config change**

The MCP server entry is stored in `~/.claude/settings.json`. It's tracked in `~/projects/claude-config`.

```bash
cd ~/projects/claude-config
git add .claude/settings.json
git commit -m "feat: add lovie-formation MCP server"
```

---

### Task 2: Discover tool schemas (read-only tools only)

**Goal:** Before writing the skill, know the exact required fields for every Lovie tool. Use read-only tools to map this. Do NOT call `formation_start`, `formation_approve_certificate`, or any setter until Task 3.

**Files:**
- No files created — discovery only

- [ ] **Step 1: List available info topics**

Call `formation_list_info_topics` with no arguments.

Expected response: an array of topic names such as `["pricing", "faq", "company-types", "requirements", "guide"]`.

Record the exact topic names returned.

- [ ] **Step 2: Get the step-by-step guide**

Call `formation_get_info` with topic = `"guide"` (or whatever the guide topic is named in the response above).

Expected: a description of the full formation flow, confirming tool call order.

- [ ] **Step 3: Get requirements info**

Call `formation_get_info` with topic = `"requirements"`.

Expected: a list of required information fields (company name, member details, etc.). Record exactly what fields each tool requires.

- [ ] **Step 4: Get company types info**

Call `formation_get_info` with topic = `"company-types"`.

Expected: valid values for `formation_set_company_type` (e.g. `"LLC"`, `"C-Corp"`, `"S-Corp"`) and `formation_set_entity_ending` (e.g. `"LLC"`, `"Inc."`, `"Corp."`).

- [ ] **Step 5: Check auth status**

Call `formation_auth_status` with no arguments.

Expected response: `{ "authenticated": false }` or similar. Record the exact response shape.

- [ ] **Step 6: Document all discovered schemas**

Write your findings as a comment block in the plan (add below this step, inline). Format:

```
Discovered tool schemas (from Task 2):
- formation_check_name: { name: string }
- formation_set_company_type: { type: "LLC" | "C-Corp" | "S-Corp" }
- formation_set_entity_ending: { ending: string }
- formation_set_company_name: { name: string }
- formation_add_shareholder: { name: string, email: string, ownership_percentage: number }
- formation_set_registered_agent: { ... }
- formation_set_authorized_party: { name: string, email: string }
... (fill in from actual responses)
```

**Do not proceed to Task 3 until all required fields are documented.**

---

### Task 3: Auth flow test

**Files:**
- No files created — testing auth only

- [ ] **Step 1: Initiate browser login**

Call `formation_login` with no arguments.

Expected: a browser window opens to the Lovie dashboard login page. If no browser window appears, check that `BROWSER` env var is set or that a default browser is configured on the system.

- [ ] **Step 2: Log in and copy the token**

In the browser: create a Lovie account (free) or log into an existing one. After login, the dashboard should display an API token or session token. Copy it.

- [ ] **Step 3: Set the token**

Call `formation_set_token` with the copied token.

Expected response: `{ "success": true }` or similar confirmation. Record exact response shape.

- [ ] **Step 4: Verify auth is now active**

Call `formation_auth_status` again.

Expected: `{ "authenticated": true }` or the equivalent. If still unauthenticated, the token may have expired or been copied incorrectly — repeat Steps 1–3.

---

### Task 4: Non-destructive flow tests

**Goal:** Test every tool that does NOT mutate state (name check, info reads). Confirm exact response shapes and error cases before building the setup sequence.

**Files:**
- No files created — testing only

- [ ] **Step 1: Check an available name**

Call `formation_check_name` with a clearly unique, fictional name (e.g. `"Zarknox Consulting LLC"`).

Expected: response contains a field indicating the name IS available (e.g. `{ "available": true }` or `{ "status": "available" }`). Record the exact field name.

- [ ] **Step 2: Check an unavailable name**

Call `formation_check_name` with a common name likely to be taken (e.g. `"Apple LLC"` or `"Google LLC"`).

Expected: response indicates NOT available. This confirms the error case the skill must handle. Record exact response shape.

- [ ] **Step 3: Document name check response shapes**

Add a comment below this step:

```
formation_check_name responses:
  Available:   { <field>: <value> }
  Unavailable: { <field>: <value> }
```

Fill in from actual responses above.

---

### Task 5: Full formation dry-run (through certificate generation — do NOT approve)

**Goal:** Run the complete setup sequence for a test entity. Stop at `formation_generate_certificate`. Never call `formation_approve_certificate` during testing — that files a real entity with Delaware SOS.

Use this test entity throughout:
- Company name: `"Test Venture LLC"` (check availability first)
- Type: `"LLC"`, ending: `"LLC"`
- Member: your own name, your own email, 100% ownership
- Authorized party: your own name and email
- State: Delaware

- [ ] **Step 1: Start a formation session**

Call `formation_start` with no arguments (or whatever fields are required per Task 2 discovery).

Expected: session ID or session object confirming a new formation session has begun. Record the response shape.

- [ ] **Step 2: Set the state**

Call `formation_set_state` with `{ state: "Delaware" }` (or the exact field name from Task 2).

Expected: confirmation that state is set.

- [ ] **Step 3: Set company type**

Call `formation_set_company_type` with `{ type: "LLC" }` (use exact field name from Task 2).

Expected: confirmation.

- [ ] **Step 4: Set entity ending**

Call `formation_set_entity_ending` with `{ ending: "LLC" }` (use exact field name from Task 2).

Expected: confirmation.

- [ ] **Step 5: Check name availability**

Call `formation_check_name` with `{ name: "Test Venture LLC" }`.

Expected: available. If not available, pick a different test name and use it for the rest of this task.

- [ ] **Step 6: Set company name**

Call `formation_set_company_name` with `{ name: "Test Venture LLC" }` (use exact field name from Task 2).

Expected: confirmation.

- [ ] **Step 7: Add a member/shareholder**

Call `formation_add_shareholder` with your own info. Use the exact field names from Task 2 Step 6 discovery. The fields below are guesses — replace them with verified names:

```
{ <name_field>: "Zachary Kiihne", <email_field>: "zkiihne@gmail.com", <ownership_field>: 100 }
```

Expected: confirmation that member was added.

- [ ] **Step 8: Set registered agent**

Call `formation_set_registered_agent` with whatever fields Task 2 revealed (likely Lovie as default agent).

Expected: confirmation.

- [ ] **Step 9: Set authorized party**

Call `formation_set_authorized_party` with your own info (use exact fields from Task 2):

```
{ name: "Zachary Kiihne", email: "zkiihne@gmail.com" }
```

Expected: confirmation.

- [ ] **Step 10: Check session status**

Call `formation_get_status` with no arguments.

Expected: all setup fields populated. Record exact status shape — this is how the skill will verify completeness before generating the certificate.

- [ ] **Step 11: Generate certificate (STOP HERE)**

Call `formation_generate_certificate` with no arguments.

Expected: a response containing a PDF URL. Record the exact field name for the URL.

**DO NOT call `formation_approve_certificate`.** The test is complete once the PDF URL is in hand. Verify the PDF loads in a browser — confirm the entity details are correct.

- [ ] **Step 12: Document all response shapes**

Add a comment below this step with the exact response fields discovered across Tasks 2–5. This is the source of truth for the skill.

---

### Task 6: Write the skill

**Files:**
- Create: `~/.claude/skills/llc-formation/SKILL.md`

Use ONLY tool names and field names verified in Tasks 2–5. No guessing.

- [ ] **Step 1: Create the skill directory**

```bash
mkdir -p ~/.claude/skills/llc-formation
```

- [ ] **Step 2: Write the skill file**

Write `~/.claude/skills/llc-formation/SKILL.md` with this structure (fill in exact fields from Task discovery):

````markdown
---
name: llc-formation
description: Form a Delaware LLC, C-Corp, or S-Corp via Lovie. Guides auth → name check → entity setup → certificate review → filing. Always requires human approval before filing.
---

# LLC Formation Wizard Power

Forms real Delaware entities via **Lovie MCP** (`lovie-formation` MCP server). Free — you pay only ~$90 Delaware state filing fee.

Check status: `claude mcp list` — look for "lovie-formation".

---

## Core Flow (Every Formation)

1. **Check auth** — call `formation_auth_status` first; guide through login if needed
2. **Check name** — verify with Delaware SOS before collecting any other details
3. **Gather details** — company type, members, authorized party
4. **Setup sequence** — run 8 tools in order to configure the entity
5. **Generate certificate** — get PDF for human review
6. **Review** — show the PDF URL; require explicit approval
7. **File** — call `formation_approve_certificate` ONLY after approval

Never call `formation_approve_certificate` without showing the certificate PDF and getting explicit confirmation. This is irreversible.

---

## Auth Flow

```
formation_auth_status()
→ if not authenticated:
    formation_login()           # opens browser — user logs in
    formation_set_token({ token: "<copied from dashboard>" })
    formation_auth_status()     # verify now authenticated
```

---

## Name Check

Always check name availability before collecting any other formation details.

```
formation_check_name({ name: "<proposed name>" })
→ if unavailable: stop, ask user for an alternative name
→ if available: proceed
```

---

## Setup Sequence (run in this exact order)

```
formation_start()
formation_set_state({ <state_field>: "Delaware" })
formation_set_company_type({ <type_field>: "LLC" })     # or "C-Corp" / "S-Corp"
formation_set_entity_ending({ <ending_field>: "LLC" })  # or "Inc." / "Corp."
formation_set_company_name({ <name_field>: "<verified name>" })
formation_add_shareholder({ <member fields> })           # repeat for each member
formation_set_registered_agent({ <agent fields> })
formation_set_authorized_party({ <party fields> })
```

**Replace `<field>` placeholders with verified field names from your test run.**

---

## Certificate + Filing

```
formation_generate_certificate()
→ returns: { <url_field>: "https://..." }

# STOP. Show the user:
"Certificate ready: <url>
 Review it — this will be filed with Delaware SOS and cannot be undone.
 Proceed with filing?"

# Only after explicit approval:
formation_approve_certificate()
```

---

## Entity Types

| Type | Ending options | Notes |
|------|---------------|-------|
| LLC | LLC | Pass-through taxation, flexible structure |
| C-Corp | Inc., Corp. | Best for VC-backed startups |
| S-Corp | Inc., Corp. | Pass-through, max 100 shareholders |

---

## Member Fields

Each call to `formation_add_shareholder` adds one member. For a sole LLC:
- name: full legal name
- email: contact email
- ownership: 100 (percent)

For multi-member: call once per member, ownership must sum to 100.

---

## Gotchas

*(Fill in from Task 5 dry-run — any required fields not obvious from tool names, any error messages encountered, any ordering constraints discovered.)*

---

## Cost

| Item | Cost |
|------|------|
| Lovie service fee | Free |
| Delaware state filing | ~$90 |
| Expedited (24hr) | +$50 |
| Same-day | +$100 |

---

## Setup (if not wired)

```bash
claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest
```

Auth is browser-based (one-time). After login, copy token from Lovie dashboard and call `formation_set_token`.
````

- [ ] **Step 3: Fill in all placeholder fields**

Go back through the skill and replace every `<field>`, `<url_field>`, `<agent fields>`, and `<party fields>` placeholder with the exact names discovered in Tasks 2–5.

Also fill in the Gotchas section with anything surprising found during the dry-run.

The skill is not done until zero placeholders remain.

---

### Task 7: Write README and sync to claude-config

**Files:**
- Create: `~/projects/wizard-powers/llc-formation/README.md`
- Create: `~/projects/claude-config/skills/llc-formation/SKILL.md` (sync)

- [ ] **Step 1: Create the wizard-powers integration directory**

```bash
mkdir -p ~/projects/wizard-powers/llc-formation
```

- [ ] **Step 2: Write the README**

Write `~/projects/wizard-powers/llc-formation/README.md`:

```markdown
# LLC Formation Wizard Power

Forms real Delaware entities via [Lovie](https://lovie.co) MCP.

## How It Works

The `llc-formation` skill guides Claude through Lovie's formation API:
auth → name check → entity setup → certificate review → filing.

## Supported Entity Types

- LLC
- C-Corp
- S-Corp

## Requirements & Blockers

| Requirement | Status | How to Unblock |
|-------------|--------|----------------|
| Lovie account | ⬜ Needed | Free at lovie.co — sign up with email |
| Browser login (one-time) | ⬜ Needed | `formation_login` opens browser; copy token to `formation_set_token` |
| lovie-formation MCP wired | ⬜ Needed | `claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest` |

*(Update status column to ✅ Done as each is completed)*

## Known Gotchas

*(Fill in from dry-run in Task 5)*

## Cost

| Item | Cost |
|------|------|
| Lovie service | Free |
| Delaware state filing (LLC) | ~$90 |

## Setup

```bash
claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest
```

Then start a session and the `llc-formation` skill will guide you through login.
```

- [ ] **Step 3: Sync skill to claude-config**

```bash
mkdir -p ~/projects/claude-config/skills/llc-formation
cp ~/.claude/skills/llc-formation/SKILL.md ~/projects/claude-config/skills/llc-formation/SKILL.md
```

- [ ] **Step 4: Commit wizard-powers**

```bash
cd ~/projects/wizard-powers
git add llc-formation/README.md
git commit -m "feat: add LLC formation wizard power — Lovie MCP integration"
```

- [ ] **Step 5: Commit claude-config**

```bash
cd ~/projects/claude-config
git add skills/llc-formation/SKILL.md
git commit -m "feat: add llc-formation skill (Lovie MCP)"
```

---

### Task 8: Update plan.json and push both repos

**Files:**
- Modify: `~/projects/wizard-powers/plan.json`

- [ ] **Step 1: Update plan.json**

In `~/projects/wizard-powers/plan.json`, replace the `"Next Integration (TBD)"` phase with:

```json
{
  "name": "LLC Formation",
  "status": "complete",
  "provider": "Lovie (via lovie-formation MCP)",
  "requirements": [
    {
      "id": "lovie-account",
      "description": "Free Lovie account",
      "how": "Sign up at lovie.co",
      "status": "complete"
    },
    {
      "id": "browser-auth",
      "description": "One-time browser login to get token",
      "how": "formation_login → copy token → formation_set_token",
      "status": "complete"
    },
    {
      "id": "lovie-mcp-wired",
      "description": "lovie-formation MCP server in Claude Code",
      "how": "claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest",
      "status": "complete"
    }
  ],
  "steps": [
    {
      "id": "llc-skill",
      "title": "Create LLC formation wizard skill",
      "status": "complete",
      "output": "~/.claude/skills/llc-formation/SKILL.md"
    },
    {
      "id": "lovie-mcp-wiring",
      "title": "Wire lovie-formation MCP into Claude Code",
      "status": "complete"
    },
    {
      "id": "formation-test",
      "title": "Dry-run through formation_generate_certificate (not approve)",
      "status": "complete",
      "note": "<fill in gotchas discovered during dry-run>"
    }
  ]
}
```

Also add a new `"Next Integration (TBD)"` phase after this one (copy the template from the current one in plan.json).

- [ ] **Step 2: Commit plan.json**

```bash
cd ~/projects/wizard-powers
git add plan.json
git commit -m "chore: mark LLC formation complete in plan.json"
```

- [ ] **Step 3: Run the 5-point completion checklist**

Per `wizard-powers/CLAUDE.md`:

```
[ ] All test steps pass end-to-end (Tasks 3–5 complete without errors)
[ ] Skill is in directory format (~/.claude/skills/llc-formation/SKILL.md)
[ ] Skill synced to claude-config (~/projects/claude-config/skills/llc-formation/SKILL.md)
[ ] README requirements table accurate (no stale "NEEDED" items)
[ ] plan.json phase status is "complete"
```

If any item is unchecked, fix it before pushing.

- [ ] **Step 4: Push both repos**

```bash
cd ~/projects/wizard-powers && git push origin main
cd ~/projects/claude-config && git push origin main
```

- [ ] **Step 5: Verify on GitHub**

Check `github.com/zkiihne/wizard-powers` — `llc-formation/README.md` and updated `plan.json` should be visible.
Check `github.com/zkiihne/claude-config` — `skills/llc-formation/SKILL.md` should be visible.
