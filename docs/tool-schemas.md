# Lovie Formation MCP — Tool Schemas

Discovered by static analysis of the cached package source at:
`~/.npm/_npx/311503311d2a306d/node_modules/@lovie-ai/formation-mcp-server/dist/`

Package: `@lovie-ai/formation-mcp-server@1.0.20` (marked deprecated on npm as of ~Feb 2025)
MCP server name: `lovie-formation`
Connected via: `npx @lovie-ai/formation-mcp-server@latest` (stdio transport)

---

## Important Discovery: formation_check_name

The task spec assumed `formation_check_name` takes a `name: string` parameter directly. **This is wrong.** The tool takes a `sessionId` and reads the company name from session state. There is no standalone name-check without an active session. See the Auth section for which tools require auth.

---

## Authentication Model

Tools are split into PUBLIC (no auth required) and PROTECTED (auth required).

### Public tools (no auth needed)
- `formation_login`
- `formation_set_token`
- `formation_auth_status`
- `formation_logout`
- `formation_get_info`
- `formation_list_info_topics`

### Protected tools (require auth via formation_set_token)
All other tools. If called without auth, they return:
```json
{
  "error": true,
  "code": "AUTH_REQUIRED",
  "message": "Authentication required. Please login first using formation_login, then set your token with formation_set_token.",
  "hint": "Call formation_login to open the Lovie dashboard, copy your token, then call formation_set_token with the token."
}
```

Auth token is stored in memory only (per MCP process lifetime), persisted for 7 days by the server's own clock. The underlying JWT (Clerk token) expires quickly (~60s) but the server ignores that.

---

## Auth Tools

### formation_auth_status
No input required.

**Response shape (unauthenticated):**
```json
{
  "authenticated": false,
  "message": "Not logged in. Use formation_login to authenticate."
}
```

**Response shape (authenticated):**
```json
{
  "authenticated": true,
  "userId": "user_...",
  "expiresAt": "2026-06-13T00:00:00.000Z",
  "daysRemaining": 7,
  "message": "Authenticated and session is valid. 7 day(s) remaining."
}
```

**Response shape (session expired):**
```json
{
  "authenticated": false,
  "message": "Session expired (7 days). Use formation_login to authenticate again."
}
```

---

### formation_login
No input required. Opens browser to `https://lovie-web.vercel.app/dashboard`.

**Response shape:**
```json
{
  "success": true,
  "action": "browser_opened",
  "url": "https://lovie-web.vercel.app/dashboard",
  "instructions": ["1. A browser window has been opened...", "..."],
  "nextStep": "After copying both values, call formation_set_token with your token and userId."
}
```

---

### formation_set_token
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `token` | string | yes | Must start with `"eyJ"` (JWT) |
| `userId` | string | yes | Must start with `"user_"` |

**Response shape (success):**
```json
{
  "success": true,
  "authenticated": true,
  "userId": "user_...",
  "expiresAt": "2026-06-13T00:00:00.000Z",
  "daysUntilExpiry": 7,
  "message": "Successfully authenticated as user_...! Your session will remain active for 7 days."
}
```

---

### formation_logout
No input required.

**Response shape:**
```json
{
  "success": true,
  "wasLoggedIn": true,
  "message": "Successfully logged out. Use formation_login to authenticate again."
}
```

---

## Info Tools (public, no auth)

### formation_list_info_topics
No input required.

**Response shape:**
```json
{
  "topics": [
    { "topic": "guide", "name": "Formation Guide", "description": "Step-by-step guide for Delaware company formation process" },
    { "topic": "pricing", "name": "Pricing Information", "description": "Delaware filing fees and service costs" },
    { "topic": "company-types", "name": "Company Types", "description": "Detailed comparison of LLC, C-Corp, and S-Corp" },
    { "topic": "faq", "name": "FAQ", "description": "Frequently asked questions about company formation" },
    { "topic": "requirements", "name": "Requirements", "description": "Required information for Delaware company formation" },
    { "topic": "incorporation-process", "name": "Incorporation Process", "description": "How our legal team incorporates your company and transfers ownership to you" }
  ],
  "usage": "Call formation_get_info with a topic to get detailed information."
}
```

**Valid topic values:** `guide`, `pricing`, `company-types`, `faq`, `requirements`, `incorporation-process`

---

### formation_get_info
| Field | Type | Required | Enum values |
|-------|------|----------|-------------|
| `topic` | string | yes | `guide`, `pricing`, `company-types`, `faq`, `requirements`, `incorporation-process` |

