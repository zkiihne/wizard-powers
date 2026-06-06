# Physical Mail Wizard Power

Sends real physical mail via [lob-mcp](https://github.com/optimize-overseas/lob-mcp) → [Lob API](https://lob.com) → USPS.

## How It Works

The `mail` skill (`~/.claude/skills/mail.md`) guides Claude through the lob-mcp tool flow:
address validation → preview (proof PDF + confirmation token) → commit.

## Supported Actions

- Demand letter
- Legal notice (certified mail)
- Postcard (thank-you, outreach)
- Physical invoice
- Cease & desist

## Requirements & Blockers

| Requirement | Status | How to Unblock |
|-------------|--------|----------------|
| Lob account | ✅ Done | Sign up free at lob.com (no credit card) |
| `LOB_TEST_API_KEY` | ✅ Done | lob.com → Dashboard → Settings → API Keys → `test_...` key |
| lob-mcp wired | ✅ Done | `claude mcp add lob ...` — see Setup below |
| `LOB_LIVE_API_KEY` | Optional | Same location — `live_...` key. Only needed for real sends |
| npx in PATH | ✅ OK | Ships with Node.js |

## Known Gotchas

- `use_type` is required on every mail piece (`"operational"` for letters/invoices, `"marketing"` for postcards/outreach) — no default is set on the account
- Proof PDF URL is `null` in test mode (layout is still validated)
- Commit payload must exactly match preview payload for the confirmation token to be accepted in live mode

## Setup

Once you have the test key:

```bash
claude mcp add lob \
  --env LOB_TEST_API_KEY=test_YOUR_KEY \
  --env LOB_LIVE_MODE=false \
  --env LOB_MAX_PIECES_PER_RUN=10 \
  -- npx -y lob-mcp
```

Then: `"Send a demand letter to Jane Smith at 123 Main St, Brooklyn NY for $850 owed for web design"`

To enable real mail, add `--env LOB_LIVE_API_KEY=live_YOUR_KEY --env LOB_LIVE_MODE=true`.

## Cost Reference

| Type | ~Cost |
|------|-------|
| Letter (first class) | ~$1.50 |
| Letter (certified) | ~$7.00 |
| Postcard (4x6) | ~$0.85 |
