# LLC Formation Wizard Power — Design Spec

**Date:** 2026-06-06  
**Status:** Approved  
**Project:** wizard-powers  

---

## Summary

Add LLC formation as a wizard power, enabling an AI agent to form a real US LLC via natural language through Lovie's MCP server. The integration covers the full Delaware formation lifecycle: name check → entity setup → certificate review → filing.

---

## Provider

**Lovie** (`@lovie-ai/formation-mcp-server@latest`)

- Free formation service (user pays only Delaware state filing fee ~$90)
- Delaware entity types: LLC, C-Corp, S-Corp
- 14 MCP tools covering auth, setup, and filing
- npm package, stdio transport
- Browser-based one-time auth flow; token persists across sessions

Alternatives considered and rejected:
- **doola** — $297/company, better for multi-state; overkill for on-demand personal use
- **FileForms** — most complete, but requires partner API application; no MCP server exists

---

## Architecture

Same pattern as the physical mail wizard power (lob-mcp):

```
User intent
  → Auth check
  → Name availability check (before collecting anything else)
  → Gather entity details conversationally
  → Execute setup tools sequentially
  → Generate certificate PDF
  → HARD GATE: human reviews PDF before filing
  → Approve certificate → filed with Delaware SOS
```

---

## MCP Tools Used

### Auth
| Tool | Purpose |
|------|---------|
| `formation_auth_status` | Check if logged in |
| `formation_login` | Opens browser to Lovie dashboard |
| `formation_set_token` | Set token after browser login |

### Pre-flight
| Tool | Purpose |
|------|---------|
| `formation_check_name` | Verify name available with Delaware SOS |

### Session + Setup
| Tool | Purpose |
|------|---------|
| `formation_start` | Begin new formation session |
| `formation_set_state` | Set state (Delaware) |
| `formation_set_company_type` | LLC / C-Corp / S-Corp |
| `formation_set_entity_ending` | Legal suffix (LLC, Inc., etc.) |
| `formation_set_company_name` | Set entity name |
| `formation_add_shareholder` | Add member(s) — call once per member |
| `formation_set_registered_agent` | Appoint registered agent |
| `formation_set_authorized_party` | Set signing party |

### Filing
| Tool | Purpose |
|------|---------|
| `formation_generate_certificate` | Generate PDF for human review |
| `formation_approve_certificate` | File with Delaware SOS (irreversible) |

---

## Flow Detail

### Step 1 — Auth
Call `formation_auth_status`. If not authenticated:
1. Call `formation_login` (opens browser)
2. User logs in, copies token from dashboard
3. Call `formation_set_token` with that token

### Step 2 — Name Check
Gather the proposed company name from the user, then immediately call `formation_check_name`. If unavailable, stop and ask for an alternative before proceeding.

### Step 3 — Gather Details
Collect conversationally:
- Company type (default: LLC)
- Entity ending (default: "LLC")
- Member(s): name, email, ownership percentage
- Authorized signing party
- Registered agent preference (Lovie can handle this)

### Step 4 — Setup Sequence
Execute tools in order:
1. `formation_start`
2. `formation_set_state` (Delaware)
3. `formation_set_company_type`
4. `formation_set_entity_ending`
5. `formation_set_company_name`
6. `formation_add_shareholder` (repeat for each member)
7. `formation_set_registered_agent`
8. `formation_set_authorized_party`

### Step 5 — Certificate Review (HARD GATE)
Call `formation_generate_certificate`. Present the PDF URL to the user. Do not proceed until the user explicitly approves.

> "Certificate generated: [PDF URL]. Review it carefully — this will be filed with the Delaware Secretary of State and cannot be undone. Proceed with filing?"

### Step 6 — File
On user approval, call `formation_approve_certificate`.

---

## Skill

**Location:** `~/.claude/skills/llc-formation.md`  
**Trigger:** user says "form an LLC", "start a company", "file an LLC", "create a Delaware LLC"

The skill teaches the model:
- The 14 tool names and their exact required fields
- The mandatory hard gate before `formation_approve_certificate`
- Auth flow (check first, guide through browser login if needed)
- Error handling: name unavailable → ask for alternative

---

## Constraints

- Delaware only (Lovie limitation)
- Real filing costs ~$90 (state fees)
- `formation_approve_certificate` is irreversible — the hard gate is non-negotiable
- Browser required for initial auth (not headless)

---

## Deliverables

1. Wire Lovie MCP: `claude mcp add lovie-formation npx @lovie-ai/formation-mcp-server@latest`
2. Auth test + name check test (non-destructive)
3. Full dry-run through `formation_generate_certificate` (stop before approve)
4. Write `~/.claude/skills/llc-formation.md`
5. Sync skill to `~/projects/claude-config`, commit both repos
6. Update `wizard-powers/plan.json` to mark LLC formation complete