**Response shape:**
```json
{
  "topic": "guide",
  "title": "Formation Guide",
  "description": "Step-by-step guide for Delaware company formation process",
  "content": "# Lovie - Delaware Company Formation Guide\n\n..."
}
```

Content is inline markdown text (not a URL). Topics and their content are hardcoded in the server source — no network call is made.

---

## Session Tools (require auth)

### formation_start
No input required (auth is checked but session creation happens regardless, userId from auth is stored in session).

**Response shape:**
```json
{
  "sessionId": "<uuid>",
  "userId": "user_... or null",
  "firstQuestion": {
    "prompt": "Tell me about your business",
    "description": "...",
    "examples": ["..."]
  },
  "message": "Formation session started. Please ask the user to describe their business using formation_describe_business.",
  "nextStep": "formation_describe_business"
}
```

---

### formation_describe_business
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | From formation_start |
| `businessDescription` | string | yes | Min 10 chars |

**Response shape:**
```json
{
  "success": true,
  "businessDescription": "...",
  "recommendation": {
    "suggestedType": "LLC",
    "reason": "...",
    "alternativeNote": "..."
  },
  "availableStates": [
    { "code": "DE", "name": "Delaware", "companyTypes": ["LLC", "C-Corp"], "description": "..." },
    { "code": "WY", "name": "Wyoming", "companyTypes": ["LLC"], "description": "..." }
  ],
  "message": "...",
  "nextStep": "formation_set_state"
}
```

---

### formation_get_status
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

**Response shape:**
```json
{
  "sessionId": "...",
  "userId": "...",
  "status": "created|in_progress|review|completed|abandoned|expired",
  "currentStep": "created|business_described|state_selected|type_selected|ending_selected|name_set|name_checked|company_address_set|agent_set|shares_set|shareholders_added|authorized_party_set|certificate_generated|certificate_approved|completed",
  "progress": {
    "completedSteps": [...],
    "remainingSteps": [...],
    "percentComplete": 0
  },
  "data": {
    "companyDetails": { ... },
    "registeredAgent": { ... },
    "shareStructure": { ... },
    "shareholders": [ ... ],
    "authorizedParty": { ... },
    "nameCheckResult": { ... },
    "certificateData": { ... }
  },
  "createdAt": "...",
  "updatedAt": "..."
}
```

---

### formation_resume
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

Returns session data plus `nextAction` (tool name to call next) and `nextActionDescription`. Shape similar to `formation_get_status` with added fields.

---

## Company Tools (require auth)

### formation_set_state
| Field | Type | Required | Enum |
|-------|------|----------|------|
| `sessionId` | string | yes | — |
| `state` | string | yes | `DE`, `WY` |

- Delaware supports LLC and C-Corp
- Wyoming supports LLC only

**Response shape:**
```json
{
  "success": true,
  "state": "DE",
  "stateDescription": "Delaware - Premier business jurisdiction...",
  "companyTypes": [
    { "value": "LLC", "name": "Limited Liability Company", "description": "..." },
    { "value": "C-Corp", "name": "C Corporation", "description": "..." }
  ],
  "recommendation": { "type": "LLC", "reason": "..." },
  "message": "..."
}
```

---

### formation_set_company_type
| Field | Type | Required | Enum |
|-------|------|----------|------|
| `sessionId` | string | yes | — |
| `companyType` | string | yes | `LLC`, `C-Corp` |

**Response includes:** `entityEndings` array, `upgradeNote` (LLC→C-Corp upgrade offer), `incorporationProcess` (DE only), `confirmationRequired: true`.

Entity endings by company type:
- LLC: `["LLC", "L.L.C.", "Limited Liability Company"]`
- C-Corp: `["Inc.", "Incorporated", "Corp.", "Corporation", "Company", "Co.", "Limited", "Ltd."]`

---

### formation_set_entity_ending
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `entityEnding` | string | yes | Must match valid endings for chosen company type |

---

### formation_set_company_name
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `baseName` | string | yes | Min 3, max 200 chars. Full name = `baseName + " " + entityEnding` (max 245 chars total) |

**Response:**
```json
{
  "success": true,
  "baseName": "Zarknox Consulting",
  "fullName": "Zarknox Consulting LLC",
  "message": "Company name set to \"Zarknox Consulting LLC\"."
}
```

---

### formation_check_name
**IMPORTANT: Does NOT take a name string directly. Takes sessionId only.**
The company name must already be set via `formation_set_company_name` before calling this.

| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

Calls an external NameCheckAgent against Delaware SoS. Can time out (60s max).

**Response shape (available):**
```json
{
  "available": true,
  "companyName": "Zarknox Consulting LLC",
  "reason": "...",
  "suggestions": [],
  "checkedAt": "2026-06-06T12:00:00.000Z"
}
```

