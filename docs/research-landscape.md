# Wizard Powers — Real-World API Landscape

**Research date:** 2026-06-04  
**Status:** Draft — first pass, not exhaustive

The goal: identify every category where an AI agent can trigger a real-world, irreversible, or physically meaningful outcome purely through an API call.

---

## Tier 1 — High Impact, Proven APIs

These are well-documented, production-ready, and high-stakes. An agent with access to these can do things most people hire humans for.

### 1. Business Formation
Form a legal LLC or corporation in any US state, programmatically.

| Provider | Notes |
|----------|-------|
| [FileForms](https://fileforms.com/business-formation-api) | API-first, all 50 states, no volume minimum. Also handles EINs, registered agent, foreign qualifications. Best for solo/small scale. |
| [doola](https://www.doola.com/business-solutions/company-formation-api/) | $297/company. Also handles C Corps. Whitelabel-friendly. |
| [CorpNet](https://www.corpnet.com/corpnet-api/) | Handles all entity types including nonprofits. |
| [MyCompanyWorks EntityMachine](https://www.mycompanyworks.com/entitymachine/entity-formation-api) | 50+ orders/mo minimum. |

**What an agent can do:** File an LLC, get an EIN, appoint a registered agent — entirely autonomously.

---

### 2. Physical Mail
Send real paper letters, postcards, certified mail — delivered to a physical address.

| Provider | Notes |
|----------|-------|
| [PostGrid](https://www.postgrid.com/direct-mail-api/) | Letters, postcards, checks, self-mailers. US + Canada + international. Address validation + tracking. |
| [Lob](https://www.lob.com/blog/what-is-a-physical-mail-api-and-how-does-it-work) | Industry standard. Strong address verification. |
| [LettrLabs](https://www.lettrlabs.com/post/direct-mail-api) | Handwritten cards. Higher emotional impact. |
| [Click2Mail](https://click2mail.com/by-service) | Budget-friendly. Next-day printing. |

**What an agent can do:** Send a demand letter, a birthday card, a legal notice, a physical invoice — to any address in the country.

---

### 3. Electronic Signatures
Have real people sign legally binding documents, initiated programmatically.

| Provider | Notes |
|----------|-------|
| [DocuSign eSign API](https://developers.docusign.com/docs/esign-rest-api/) | Industry standard. $50-480/mo. Bulk sending, template population, field placement. |
| [Dropbox Sign (HelloSign)](https://sign.dropbox.com/products/dropbox-sign-api) | Cleaner DX. $75/mo for 50 requests. Free tier available. |

**What an agent can do:** Generate a contract from a template, send it to any email, collect legally binding signatures.

---

### 4. Remote Notarization (RON)
Notarize documents remotely via audio-visual session. Legal in 45 US states + DC.

| Provider | Notes |
|----------|-------|
| [Notarize](https://www.notarize.com) | Largest. API integrates into CRM/LOS/workflow systems. |
| [Pactima](https://pactima.com/products/ron) | Extensive suite of notarization-specific API endpoints. |
| [BlueNotary](https://bluenotary.us) | High-volume. SOC 2 + HIPAA. |
| [SIGNiX](https://www.signix.com/remote-online-notarization-solution) | Enterprise. |

**What an agent can do:** Trigger a notarization workflow on any document — deed, affidavit, power of attorney.

---

### 5. Payments — ACH, Wire, RTP
Move money between bank accounts programmatically.

| Provider | Notes |
|----------|-------|
| [Dwolla](https://www.dwolla.com/) | ACH mass payouts, marketplace flows, platform payments. |
| [Plaid Transfer](https://plaid.com/products/transfer/) | ACH + RTP + FedNow in one API. |
| [Increase](https://increase.com/) | Banking-grade. ACH + Wires. Single API call to send a wire. |
| [Sila](https://www.silamoney.com/ach-api) | ACH-first. |

**What an agent can do:** Initiate an ACH transfer, send a wire, pay a contractor — all without touching a bank portal.

---

### 6. Bank Account Opening
Open a real bank account programmatically (for embedded finance / fintech platforms).

| Provider | Notes |
|----------|-------|
| [Increase](https://increase.com/) | Programmable bank accounts. Instant open. |
| [Column](https://column.com/) | Full banking API. Accounts + payments. |
| [Galileo](https://www.galileo-ft.com/) | Card + account issuance. |

**What an agent can do:** Open a business checking account, issue a debit card, receive ACH deposits.

---

### 7. Tax Form Filing
File 1099s, W-2s, and other IRS information returns programmatically.

| Provider | Notes |
|----------|-------|
| [TaxBandits](https://developer.taxbandits.com/) | 1099, W-2, W-9, 1042-S, 94x, ACA. Clean API. |
| [Tax1099](https://www.tax1099.com/tax1099-api-integration) | Vendor onboarding + informational tax forms. |
| [IRS IRIS A2A](https://boomtax.com/tax-forms/irs-iris-api-integration-guide) | IRS-direct. SOAP/XML. High volume. |

**What an agent can do:** File contractor 1099s at year-end, submit W-2s, handle ACA reporting — entirely programmatically.

---

### 8. Shipping Labels
Generate and purchase real shipping labels. Hand off to FedEx/UPS/USPS for physical delivery.

| Provider | Notes |
|----------|-------|
| [EasyPost](https://www.easypost.com/) | 100+ carriers. Rate shopping, labels, tracking, insurance, returns. |
| [Shippo](https://goshippo.com/) | Clean API. Multi-carrier. |
| [FedEx Ship API](https://developer.fedex.com/) | Direct. |
| [USPS Domestic Labels API](https://developers.usps.com/apis) | USPS-direct. |

**What an agent can do:** Buy a shipping label, schedule a pickup, ship a package — with zero human touch.

---

### 9. Identity Verification / KYC
Verify a person's identity against government-issued ID documents.

| Provider | Notes |
|----------|-------|
| [Persona](https://docs.withpersona.com/api-introduction) | Inquiry-based. Configurable checks. Government ID + liveness. |
| [Stripe Identity](https://stripe.com/identity) | Selfie + document. Tight Stripe integration. |

**What an agent can do:** Onboard a user, verify their identity for compliance, gate access to financial products.

---

### 10. Insurance Binding
Get a quote and bind real insurance coverage programmatically.

| Provider | Notes |
|----------|-------|
| [CoverForce](https://www.coverforce.com/) | End-to-end: appetite → quote → bind → issuance. Minutes vs weeks. |
| [Bindable](https://bindable.com/api) | Embedded insurance. |
| [SANDIS](https://sandis.io/platform/insurance-api) | Production-ready. Full policy lifecycle via API. Deploys in ~2 weeks. |
| [bolttech](https://bolttech.io/sales/embedded-insurance-api/) | Carrier network. Instant quoting + binding. |

**What an agent can do:** Get a general liability quote and bind coverage for a newly formed LLC — fully automated.

---

### 11. Background Checks
Run FCRA-compliant employment and tenant background screenings via API.

| Provider | Notes |
|----------|-------|
| [Accurate Background](https://www.accurate.com/) | FCRA-compliant API. Criminal, credit, employment history. |
| [GoodHire](https://www.goodhire.com/) | ATS integrations. Automated workflows. |
| [BackgroundChecks.com](https://www.backgroundchecks.com/) | Low-code widgets + full API. Sandbox available. |

**What an agent can do:** Trigger a background check on a job applicant and receive the report programmatically.

---

### 12. Stock / Securities Trading
Buy and sell publicly traded securities programmatically.

| Provider | Notes |
|----------|-------|
| [Alpaca](https://alpaca.markets/) | 11,000+ US stocks/ETFs. Commission-free. **Has an official MCP server.** 24/5 trading. Broker API for client accounts. |

**What an agent can do:** Execute a buy/sell order, manage a portfolio, run an algo strategy — all via API or MCP.

---

## Tier 2 — Medium Impact, Ready APIs

---

### 13. Domain Registration
Register a real domain name programmatically.

| Provider | Notes |
|----------|-------|
| [Namecheap API](https://www.namecheap.com/support/api/intro/) | Search + register + manage. Sandbox available. |
| [GoDaddy API](https://developer.godaddy.com/doc/endpoint/domains) | Availability + registration + DNS management. |
| [Cloudflare Registrar API](https://blog.cloudflare.com/registrar-api-beta/) | Beta. Search + check + register. |

**What an agent can do:** Check availability and register a domain for a new business in seconds.

---

### 14. 3D Printing / On-Demand Manufacturing
Upload a CAD file and have a physical part manufactured and shipped.

| Provider | Notes |
|----------|-------|
| [Slant 3D](https://www.slant3d.com/slant-3d-printing-api) | No API access fees. Pay per part. Digital inventory. |
| [Sculpteo](https://www.sculpteo.com/en/services/api-services/) | Automate upload, configure, order. |
| [Shapeways](https://developers.shapeways.com/) | Free API. 5% per-transaction fee. |

**What an agent can do:** Given a 3D model file, order a physical part to be printed and shipped to any address.

---

### 15. Charitable Donations
Send real money to verified nonprofits programmatically.

| Provider | Notes |
|----------|-------|
| [Every.org](https://www.every.org/charity-api) | Free for non-commercial. Send to any charity. |
| [GlobalGiving](https://www.globalgiving.org/api/) | 9.6M+ validated orgs. 175+ countries. |
| [Change](https://getchange.io/) | Self-serve. Easy integration. |
| [Benevity](https://benevity.com/products/api) | Micro-donation API. Enterprise. |

**What an agent can do:** Donate to a charity on behalf of a user, round up purchases to donate the difference.

---

### 16. Court / Legal Document Filing
File documents with federal and some state courts programmatically.

| Provider | Notes |
|----------|-------|
| [PACER / CM-ECF](https://pacer.uscourts.gov/file-case/developer-resources) | Federal courts. XML-based case opening for bankruptcy. |
| [USLegalPro](https://uslegalpro.com/api) | Third-party API for court e-filing across multiple court systems. |

**What an agent can do:** File a motion, open a bankruptcy case, submit to federal court — programmatically.

---

### 17. Pharmacy / Medication
Submit prescriptions, check pricing, arrange delivery.

| Provider | Notes |
|----------|-------|
| [CloudRx](https://www.cloudrx.co.uk/pharmacy-api) | Submit prescriptions, repeat prescriptions, arrange direct-to-patient delivery. |
| [GoodRx API](https://www.goodrx.com/developer/documentation) | Real-time pricing + discount/coupon lookup across pharmacies. |
| [Walgreens Pharmacy API](https://developer.walgreens.com/) | Refill initiation, transfer, status. |

**What an agent can do:** Look up medication pricing, initiate a refill, arrange home delivery.

---

### 18. IRS / Federal Tax ID
Register for an EIN (via business formation APIs above — IRS has no direct public filing API).

- **FileForms** and **doola** both handle EIN registration as part of LLC formation.
- IRS IRIS A2A handles information return filing at scale (1099s, W-2s) — not entity registration.
- No public direct API to the IRS for EIN applications yet.

---

## Tier 3 — Interesting but Restricted / Partial

These are real categories but either have limited API access, require special authorization, or are harder to automate end-to-end.

### Trademark / Patent Filing (USPTO)
- USPTO has read APIs (TSDR, PTAB, ODP) — great for searching and monitoring.
- **No public API for filing new trademark or patent applications** — must go through Electronic Filing System (EFS-Web / TEAS) with attorney credentials.
- Third-party tools (Anaqua, Docket Alarm) wrap this but aren't simple APIs.

### Real Property Recording / Deed Filing
- Most county recorders in the US do not expose APIs.
- Data retrieval is available (First American, ATTOM, PropMix).
- Some states (e.g., California SOS) have portals but no programmatic filing API.
- Closest option: title companies with API access to their county networks.

### SEC / EDGAR Filing
- EDGAR has excellent **read** APIs (all 10-K/10-Q/8-K data).
- **Submitting** to EDGAR requires special filer credentials + EDGAR Online Forms system — not a simple REST call.

### Voter Registration
- No federal API. State-by-state, most require in-person or mail-based processes.
- Some states (AZ, WA, OR) have online portals but no public API.

### DMV / Vehicle Registration
- No national API. State DMVs are largely not API-accessible.
- Some jurisdictions (CA, TX) have partial online services, but no clean developer API.

---

## Agent Integration Ideas (Backlog)

These are workflows worth building — combining multiple APIs into one wizard-power agent action:

1. **"Launch a business"** — FileForms (LLC) + IRS EIN + PostGrid (mailing address) + Namecheap (domain) + bank account (Column) + insurance (CoverForce)
2. **"Send a legal notice"** — DocuSign (e-sign) + PostGrid (certified mail)
3. **"Hire a contractor"** — DocuSign (contract) + Persona (KYC) + GoodHire (background check) + Dwolla (ACH payment) + TaxBandits (1099 at year-end)
4. **"Ship a product"** — EasyPost (label) + Slant3D (manufacturing) + PostGrid (packing insert)
5. **"Close a simple deal"** — DocuSign (agreement) + Pactima (notarization) + Increase (wire)
6. **"Fund a charity"** — Every.org (donation) + PostGrid (thank-you card)
7. **"Run a trading strategy"** — Alpaca MCP (buy/sell) + TaxBandits (1099-B at year-end)

---

## Open Questions (for next session)

1. Which integration to build first — most bang for the buck?
2. MCP server vs Claude tool use wrappers vs a unified "wizard" API layer?
3. Scope: one polished integration or a broad catalog of thin wrappers?
4. Should each integration be a separate MCP server or one monorepo with multiple tools?
