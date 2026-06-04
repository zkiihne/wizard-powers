# Wizard Power Entry Template

---

## [Action Name]
> One sentence: what physically happens in the world when this runs.

**Impact level:** Low / Medium / High  
**Reversible:** Yes / No  
**Requires human in the loop:** Yes / No

---

### Options

| Provider | API Key | Cost Model | Per-Use Cost | Coverage | MCP Available | Notes |
|----------|---------|------------|--------------|----------|---------------|-------|
| Name | Yes/No | Per use / Subscription / Free | ~$X | US / International | Yes/No | Any gotchas |

---

### Requirements to activate
- [ ] Account signup
- [ ] API key
- [ ] Billing setup
- [ ] Compliance / legal requirement (e.g. FCRA consent, notary credential)
- [ ] Other (e.g. minimum volume, whitelisting, KYC)

---

### Agent notes
What the agent needs to know to call this reliably — required fields, gotchas, failure modes.

---

## Example: Send a Physical Letter

> A real paper letter is printed, stuffed, stamped, and mailed to any US address — arrives in 3-5 days.

**Impact level:** Medium  
**Reversible:** No — once mailed, it's gone  
**Requires human in the loop:** No

---

### Options

| Provider | API Key | Cost Model | Per-Use Cost | Coverage | MCP Available | Notes |
|----------|---------|------------|--------------|----------|---------------|-------|
| [PostGrid](https://postgrid.com) | Yes | Per mail piece | ~$0.75–$1.20/letter | US, CA, international | No | Address validation included. Certified mail available. |
| [Lob](https://lob.com) | Yes | Per mail piece | ~$0.80–$1.50/letter | US + international | No | Industry standard. Strong address verification. Test mode available. |
| [LettrLabs](https://lettrlabs.com) | Yes | Per mail piece | ~$2–$5/card | US | No | Robotic pen — looks genuinely handwritten. Higher emotional impact. |
| [Click2Mail](https://click2mail.com) | Yes | Per mail piece | ~$0.60–$0.90/letter | US | No | Cheapest. Next-day printing. Less polished API. |

---

### Requirements to activate
- [ ] Account signup at chosen provider
- [ ] API key
- [ ] Billing/payment method on file
- [ ] Valid sender address
- [ ] Content must comply with mail regulations (no threats, no illegal content)

---

### Agent notes
- Always validate the destination address before sending — most providers charge even if undeliverable
- Certified/tracked mail costs more (~$5–8) but gives delivery confirmation
- PDF or HTML content; most providers render HTML to print-ready PDF
- Test mode lets you preview without spending money