**Response shape (unavailable):**
```json
{
  "available": false,
  "companyName": "Apple LLC",
  "reason": "...",
  "suggestions": ["Apple Technologies LLC", "Apple Holdings LLC"],
  "checkedAt": "2026-06-06T12:00:00.000Z"
}
```

**Response shape (timeout):**
```json
{
  "available": false,
  "companyName": "...",
  "error": "API_TIMEOUT",
  "message": "Name check timed out...",
  "canContinue": true,
  "continueMessage": "You can still proceed...",
  "nextStep": "Continue with formation_set_registered_agent to proceed."
}
```

**Response shape (other error):**
```json
{
  "available": false,
  "companyName": "...",
  "error": "NAME_CHECK_FAILED",
  "message": "Name check failed: ...",
  "canContinue": true,
  "continueMessage": "...",
  "nextStep": "..."
}
```

---

### formation_set_company_address
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `source` | string | yes | `own` or `need_assistance` |
| `virtualPostMailInterested` | boolean | no | Flag for VPM partnership interest |
| `address` | object | conditionally | Required if `source === "own"` |
| `address.street1` | string | yes (if own) | — |
| `address.street2` | string | no | — |
| `address.city` | string | yes (if own) | — |
| `address.state` | string | yes (if own) | State code, e.g. `CA` |
| `address.zipCode` | string | yes (if own) | — |
| `address.country` | string | no | Default: `US` |

If `source` is missing/invalid, returns a prompt asking the user to choose (does not error hard).

---

## Stakeholder Tools (require auth)

### formation_set_registered_agent
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `useDefault` | boolean | yes | `true` = use Northwest Registered Agent (first year free) |
| `agent` | object | conditionally | Required if `useDefault === false` |
| `agent.name` | string | yes (if custom) | — |
| `agent.email` | string | yes (if custom) | format: email |
| `agent.phone` | string | yes (if custom) | — |
| `agent.address.street1` | string | yes (if custom) | — |
| `agent.address.city` | string | yes (if custom) | — |
| `agent.address.state` | string | yes (if custom) | Must be `DE` for Delaware |
| `agent.address.zipCode` | string | yes (if custom) | — |
| `agent.address.street2` | string | no | — |
| `agent.address.county` | string | no | — |

**Default agent (when useDefault=true):**
```json
{
  "isDefault": true,
  "name": "Northwest Registered Agent",
  "email": "support@northwestregisteredagent.com",
  "phone": "1-509-768-2249",
  "address": {
    "street1": "8 The Green, Suite A",
    "city": "Dover",
    "state": "DE",
    "zipCode": "19901",
    "county": "Kent"
  }
}
```

---

### formation_set_share_structure
Only applicable for C-Corp (returns early with success message for LLC).

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `useDefault` | boolean | no | Default `true`. Uses 10M shares @ $0.00001 par |
| `authorizedShares` | integer | conditionally | Required if useDefault=false. Range: 1–1,000,000,000 |
| `parValuePerShare` | number | conditionally | Required if useDefault=false. Range: 0–1000 |

**Default share structure:**
```json
{
  "isDefault": true,
  "authorizedShares": 10000000,
  "parValuePerShare": 0.00001
}
```

Response includes capital funding requirement explanation (total par value must be transferred to company bank account after formation).

---

### formation_add_shareholder
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `shareholder.firstName` | string | yes | Min 1 char |
| `shareholder.lastName` | string | yes | Min 1 char |
| `shareholder.email` | string | yes | format: email |
| `shareholder.phone` | string | no | e.g. `+1-555-123-4567` |
| `shareholder.ownershipPercentage` | number | yes | 0.01–100 |
| `shareholder.role` | string | no | Enum: `member`, `managing_member`, `shareholder`, `director`, `officer`. Defaults to `member` (LLC) or `shareholder` (Corp) |
| `shareholder.address.street1` | string | yes | — |
| `shareholder.address.city` | string | yes | — |
| `shareholder.address.state` | string | yes | State code |
| `shareholder.address.zipCode` | string | yes | — |
| `shareholder.address.street2` | string | no | — |
| `shareholder.address.country` | string | no | Default: `US` |

Can be called multiple times. Total ownership must sum to 100% before submitting.

---

### formation_set_authorized_party
| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `sessionId` | string | yes | — |
| `name` | string | yes | Full legal name |
| `title` | string | yes | e.g. `Managing Member`, `President` |

---

## Certificate Tools (require auth)

### formation_generate_certificate
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

