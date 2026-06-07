# LLC Formation Wizard Power

Forms real Delaware or Wyoming LLCs (and Delaware C-Corps) via [Lovie](https://lovie.co) MCP.

## How It Works

The `llc-formation` skill guides Claude through Lovie's formation MCP server:
auth → business description → entity setup (state, type, name, address, agent, shareholders) → certificate review → filing.

## Supported Entity Types

- Delaware LLC
- Delaware C-Corp
- Wyoming LLC

## Requirements & Blockers

| Requirement | Status | How to Unblock |
|-------------|--------|----------------|
| Lovie account | ⬜ Needed | Free sign-up at https://lovie-web.vercel.app/dashboard |
| Browser login (one-time per MCP process) | ⬜ Needed | `formation_login` opens browser; copy token + userId from dashboard |
| lovie-formation MCP wired | ✅ Done | `claude mcp add --scope user lovie-formation npx @lovie-ai/formation-mcp-server@latest` |

## Known Gotchas

1. **`formation_set_token` requires BOTH `token` AND `userId`** — not just the token.
2. **Auth is in-memory per MCP process** — must re-authenticate every new Claude session.
3. **`formation_check_name` takes `sessionId` ONLY** — the name must be set first via `formation_set_company_name`.
4. **`formation_describe_business` must come before `formation_set_state`** — server enforces step order.
5. **`formation_set_company_address` is required** — cannot skip even with `source: "need_assistance"`.
6. **Certificate `downloadUrl` expires in ~60 minutes** — regenerate if expired.
7. **`formation_check_name` can time out** — `canContinue: true` means proceed anyway.
8. **For LLC, still call `formation_set_share_structure`** — no-op for LLC but state machine may require it.
9. **Total ownership must equal exactly 100%** (±0.01 tolerance) before submission.
10. **Wyoming supports LLC only** — C-Corp requires Delaware.
11. **Package is marked deprecated on npm** (as of Feb 2025) but the server is still functional.
12. **Backend API:** `https://lovie-formation-agent-api-production.up.railway.app` — formation_submit POSTs there.

## Cost

| Item | Cost |
|------|------|
| Lovie service | Free |
| Delaware state filing (LLC) | ~$90 |
| Delaware state filing (C-Corp) | ~$89+ |
| Wyoming state filing (LLC) | Varies |
| Expedited (24hr) | +$50 |
| Same-day | +$100 |

## Setup

```bash
claude mcp add --scope user lovie-formation npx @lovie-ai/formation-mcp-server@latest
```

Then start a session — the `llc-formation` skill guides through browser login (one-time auth per MCP process).

## Schema Reference

Full tool schemas with exact field names and response shapes: `../docs/tool-schemas.md`
