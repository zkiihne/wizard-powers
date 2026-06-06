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

## Setup

1. Sign up at lob.com (free developer tier, no credit card for test)
2. Get API keys: Dashboard → Settings → API Keys
3. Wire lob-mcp:

```bash
claude mcp add lob \
  --env LOB_TEST_API_KEY=test_YOUR_KEY \
  --env LOB_LIVE_API_KEY=live_YOUR_KEY \
  --env LOB_LIVE_MODE=false \
  --env LOB_MAX_PIECES_PER_RUN=10 \
  -- npx -y lob-mcp
```

4. Ask Claude: `"Send a demand letter to Jane Smith at 123 Main St, Brooklyn NY for $850 owed for web design"`

## Cost Reference

| Type | ~Cost |
|------|-------|
| Letter (first class) | ~$1.50 |
| Letter (certified) | ~$7.00 |
| Postcard (4x6) | ~$0.85 |