Requires: fullName, registeredAgent, shareholders (≥1), authorizedParty all set.
Calls external certificate API. Returns S3 download URL (expires in ~60 minutes).

**Response shape:**
```json
{
  "success": true,
  "certificateId": "...",
  "downloadUrl": "https://s3.amazonaws.com/...",
  "documentType": "Certificate of Formation",
  "companyType": "llc",
  "expiresAt": "...",
  "minutesRemaining": 58,
  "certificateReviewRequired": {
    "title": "Certificate of Formation Generated",
    "action": "...",
    "url": "...",
    "displayMessage": "..."
  },
  "confirmationRequired": true,
  "confirmationMessage": "...",
  "instructions": "..."
}
```

---

### formation_approve_certificate
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

Requires certificate to be generated and not expired. Marks session COMPLETED and triggers next steps.

---

## Submission Tools (require auth)

### formation_submit
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

POSTs to `https://lovie-formation-agent-api-production.up.railway.app/api/submissions/formation`.
Requires: userId, fullName, state, companyType, companyAddress, shareholders (≥1, summing to 100%), registeredAgent, authorizedParty.

**Success response:**
```json
{
  "success": true,
  "message": "Formation request submitted successfully!",
  "submission": {
    "id": "...",
    "sessionId": "...",
    "userId": "...",
    "status": "PENDING_REVIEW",
    "companyName": "...",
    "entityType": "LLC",
    "stateOfFormation": "DE",
    "submittedAt": "..."
  },
  "nextSteps": ["..."]
}
```

---

### formation_check_submission_status
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

GETs from the backend API. Submission status values: `PENDING_REVIEW`, `IN_REVIEW`, `FILING`, `COMPLETED`, `ERROR`.

---

## Sync Tool (require auth)

### formation_sync
| Field | Type | Required |
|-------|------|----------|
| `sessionId` | string | yes |

Currently a no-op — returns success without actually syncing to external backend.

---

## Formation Workflow State Machine

Steps (in order):
1. `created` → formation_start
2. `business_described` → formation_describe_business
3. `state_selected` → formation_set_state
4. `type_selected` → formation_set_company_type
5. `ending_selected` → formation_set_entity_ending
6. `name_set` → formation_set_company_name
7. `name_checked` → formation_check_name (optional)
8. `company_address_set` → formation_set_company_address
9. `agent_set` → formation_set_registered_agent
10. `shares_set` → formation_set_share_structure (C-Corp only)
11. `shareholders_added` → formation_add_shareholder (repeatable)
12. `authorized_party_set` → formation_set_authorized_party
13. `certificate_generated` → formation_generate_certificate
14. `certificate_approved` → formation_approve_certificate
15. `completed` → formation_submit → formation_check_submission_status

Session status values: `created`, `in_progress`, `review`, `completed`, `abandoned`, `expired`

---

## Key Enum Reference

### States
| Code | Name | Supports |
|------|------|----------|
| `DE` | Delaware | LLC, C-Corp |
| `WY` | Wyoming | LLC only |

### Company Types
| Value | Full Name |
|-------|-----------|
| `LLC` | Limited Liability Company |
| `C-Corp` | C Corporation |

### Entity Endings
| Company Type | Valid Endings |
|-------------|--------------|
| LLC | `LLC`, `L.L.C.`, `Limited Liability Company` |
| C-Corp | `Inc.`, `Incorporated`, `Corp.`, `Corporation`, `Company`, `Co.`, `Limited`, `Ltd.` |

### Shareholder Roles
`member`, `managing_member`, `shareholder`, `director`, `officer`

### Info Topics
`guide`, `pricing`, `company-types`, `faq`, `requirements`, `incorporation-process`

---

## Notable Behaviors for Skill Authors

1. **formation_check_name takes sessionId, not a name string.** Name must be set first via formation_set_company_name.
2. **auth is in-memory per MCP process.** If the server restarts (e.g. npx re-runs), the user must re-authenticate.
3. **Certificate URL expires in ~60 minutes.** If expired, re-generate.
4. **formation_set_company_address** with an invalid/missing `source` returns a prompt object (not an error). Handle the `askUser: true` response.
5. **formation_set_registered_agent** with undefined `useDefault` also returns a prompt, not an error.
6. **Ownership percentages must sum to exactly 100%** at submission time (tolerance: ±0.01).
7. **The package is marked deprecated on npm** but the server is still functional (last published Feb 2025).
8. **Backend API base:** `https://lovie-formation-agent-api-production.up.railway.app`
9. **Dashboard URL:** `https://lovie-web.vercel.app/dashboard`
