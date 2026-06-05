# Wizard Power Skill Anatomy

**This is the Phase 3 deliverable.** See `development-process.md` for the full lifecycle.

A framework for speccing out any wizard power and grading its readiness for a Claude skill.

---

## The 8 Dimensions

Every wizard power skill must define all eight. Missing any one means the skill isn't ready to ship.

---

### 1. Trigger

Natural language phrases that should activate this skill.

**Physical mail example:**
- "send [name] a letter to [address]"
- "mail something to [person]"
- "send a postcard to [address]"

---

### 2. Provider

Which API(s) can fulfill this action. Include pricing so the confirmation gate is honest.

**Physical mail example:**

| Provider | Price/letter | Sandbox | Notes |
|----------|-------------|---------|-------|
| Lob | ~$0.87 | Yes | Best developer DX, address verification included |
| PostGrid | ~$0.90 | Yes | Better bulk pricing |

---

### 3. Auth

What credentials are needed and how they're stored.

**Physical mail example:**
- `LOB_API_KEY` — env var
- No OAuth needed — API key only

---

### 4. Inputs

What to collect from the user before executing. Mark each as required or optional.

**Physical mail example:**

| Input | Required | Notes |
|-------|----------|-------|
| Recipient name | Yes | |
| Recipient address | Yes | Will run address verification before sending |
| Content (letter body) | Yes | Plain text or HTML |
| Mail type | No | Default: letter. Options: letter, postcard |
| Return address | No | Default: user's address from config |
| Delivery speed | No | Default: standard |

---

### 5. Confirmation Gate

What to show the user before executing. This is non-negotiable for any action with real-world cost or irreversibility.

**Physical mail example:**
```
To:      Jane Smith, 123 Main St, Austin TX 78701
From:    Your Name, [return address]
Type:    Letter (1 page)
Cost:    ~$0.87
Delivery: 3–5 business days

Proceed?
```

---

### 6. Reversibility

Can this be undone? If so, how and for how long?

**Physical mail example:**
- Lob: can cancel via API until item enters printing queue (~1–4 hours after submission)
- After that: irreversible — piece is physically printed and queued for USPS

Skill behavior: expose a `cancel_mail <id>` command and surface the cancellation window in the receipt.

---

### 7. Receipt

What to return on success so the user has a record and can follow up.

**Physical mail example:**
```
Sent ✓
ID:       ltr_abc123
Expected: June 10–12
Tracking: [link if available]
Cancel by: June 5, 5:00 PM (within 4 hours)
```

---

### 8. Failure Modes

Common errors and how the skill should handle each.

**Physical mail example:**

| Error | Cause | Handling |
|-------|-------|---------|
| Invalid address | Address doesn't pass USPS verification | Surface suggested corrections, ask user to confirm or edit |
| Content too long | Exceeds 1-page limit | Tell user, offer to split into multiple letters |
| Billing failure | API key has no credits | Surface error with link to add funds |
| Cancelled too late | Piece already in print queue | Tell user it can't be stopped |

---

## Readiness Score

A skill scores 1 point per dimension. Ship at 8/8.

| # | Dimension | Scored |
|---|-----------|--------|
| 1 | Trigger defined | |
| 2 | Provider chosen, pricing documented | |
| 3 | Auth pattern defined | |
| 4 | All inputs mapped (required vs optional) | |
| 5 | Confirmation gate designed | |
| 6 | Reversibility window documented | |
| 7 | Receipt/output defined | |
| 8 | Failure modes handled | |

**Score: /8**

---

## Compliance Notes (optional 9th dimension)

Anything legally relevant that the skill needs to respect or surface.

**Physical mail example:**
- USPS prohibits certain content (hazardous, obscene, fraudulent)
- Lob's ToS prohibits sending unsolicited commercial mail at scale
- No legal weight — this is not certified mail unless explicitly requested via registered mail option

---

## Template

Copy this block to spec a new wizard power:

```markdown
## [Skill Name]

**Trigger:**

**Provider:**

**Auth:**

**Inputs:**

**Confirmation Gate:**

**Reversibility:**

**Receipt:**

**Failure Modes:**

**Compliance Notes:**

**Score: /8**
```
