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
| Lob account | **NEEDED** | Sign up free at lob.com (no credit card) |
| `LOB_TEST_API_KEY` | **NEEDED** | lob.com → Dashboard → Settings → API Keys → `test_...` key |
| `LOB_LIVE_API_KEY` | Optional | Same location — `live_...` key. Only needed for real sends |
| npx in PATH | Assumed OK | Ships with Node.js — verify: `npx --version` |

Nothing works until `LOB_TEST_API_KEY` is set. Test mode is free and sends no real mail.

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
