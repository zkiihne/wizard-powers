# Wizard Powers Catalog

One entry per real-world action an AI agent can take via API.
Format: what happens, providers, cost, requirements, caveats.

---

## Legal & Government

### Form a Legal Business Entity (LLC, C-Corp, Nonprofit)

> A legal business entity is incorporated in the chosen US state, generating official formation documents and a state-issued entity ID.

**Providers**
- [FileForms](https://fileforms.com/business-formation-api) — ~$49–99/formation + state fee — API key + billing — all 50 states; API-first, no volume minimum, also handles EINs and registered agents
- [doola](https://www.doola.com/business-solutions/company-formation-api/) — $297/company + state fee — API key + billing — US; strong non-resident support, whitelabel-friendly
- [CorpNet](https://www.corpnet.com/corpnet-api/) — custom/quote — API key + contract — all entity types including nonprofits and PLLCs

**Free tier:** No  
**Compliance required:** No — but state filing fees apply ($50–$500 depending on state)  
**MCP exists:** No  
**Reversible:** Yes — entities can be dissolved, but dissolution is a separate filing

---

### Register a DBA ("Doing Business As") Name

> A fictitious business name is recorded with the county clerk or state, creating a public record linking an individual or entity to a trade name.

**Providers**
- [LegalZoom](https://www.legalzoom.com/business/business-formation/dba-overview.html) — $99 + state fee — account + billing — all 50 states; handles publication requirements
- [ZenBusiness](https://www.zenbusiness.com/pricing-dba/) — $95 + state fee — account + billing — all 50 states; includes registered agent option
- [MyCorporation](https://www.mycorporation.com/business-formations/dba.jsp) — varies — account + billing — all 50 states; bulk-capable

**Free tier:** No  
**Compliance required:** Yes — most states require newspaper publication of the fictitious name (typically 4 consecutive weeks)  
**MCP exists:** No  
**Reversible:** Yes — abandoned via statement of abandonment with the county/state

---

### Register a 501(c)(3) Nonprofit

> The IRS receives Form 1023 or 1023-EZ and, if approved, grants federal tax-exempt status; donations become tax-deductible and the organization is exempt from federal income tax.

**Providers**
- [Harbor Compliance](https://www.harborcompliance.com/501c3-application) — ~$1,899 full service — account + billing — US; covers IRS application + state incorporation + ongoing compliance
- [InstantNonprofit](https://instantnonprofit.com/) — varies — account + billing — US; tech-assisted with human nonprofit specialists
- [IRS Form 1023/1023-EZ direct](https://www.irs.gov/) — $275 (EZ) or $600 (full) IRS user fee — no API; web portal via pay.gov

**Free tier:** No — IRS fees are $275–$600 regardless of channel  
**Compliance required:** Yes — must meet IRC § 501(c)(3) structural requirements; state charitable solicitation registration is a separate ongoing obligation  
**MCP exists:** No  
**Reversible:** No — exempt status can be voluntarily terminated; the legal entity must be formally dissolved

---

### Apply for a Federal EIN

> The IRS issues a 9-digit employer identification number that becomes the entity's permanent federal tax identity, required to hire employees, open business bank accounts, and file most business taxes.

**Providers**
- [IRS EIN Online Application](https://www.irs.gov/businesses/small-businesses-self-employed/apply-for-an-employer-identification-number-ein-online) — free — no API; real-time issuance via web form (M–F 7am–10pm ET); EIN issued instantly
- [FileForms](https://fileforms.com/) — included in formation packages — API + billing — US
- [doola](https://www.doola.com/) — included in formation packages — account + billing — strong non-US-resident support

**Free tier:** Yes — IRS direct application is free  
**Compliance required:** No — responsible party must have a valid SSN/ITIN  
**MCP exists:** No  
**Reversible:** No — an EIN is permanent; the associated account can be closed but the number is never reassigned

---

### Register a Copyright with the US Copyright Office

> A copyright claim is officially recorded with the Library of Congress, creating a public certificate required to sue for statutory damages and attorney's fees in US federal court.

**Providers**
- [US Copyright Office eCO System](https://eservice.eco.loc.gov/) — $45–65/registration — account + credit card — US; web portal only, no public API as of 2026
- Mail filing — $125/claim — paper only

**Free tier:** No — minimum $45 filing fee  
**Compliance required:** No — registration voluntary but required before filing an infringement lawsuit for US works  
**MCP exists:** No  
**Reversible:** No — registrations are permanent public records

---

### File a DMCA Takedown Notice

> A copyright infringement notice is formally delivered to a host, platform, or search engine, legally requiring them to remove or de-index the infringing content within 10–14 days or lose safe harbor protection.

**Providers**
- [DMCA.com](https://www.dmca.com/Takedowns.aspx) — ~$199/takedown or $10/mo unlimited DIY — account + billing — US/international; direct partnerships with major hosts
- [Ceartas](https://www.ceartas.io/) — custom/subscription — API key + billing — US/international; AI-powered scanning with developer API
- [DMCAForce](https://dmcaforce.com/) — ~$150/mo — subscription — US/international; bulk weekly scans + automated notice dispatch

**Free tier:** Yes — DIY notices to platforms cost $0; services charge for managed filing  
**Compliance required:** No — but notice must satisfy 17 U.S.C. § 512(c)(3) or it is legally ineffective  
**MCP exists:** No  
**Reversible:** Yes — counter-notice from the alleged infringer can restore content within 10–14 business days

---

### File a UCC-1 Financing Statement / Mechanic's Lien

> A lien is recorded in the public record of the debtor's state (UCC-1) or county where property is located (mechanic's lien), publicly encumbering collateral and blocking clear title transfer until the debt is resolved.

**Providers**
- [CSC Global](https://www.cscglobal.com/service/business-administration/ucc-services/ucc-filings/) — custom/quote — account + contract — all 50 states; API integration for bulk filers, law firms, and lenders
- [RASi](https://www.rasi.com/en/ucc-lien-services) — custom/quote — account + contract — all 50 states; covers UCC, tax liens, judgment liens, and mechanic's liens
- Direct state portals — $20–40 state fee — no API

**Free tier:** No  
**Compliance required:** Yes — must name the correct debtor exactly per Revised Article 9; mechanic's liens have strict notice deadlines (often 20–90 days from last work)  
**MCP exists:** No  
**Reversible:** Yes — filer submits a UCC-3 termination statement; mechanic's lien requires a formal release or court order

---

### Submit a FOIA Request to a Federal Agency

> A written public records request is submitted to a federal agency, legally obligating the agency to respond within 20 business days and produce non-exempt government records.

**Providers**
- [FOIA.gov Agency API](https://www.foia.gov/developer/agency-api/) — free — API key from api.data.gov; POST endpoint covers 100+ agencies
- [USCIS FOIA API](https://www.uscis.gov/) — free — API key via USCIS; purpose-built for immigration attorneys and case management software
- [MuckRock](https://www.muckrock.com/) — free–$40/mo — account; bulk filing and tracking, no public submission API

**Free tier:** Yes  
**Compliance required:** No — any person may submit  
**MCP exists:** No  
**Reversible:** Yes — requests can be withdrawn before records are produced

---

### Submit a Public Comment on a Proposed Federal Regulation

> A comment is formally entered into the federal rulemaking docket, becoming part of the official public record the agency must consider before finalizing a rule.

**Providers**
- [Regulations.gov API v4](https://open.gsa.gov/api/regulationsgov/) — free — API key from api.data.gov; `POST /v4/comments` covers 200+ agencies

**Free tier:** Yes  
**Compliance required:** No — must be submitted before the docket's comment deadline  
**MCP exists:** No  
**Reversible:** No — submitted comments become permanent public record

---

### Report Suspected Tax Fraud to the IRS

> A tip is logged with IRS Criminal Investigation, which may trigger a review or audit of the reported individual or business.

**Providers**
- [IRS Online Form 3949-A](https://www.irs.gov/forms-pubs/about-form-3949-a) — free — no API; secure online portal (no developer API)
- [IRS Whistleblower Office Form 211](https://www.irs.gov/compliance/whistleblower-informant-award) — free — for claims over $2M; eligible for 15–30% of proceeds collected

**Free tier:** Yes  
**Compliance required:** No — may be submitted anonymously  
**MCP exists:** No  
**Reversible:** No — once submitted, the referral enters IRS systems with no recall mechanism

---

### File a Whistleblower Complaint with the SEC

> A formal tip is entered into the SEC's Tips, Complaints, and Referrals system, potentially qualifying the submitter for a 10–30% monetary award from any enforcement action exceeding $1M.

**Providers**
- [SEC TCR Online Portal](https://www.sec.gov/submit-tip-or-complaint/tcr-disclaimer) — free — no API; web form only
- [CFTC TCR Portal](https://www.whistleblower.gov/) — free — no API; parallel program for commodities/derivatives fraud

**Free tier:** Yes  
**Compliance required:** Yes — attorney required to claim an award anonymously  
**MCP exists:** No  
**Reversible:** No — submissions are logged; identity can be protected but the tip cannot be recalled

---

### Submit a Complaint to the CFPB

> A formal complaint is entered against a named financial company; the CFPB forwards it to the company (must respond within 15 days) and publishes it in the public Consumer Complaint Database.

**Providers**
- [CFPB Complaint Portal](https://cfpb.gov/complaint) — free — no submission API; web form, phone, or mail only

**Free tier:** Yes  
**Compliance required:** No — complainant must have a commercial relationship with the named company  
**MCP exists:** No  
**Reversible:** Partial — consumers can request removal from the public database; internal CFPB record persists

---

### Place a Statutory Legal Notice in a Newspaper

> A notice is published in a newspaper of record in the required jurisdiction, creating a legally defensible record of constructive public notice (required for LLC formations, foreclosures, probate, name changes, etc.).

**Providers**
- [Column](https://www.column.us/public-notice/pricing) — varies by state/word count — API key + account — all 50 states; bulk/API submission, handles formatting and affidavit of publication
- [DailyDAC](https://www.dailydac.com/) — ~$990 first week, $330/subsequent — account — digital-first, accepted in most jurisdictions for insolvency notices
- State press association portals — $20–100/insertion — web form only; no API

**Free tier:** No  
**Compliance required:** Yes — each state defines which newspapers qualify; affidavit of publication is usually required as proof  
**MCP exists:** No  
**Reversible:** No — once published, the notice is a permanent record

---

### Register for a Sales Tax Permit in a US State

> A seller obtains legal authorization from a state to collect and remit sales tax, creating a nexus obligation and a recurring filing requirement.

**Providers**
- [Avalara](https://www.avalara.com/us/en/products/business-licenses/sales-tax-registration.html) — ~$349–403/state — API + account — all 50 states; integrates with AvaTax for ongoing filing
- [TaxJar](https://www.taxjar.com/) — ~$299/state one-time — API key + account — all 50 states; registration bundled with filing automation
- [Galvix](https://www.galvix.com/) — ~$60/state/mo — account — compliance-as-a-service including registration, filing, and notice management

**Free tier:** No — state fees apply  
**Compliance required:** Yes — registration creates a legal obligation to file and remit on schedule  
**MCP exists:** No  
**Reversible:** Yes — permit cancelled by filing a closing request; outstanding returns must still be filed

---

### Apply for a Liquor License

> A state alcoholic beverage control board receives a formal application, triggering a public notice period, background checks, and review that—if approved—grants the legal right to sell alcohol at a specified location.

**Providers**
- No clean API exists for multi-state applications
- [ABC Liquor Consultants](https://abcliquorconsultants.com/) — custom/quote — consulting engagement; human-managed, not API-driven
- State portals (CA ABC, WA LCB, FL DBPR) — $100–$15,000+ state fee — web form only

**Free tier:** No  
**Compliance required:** Yes — background checks, fingerprinting, public notice posting, premises inspection, zoning, and local government sign-off required; timelines range 60 days to 12+ months  
**MCP exists:** No  
**Reversible:** Yes — application can be withdrawn before approval

---

### Apply for a Business License in a Municipality

> A municipality grants legal right to conduct a specified business activity within its jurisdiction; operating without it is a civil or criminal violation.

**Providers**
- No single API covers all 19,000+ US municipalities
- [Harbor Compliance](https://www.harborcompliance.com/) — custom/quote — managed service that files in any US municipality
- [Accela](https://www.accela.com/solutions/business-licensing/) — custom/SaaS (sold to govts) — if a municipality runs Accela, applications can be submitted via its API

**Free tier:** No  
**Compliance required:** Yes — requirements vary by business type and municipality  
**MCP exists:** No  
**Reversible:** Yes — licenses can be voluntarily surrendered

---

### File a Small Claims Court Case

> A civil lawsuit is initiated in a court of limited jurisdiction, legally compelling the named defendant to appear and respond to a monetary claim (typically $2,500–$25,000 depending on state).

**Providers**
- [US Legal Pro](https://uslegalpro.com/api) — ~$4.99–9.99/filing + court fees — REST API — TX, IL, IN, CA, MD, FL; batch-capable
- [One Legal](https://www.onelegal.com/) — service fee + court fees — account — California-focused eFiling
- State self-help portals — free form prep + $30–100 court fee — web only

**Free tier:** No — court filing fees apply in every jurisdiction  
**Compliance required:** No — service of process on the defendant is required after filing  
**MCP exists:** No  
**Reversible:** Yes — plaintiff can file a voluntary dismissal before judgment is entered

---

### E-File a Document in Federal Court

> A legal document is filed with a federal court's electronic docket via CM/ECF, creating an official timestamped court record.

**Providers**
- [US Legal Pro](https://uslegalpro.com/api) — ~$4.99–9.99/filing + court fees — REST API — TX, IL, IN, CA, MD, FL
- [Proceed Legal](https://proceedlegal.com/e-filing/) — service fee + court fees — account — national; integrates with Clio, Filevine, NetDocuments
- [PACER CM/ECF](https://pacer.uscourts.gov/) — $0.10/page — ECF credentials required — federal courts; attorney login required for filing

**Free tier:** No  
**Compliance required:** Yes — filers must be admitted to the relevant court; attorney e-filing requires court-issued credentials  
**MCP exists:** No  
**Reversible:** No — filed documents are permanent court records

---

### Contact Members of Congress with a Constituent Message

> A constituent message is formatted and delivered (via email, fax, or postal mail) to the recipient's official congressional office on behalf of the sender's verified address.

**Providers**
- [Capitol Canary / Quorum](https://capitolcanary.com/) — custom enterprise pricing — API key + contract — US federal + state; multichannel delivery (phone, email, webform, SMS)
- [resistbot/contact-officials](https://github.com/resistbot/contact-officials) — free (open source) — no auth required — US; powers Resistbot's deliveries, usable to build custom delivery tooling

**Free tier:** Yes (open source form definitions are free; Capitol Canary requires a contract)  
**Compliance required:** No — messages must include a valid constituent address  
**MCP exists:** No  
**Reversible:** No — message is delivered to a congressional inbox

---

### File an OSHA Workplace Safety Complaint

> A formal complaint is lodged with OSHA, triggering potential inspection of the named employer.

**Providers**
- [OSHA Online Complaint Form](https://www.osha.gov/form/osha7) — free — no API; web form only
- Note: No public API exists. Closest workaround: browser automation against osha.gov/form/osha7

**Free tier:** Yes  
**Compliance required:** No — but false complaints are unlawful  
**MCP exists:** No  
**Reversible:** No — filed complaint initiates an administrative record; can be withdrawn but not deleted

---

### File an EEOC Discrimination Complaint

> A formal Charge of Employment Discrimination is filed with the EEOC, creating a legal record and starting the agency's investigation and conciliation process.

**Providers**
- [EEOC Public Portal](https://www.eeoc.gov/eeoc-public-portal) — free — no API; intake requires online interview + identity verification
- Note: No public API. Charges must be filed within 180/300 days of discriminatory act

**Free tier:** Yes  
**Compliance required:** Yes — false charges expose filer to legal liability  
**MCP exists:** No  
**Reversible:** No — a filed charge is a federal record; can be withdrawn but EEOC retains it

---

### Bid on a US Government Contract (SAM.gov)

> A formal offer or proposal is submitted to a federal contracting officer in response to a solicitation, entering the acquisition competition.

**Providers**
- [SAM.gov Opportunity Management API](https://open.gsa.gov/api/opportunities-api/) — free — API key (free, up to 10 business days to activate) — US federal; read/write API (primarily for agencies posting solicitations)
- [GovCon API](https://govconapi.com/) — ~$49/mo — API key + billing — US; commercial wrapper over SAM.gov with cleaner endpoints and higher rate limits

**Free tier:** Yes (SAM.gov official APIs are free)  
**Compliance required:** Yes — bidder must be registered in SAM.gov; some contracts require 8(a), HUBZone, or other certifications  
**MCP exists:** No  
**Reversible:** Partial — proposals can be withdrawn before award

---

### Apply for a Federal Grant (Grants.gov)

> A grant application package is submitted to a federal agency for review, making the applicant eligible to receive public funding.

**Providers**
- [Grants.gov RESTful APIs](https://www.grants.gov/api) — free — no auth for search; S2S application submission requires registration — REST APIs launched March 2025 for searching; application submission uses SOAP/XML S2S
- [Simpler Grants API (beta)](https://wiki.simpler.grants.gov/product/api) — free (early access) — API key — next-generation replacement for Grants.gov search

**Free tier:** Yes  
**Compliance required:** Yes — applicants must have a UEI from SAM.gov; some grants require nonprofit status or specific institution type  
**MCP exists:** No  
**Reversible:** No — once submitted, withdrawal must be requested through the grants office

---

## Financial

### Open a Bank Account

> A real, FDIC-insured bank account is opened and funded, capable of sending/receiving ACH, wires, and holding deposits.

**Providers**
- [Increase](https://increase.com/) — no monthly fee; transaction fees apply — API key + compliance review — US; programmable bank accounts, instant open, direct Fed access
- [Column](https://column.com/) — custom/quote — API key + contract — US; full national bank with complete API; accounts + payments + card issuance

**Free tier:** No — transaction fees apply  
**Compliance required:** Yes — KYC/AML required  
**MCP exists:** No  
**Reversible:** Yes — accounts can be closed; closing takes 1–5 business days

---

### Send a Wire Transfer

> Real money moves from one bank account to another via the Fedwire network, typically settling the same business day.

**Providers**
- [Increase](https://increase.com/products/wires) — $25/wire — API key + billing — US domestic; single API call to initiate
- [Column](https://column.com/) — custom pricing — API key + contract — US domestic and international
- [Dwolla](https://www.dwolla.com/) — custom pricing — API key + contract — US domestic

**Free tier:** No  
**Compliance required:** Yes — KYC/AML; OFAC screening required  
**MCP exists:** No  
**Reversible:** No — wires are final; recalls require recipient cooperation and are not guaranteed

---

### Send an ACH Payment

> Money is transferred between US bank accounts via the ACH network, settling in 1–3 business days (same-day ACH available for a premium).

**Providers**
- [Dwolla](https://www.dwolla.com/) — custom pricing — API key + contract — US; mass payouts, marketplace flows
- [Plaid Transfer](https://plaid.com/products/transfer/) — custom pricing — API key + contract — US; ACH + RTP + FedNow in one API
- [Sila](https://www.silamoney.com/ach-api) — custom pricing — API key + contract — US; ACH-first

**Free tier:** No  
**Compliance required:** Yes — account linking and identity verification required; NACHA rules apply  
**MCP exists:** No  
**Reversible:** Partial — ACH returns possible within 2 business days (unauthorized) or 60 days (consumer)

---

### Buy US Treasury Bonds

> A US government bond is purchased and registered in the buyer's name, lending money to the federal government at a fixed interest rate.

**Providers**
- [Alpaca Broker API](https://alpaca.markets/broker) — $0 commission — API key + broker agreement — US; developer-first, supports T-bills and Treasury ETFs
- [Interactive Brokers API](https://interactivebrokers.github.io/) — $0 commission on Treasuries — API key + brokerage account — US/international; full REST/socket API
- [TreasuryDirect](https://www.treasurydirect.gov/) — free — no purchasing API exists; direct purchase requires web portal login only

**Free tier:** Yes (no commission at Alpaca/IBKR)  
**Compliance required:** Yes — brokerage account required; individual use only  
**MCP exists:** Yes (Alpaca has an official MCP server)  
**Reversible:** No — bonds can be sold on secondary market but not cancelled; I-Bonds have a 12-month lock-up

---

### Buy/Sell Stocks, ETFs, and Options

> A real securities order is placed on a US exchange, executing a legally binding purchase or sale of publicly traded financial instruments.

**Providers**
- [Alpaca](https://alpaca.markets/) — commission-free for retail; Broker API has per-trade pricing — API key + account — US; 11,000+ stocks/ETFs/options, 24/5 trading; **official MCP server available**

**Free tier:** Yes — paper trading (simulated) is free  
**Compliance required:** Yes — KYC/AML; pattern day trader rules apply; options require approval tier  
**MCP exists:** Yes — [Alpaca MCP Server](https://github.com/alpacahq/alpaca-mcp-server)  
**Reversible:** Partial — orders can be cancelled before execution; executed trades must be unwound with a new trade

---

### Open a Brokerage / IRA Account

> A regulated securities account (taxable or tax-advantaged) is opened in a person's name, triggering KYC/AML verification, FINRA account records, and IRS reporting obligations.

**Providers**
- [Alpaca Broker API](https://alpaca.markets/broker) — revenue share / custom — API key + broker agreement — US; supports Traditional IRA, Roth IRA, and taxable accounts
- [DriveWealth](https://drivewealth.com/) — custom (% of AUM or per-account) — API + partnership agreement — US and international; powers fractional investing in 150+ countries
- [Apex Fintech Solutions](https://www.apexfintechsolutions.com/) — custom — API + clearing agreement — US; white-label clearing and custody used by major fintechs

**Free tier:** No (sandbox environments available)  
**Compliance required:** Yes — FINRA broker-dealer registration, AML/BSA, PATRIOT Act KYC; IRA accounts require IRS Form 5498 reporting  
**MCP exists:** No  
**Reversible:** No — account opening is irreversible; accounts can be closed and assets transferred via ACATS

---

### Issue a Virtual or Physical Credit Card

> A payment card with a unique PAN, CVV, and expiry is provisioned and tied to a spending account, authorizing the cardholder to make purchases.

**Providers**
- [Stripe Issuing](https://stripe.com/issuing) — $0.10/virtual card; $3.00/physical card — API key + Stripe account — US/UK/EU; instant virtual card provisioning, spend controls, real-time auth hooks
- [Marqeta](https://www.marqeta.com/platform/card-issuing) — ~$0.50/virtual card + 0.5–1% transaction fee — API key + enterprise agreement — US/international; powers Cash App, DoorDash, Instacart
- [Lithic](https://www.lithic.com/) — $0.05–0.10/virtual card; revenue share on spend — API key + account — US; developer-first, no monthly minimum

**Free tier:** No (sandbox yes)  
**Compliance required:** Yes — issuing programs must be sponsored by a bank partner; KYC required on cardholders  
**MCP exists:** No  
**Reversible:** Yes — virtual cards can be terminated instantly via API

---

### Run Payroll

> Employee wages are calculated, taxes withheld, direct deposits initiated, and payroll tax filings prepared — all in one automated run.

**Providers**
- [Gusto Embedded Payroll API](https://embedded.gusto.com/) — $49/mo base + $6/employee (direct); custom for partners — API key + partner agreement — US; developer-first REST API, handles 941, W-2, state filings
- [Rippling](https://www.rippling.com/) — modular pricing; ~$8/employee/mo base — API + OAuth — US/international; payroll as one module in a broader HCM platform
- [ADP Marketplace API](https://marketplace.adp.com/) — ~$79/mo + $4–6/employee — API key + ADP Marketplace agreement — US/international; largest provider

**Free tier:** No  
**Compliance required:** Yes — employer must be registered with IRS (EIN), state unemployment, and state withholding agencies  
**MCP exists:** No  
**Reversible:** Partial — ACH payroll can be reversed within 5 business days if bank accepts recall; tax deposits are not reversible

---

### Pay IRS Estimated Quarterly Taxes

> Federal tax dollars are transferred from a bank account to the US Treasury and credited to a taxpayer's account, satisfying quarterly estimated tax obligations under IRC §6654.

**Providers**
- [EFTPS Batch Provider API](https://www.eftps.gov/) — free — enrollment + PIN + ACH origination — US; businesses submit bulk ACH debit payments programmatically; individual new enrollments closed as of Oct 2025
- [Payroll platforms (Gusto, Rippling, ADP)](https://embedded.gusto.com/) — included in payroll pricing — API — US; payroll APIs handle 941 deposits and estimated taxes as part of payroll runs

**Free tier:** Yes (EFTPS is a free government service)  
**Compliance required:** Yes — payments must be scheduled by 8PM ET the day before due date  
**MCP exists:** No  
**Reversible:** No — tax payments cannot be reversed; errors require IRS amended return or credit forward

---

### File 1099 / W-2 Tax Forms with the IRS

> Information returns are filed with the IRS and state agencies, and copies are delivered to recipients — legally required for contractors paid $600+ and all employees.

**Providers**
- [TaxBandits](https://developer.taxbandits.com/) — ~$1.49–2.99/form — API key + billing — US; 1099-NEC, 1099-MISC, W-2, 1042-S, ACA, 94x; postal mailing of recipient copies available
- [Tax1099](https://www.tax1099.com/tax1099-api-integration) — ~$1.29–2.49/form — API key + billing — US; vendor onboarding + TIN verification included
- [IRS IRIS A2A](https://boomtax.com/tax-forms/irs-iris-api-integration-guide) — free to IRS — SOAP/XML — US; direct IRS channel for high-volume transmitters

**Free tier:** No — per-form fees apply  
**Compliance required:** Yes — mandatory for any business paying contractors $600+ or employing W-2 workers; penalties up to $310/form for late filing  
**MCP exists:** No  
**Reversible:** Yes — corrected forms can be filed; voided forms are accepted by IRS

---

### Freeze or Unfreeze a Credit File

> A security freeze is placed on (or lifted from) a consumer's credit file at one or all three bureaus, preventing new credit accounts from being opened in their name.

**Providers**
- [Equifax Developer API](https://developer.equifax.com/) — custom B2B pricing — API key + FCRA compliance agreement — US; B2B2C Consumer Engagement Suite
- [Experian API Hub](https://developer.experian.com/) — custom — API key + permissible purpose agreement — US
- [TransUnion](https://developer.transunion.com/) — custom — API key + contract — US
- Consumer direct (AnnualCreditReport.com) — free by law — no API; web/phone/mail

**Free tier:** Yes — consumers can freeze for free by law  
**Compliance required:** Yes — programmatic access requires FCRA compliance; third-party access requires consumer consent  
**MCP exists:** No  
**Reversible:** Yes — freezes can be lifted instantly via PIN

---

### Dispute an Item on a Credit Report

> A formal FCRA dispute is filed with a credit bureau, requiring the bureau to investigate the item within 30 days and correct or delete inaccurate information.

**Providers**
- [Experian API Hub](https://developer.experian.com/) — custom enterprise — API key + FCRA data furnisher agreement — US; dispute submission and status check APIs for data furnishers and partners
- [CRS Credit API](https://crscreditapi.com/) — custom — API key — US; unified tri-bureau API with dispute workflow support

**Free tier:** No (for B2B API access)  
**Compliance required:** Yes — FCRA §611 governs dispute rights; Metro 2 format compliance required  
**MCP exists:** No  
**Reversible:** No — a dispute, once filed, triggers a mandatory investigation

---

### Make a Political Campaign Donation

> Funds are transferred to a political committee and reported to the FEC, creating a permanent public contribution record under campaign finance law.

**Providers**
- [ActBlue](https://secure.actblue.com/docs/custom_integrations) — 3.95% processing fee — API key + eligibility approval — US; serves Democratic/progressive campaigns; embeddable forms + custom integrations API
- [WinRed](https://winred.com/) — 3.94% processing fee — API + campaign approval — US; serves Republican campaigns; embed and webhook integration

**Free tier:** No (percentage fee on every transaction)  
**Compliance required:** Yes — FEC contribution limits ($3,300/candidate/election for federal); donor must be US citizen or permanent resident; contributions are public record  
**MCP exists:** No  
**Reversible:** No — political donations are not legally refundable

---

### Fund an Escrow Account

> Money is deposited into a regulated third-party holding account, legally restricted from use until specified contractual conditions are fulfilled.

**Providers**
- [Escrow.com API](https://www.escrow.com/api) — 0.89%–3.25% of transaction value — API key + account — US/international; create transaction, fund, release, cancel programmatically; supports ACH, wire, credit card
- [Stripe Connect manual payouts](https://docs.stripe.com/connect/manual-payouts) — Stripe processing fees (~2.9% + $0.30) — API key — US/international; holds funds in platform balance up to 90 days before payout (not true licensed escrow)

**Free tier:** No  
**Compliance required:** Yes — true escrow agents must be licensed in most US states; Escrow.com is a licensed escrow company  
**MCP exists:** No  
**Reversible:** Yes — transactions can be cancelled before release if both parties agree

---

### Initiate a Chargeback

> A cardholder dispute is filed with the card issuer, which reverses a transaction on the card network, debits the merchant's account, and initiates a formal dispute resolution process.

**Providers**
- [Lithic Disputes API](https://www.lithic.com/) — included in card issuing pricing — API key — US; card issuers can programmatically submit and manage disputes; full lifecycle via REST
- [Stripe Issuing Disputes](https://docs.stripe.com/issuing/purchases/disputes) — included in Stripe Issuing — API key — US/international; cardholders on Stripe-issued cards can dispute via API

**Free tier:** No (requires card issuing relationship)  
**Compliance required:** Yes — governed by Visa/Mastercard network rules; must be filed within valid reason code timeframes (typically 60–120 days)  
**MCP exists:** No  
**Reversible:** Partial — a dispute can be withdrawn before escalation to arbitration

---

### Buy or Exchange Foreign Currency

> Currency is converted at a market or negotiated rate and transferred to a destination account, creating a legally settled FX transaction.

**Providers**
- [Wise Platform API](https://docs.wise.com/api-reference) — ~0.35–0.65% for major pairs + small fixed fee — API key + platform agreement — 80+ countries; mid-market rate, real-time quotes
- [Airwallex API](https://www.airwallex.com/docs/api) — ~0.5–1% FX margin; custom for platform API — API key + account — 150+ countries; multi-currency wallets; free Explore plan
- [Currencycloud (Visa)](https://developer.currencycloud.com/) — custom volume-based spread — API key + partnership — 180+ countries; B2B infrastructure for banks and fintechs

**Free tier:** Yes — Airwallex Explore plan is free  
**Compliance required:** Yes — FinCEN money services business registration; state money transmitter licenses (or exemptions) in the US  
**MCP exists:** No  
**Reversible:** No — settled FX conversions are final

---

### Apply for a Business Loan

> A formal credit application is submitted to a lender, triggering a hard credit pull and underwriting process that may result in a binding loan offer.

**Providers**
- [Lendio](https://www.lendio.com/) — free for borrowers; lender pays platform fee — API/iframe embed for white-label — US; marketplace routing to 75+ lenders via single application
- [Bluevine](https://www.bluevine.com/) — 6.2%+ APR on credit lines up to $250K — web + API webhooks — US; fast decisioning

**Free tier:** No  
**Compliance required:** Yes — lenders must be licensed; platforms may need broker licensing depending on state  
**MCP exists:** No  
**Reversible:** Yes — application can be withdrawn before signing; a funded loan can only be repaid, not reversed

---

### Apply for an SBA Loan

> A small business loan application is submitted to the SBA's E-Tran system, triggering government credit risk screening and, if approved, a federally guaranteed loan.

**Providers**
- [SBA E-Tran API (CAFS)](https://catweb.sba.gov/apidocs/) — free — XML API + SBA lender authorization — US; `Originate3` method accepts loan applications; sandbox certification required before production
- [Lendio](https://www.lendio.com/) — free for borrowers — API for embedded marketplace integration — US; SBA 7(a) loans closed programmatically via partner banks

**Free tier:** Yes (SBA E-Tran is free but requires SBA lender authorization)  
**Compliance required:** Yes — applicant must be an authorized SBA lender; borrowers must meet SBA size standards; personal guarantee required  
**MCP exists:** No  
**Reversible:** Yes — application can be withdrawn before SBA issues a loan number; after guaranty, cancellation requires formal SBA approval

---

### Bind an Insurance Policy

> An insurance policy is quoted, accepted, and bound — coverage is immediately active and a policy number is issued.

**Providers**
- [CoverForce](https://www.coverforce.com/) — commission-based (free to integrators) — API key + contract — US; end-to-end: appetite → quote → bind → issuance
- [SANDIS](https://sandis.io/) — custom/quote — API key + contract — US; full policy lifecycle via API, deploys in ~2 weeks
- [Bindable](https://bindable.com/api) — commission-based — API key + contract — US; embedded insurance for platforms
- [bolttech](https://bolttech.io/) — custom/quote — API key + contract — US/international; large carrier network

**Free tier:** No  
**Compliance required:** Yes — agent/broker license required in most states to bind on behalf of customers  
**MCP exists:** No  
**Reversible:** Yes — policies can be cancelled (subject to short-rate penalties in some states)

---

### Donate to a Nonprofit

> Real money is transferred to a verified 501(c)(3) nonprofit; typically tax-deductible for the donor.

**Providers**
- [Every.org](https://www.every.org/charity-api) — 0% platform fee (donor pays optional tip) — API key — US; any of 1.8M+ US nonprofits; free for non-commercial use
- [GlobalGiving](https://www.globalgiving.org/api/) — ~5% platform fee — API key — US/international; 9.6M+ validated orgs in 175 countries
- [Change](https://getchange.io/) — custom pricing — API key + billing — US; self-serve

**Free tier:** Yes — Every.org is free for non-commercial use  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** No — donations are generally non-refundable once processed

---

### Buy Carbon Offsets

> Carbon credits representing verified emissions reductions are purchased and retired in a public registry, providing a legal claim to offset a quantity of CO2-equivalent.

**Providers**
- [Patch](https://www.patch.io/) — ~$10–50+/tonne CO2 depending on project — REST API (free to integrate, pay per offset) — global; Verra VCS + Gold Standard projects; API supports project selection, purchase, and retirement confirmation
- [Cloverly](https://cloverly.com/api) — custom pricing — REST API — global; integrates into e-commerce and SaaS workflows
- [Carbonmark](https://www.carbonmark.com/) — market-rate spot pricing (~$1–50/tonne) — API available — global; 150+ verified projects

**Free tier:** No (pay per tonne)  
**Compliance required:** No for voluntary; Yes for compliance markets (CORSIA, California ARB)  
**MCP exists:** No  
**Reversible:** No — once retired in Verra or Gold Standard registry, credits cannot be unretired

---

### Purchase Renewable Energy Certificates (RECs)

> A REC representing 1 MWh of renewable electricity generation is transferred to your account in a tracking registry, giving you the legal right to claim that energy as renewable.

**Providers**
- [Xpansiv CBL](https://www.xpansiv.com/trading-platforms/cbl) — ~$0.50–25/MWh depending on type and vintage — API via Xpansiv Connect (contact sales) — North America + international I-RECs; world's most active spot marketplace
- [Patch](https://www.patch.io/) — ~$1–20/MWh — REST API — US/international; wraps REC procurement in same API as carbon offsets

**Free tier:** No  
**Compliance required:** Yes — for state RPS compliance, RECs must be sourced from eligible facilities  
**MCP exists:** No  
**Reversible:** No — retired RECs cannot be transferred or re-sold

---

### Place a Legal Sports Bet

> A wager is placed with a licensed sportsbook, creating a binding financial obligation that resolves based on a sporting outcome.

**Providers**
- [Betfair Exchange API](https://developer.betfair.com/exchange-api/) — free to integrate; £499 one-time activation fee; ~5% commission on winnings — API key + KYC-verified account — UK/Australia/select international (not US); full `placeOrders` endpoint
- [Pinnacle API](https://www.pinnacle.com/en/api/manual/api.html) — contact for access; standard vig — API key + approved account — international (not US); sharp book with the thinnest margins

**Free tier:** No  
**Compliance required:** Yes — online sports betting legal in ~38 US states but no major US sportsbook (DraftKings, FanDuel, BetMGM) exposes a public bet-placement API; Betfair and Pinnacle operate outside the US  
**MCP exists:** No  
**Reversible:** No — once a bet is matched/accepted, it is a binding wager

---

## Identity & Compliance

### Verify a Person's Identity (KYC)

> A person's government-issued ID and/or biometric data is checked against authoritative databases, producing a pass/fail result suitable for regulatory onboarding.

**Providers**
- [Persona](https://docs.withpersona.com/) — ~$1.50–3/verification — API key + billing — US/international; configurable workflows, government ID + liveness detection
- [Stripe Identity](https://stripe.com/identity) — ~$1.50/verification — API key + billing — US/international; selfie + document; tight Stripe integration

**Free tier:** Yes — both offer test modes  
**Compliance required:** Yes — CCPA, GDPR; biometric data laws apply in IL, TX, WA  
**MCP exists:** No  
**Reversible:** N/A — verification produces a result; the record persists

---

### Run a Background Check

> A criminal, employment, and/or credit history report is generated on a named individual, FCRA-compliant and suitable for employment or tenancy decisions.

**Providers**
- [Accurate Background](https://www.accurate.com/) — custom/quote — API key + contract — US; FCRA-compliant, criminal + credit + employment history
- [GoodHire](https://www.goodhire.com/) — $29.99–79.99/report — API key + billing — US; ATS integrations, automated adverse action workflows
- [BackgroundChecks.com](https://www.backgroundchecks.com/) — $19.95–79.95/report — API key + billing — US; sandbox available

**Free tier:** No  
**Compliance required:** Yes — FCRA compliance required; written consent from the subject mandatory; adverse action process required before using a negative report  
**MCP exists:** No  
**Reversible:** No — report is generated; consumer can dispute inaccurate information with the bureau

---

### Verify a Candidate's Employment History

> An authoritative query is made against employer payroll records to confirm dates of employment, job title, and salary for a named individual, with their consent.

**Providers**
- [Equifax The Work Number API](https://developer.equifax.com/products/apiproducts/verification-employment-and-income) — $105/verification (as of Jan 2026) — API key + FCRA permissible purpose agreement — US; 823M+ employee records from 3M+ employers; instant automated response
- [Truework API](https://www.truework.com/) — ~$25–75/verification — API key + contract — US; multi-method (instant, manual, employer portal)
- [Argyle API](https://argyle.com/) — custom pricing — API key + contract — US; payroll connectivity; employee grants access via OAuth

**Free tier:** No  
**Compliance required:** Yes — FCRA permissible purpose required; written candidate consent mandatory  
**MCP exists:** No  
**Reversible:** N/A — read-only query; the verification record cannot be un-run

---

### Verify Right to Work via I-9 E-Verify

> A new hire's identity and employment authorization documents are verified against DHS and SSA databases; a case result is returned and logged.

**Providers**
- [Symmetry I-9 API (WorkBright)](https://www.symmetry.com/symmetry-i9) — custom pricing — API key + DHS E-Verify MOU — US; embeddable I-9 + automated E-Verify submission
- [Equifax I-9 HQ](https://workforce.equifax.com/solutions/i9-hq) — custom enterprise pricing — API key + Equifax contract + DHS MOU — US
- [Checkr API](https://checkr.com/) — custom pricing — API key + FCRA agreement — US; I-9 task automation + E-Verify alongside background screening

**Free tier:** No (E-Verify itself is free via DHS; third-party platforms charge)  
**Compliance required:** Yes — employers must sign a DHS E-Verify MOU; federal contractors in many states are legally mandated to use E-Verify; I-9 must be completed within 3 days of hire  
**MCP exists:** No  
**Reversible:** No — an E-Verify case creates a federal record; cases cannot be deleted

---

## Physical Mail & Shipping

### Send a Physical Letter

> A real paper letter is printed, stuffed, stamped, and mailed to any address — arrives in 3–5 days.

**Providers**
- [PostGrid](https://www.postgrid.com/) — ~$0.75–1.20/letter — API key + billing — US/CA/international; address validation + certified mail available
- [Lob](https://www.lob.com/) — ~$0.80–1.50/letter — API key + billing — US + international; industry standard, test mode available
- [LettrLabs](https://www.lettrlabs.com/) — ~$2–5/card — API key + billing — US; robotic pen, looks genuinely handwritten
- [Click2Mail](https://click2mail.com/) — ~$0.60–0.90/letter — API key + billing — US; cheapest, next-day printing

**Free tier:** No  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** No — once mailed, cannot be recalled

---

### Send a Physical Check

> A real paper check is printed and mailed to any payee at any address, valid for deposit at any US bank.

**Providers**
- [Lob Checks](https://www.lob.com/checks) — ~$2–4/check — API key + billing — US; MICR encoding, real bank routing numbers, fraud prevention
- [PostGrid Checks](https://www.postgrid.com/) — custom pricing — API key + billing — US/CA
- [OnlineCheckWriter](https://onlinecheckwriter.com/) — ~$1.25/check — API key + billing — US; integrates with QuickBooks

**Free tier:** No  
**Compliance required:** Yes — must have an active bank account to issue from; check fraud laws apply  
**MCP exists:** No  
**Reversible:** Partial — stop payment can be placed with the bank before the check is deposited

---

### Ship a Package

> A shipping label is purchased and a package enters the carrier network, tracked from origin to delivery.

**Providers**
- [EasyPost](https://www.easypost.com/) — carrier rates + ~$0.05/shipment surcharge — API key + billing — US/international; 100+ carriers, rate shopping, address verification, insurance, returns
- [Shippo](https://goshippo.com/) — $0.05/shipment — API key + billing — US/international; clean API, multi-carrier
- [FedEx Ship API](https://developer.fedex.com/) — carrier rates — API key + FedEx account — US/international
- [USPS Domestic Labels API](https://developers.usps.com/apis) — postage rates — API key + permit — US domestic

**Free tier:** No  
**Compliance required:** No — hazardous materials require special handling  
**MCP exists:** No  
**Reversible:** Partial — package can be intercepted before delivery (FedEx/UPS charge a fee)

---

## Healthcare

### Order a Prescription Refill + Delivery

> An existing prescription is refilled at a pharmacy and shipped directly to a patient's home address.

**Providers**
- [CloudRx API](https://www.cloudrx.co.uk/) — custom pricing — API key + contract — UK/US partnerships; submit prescriptions, arrange direct-to-patient delivery, track status
- [Walgreens Pharmacy API](https://developer.walgreens.com/) — no charge (retail pricing applies) — API key + developer account — US; refill initiation, transfer, status check
- [Truepill API](https://truepill.com/) — custom per-order pricing — partner contract — US; white-label pharmacy fulfillment covering OTC and Rx

**Free tier:** No  
**Compliance required:** Yes — prescriber must hold valid DEA registration; HIPAA compliance required; controlled substances have additional restrictions  
**MCP exists:** No  
**Reversible:** No — once dispensed, prescriptions cannot be returned in most states

---

### Look Up Real-Time Drug Prices

> Current retail and discount prices for a specific medication are retrieved across multiple pharmacies near a given location.

**Providers**
- [GoodRx API](https://www.goodrx.com/developer) — free (non-commercial) / custom (commercial) — API key — US; real-time pricing + discount coupons at 70,000+ pharmacies
- [openFDA Drug API](https://open.fda.gov/apis/drug/) — free — API key — US; drug label, adverse event, and recall data (not pricing)

**Free tier:** Yes — GoodRx is free for non-commercial use  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** N/A — read-only lookup

---

### Order an At-Home Lab Test

> A physical kit is mailed to the patient who self-collects a sample and returns it; results are processed by a CLIA-certified lab and released to the patient.

**Providers**
- [BioReference API Marketplace](https://developer.bioreference.com/) — custom enterprise pricing — API key + contract — US; REST API for ordering, results retrieval, patient record creation
- [Everly Health Solutions (B2B)](https://www.everlywell.com/partnerships) — custom per-kit pricing (~$30–150/kit at volume) — partner agreement — US only
- [Labcorp OnDemand](https://www.ondemand.labcorp.com/) — $30–200/test — enterprise agreement — US; no public developer API; partner integrations available

**Free tier:** No  
**Compliance required:** Yes — CLIA, HIPAA, and state-level Direct Access Testing laws vary; some states (NY, NJ, RI, MD) prohibit direct-to-consumer lab orders  
**MCP exists:** No  
**Reversible:** No — once a kit ships and sample is processed, the test cannot be reversed

---

### Order a DNA Test (Ancestry or Health)

> A saliva collection kit is mailed to a consumer; their genome is sequenced and ancestry or health trait reports are generated and stored in the provider's database.

**Providers**
- [Sequencing.com API](https://sequencing.com/) — ~$0.01–0.10/query for genomic analysis APIs — API key + billing — US/international; closest true developer API for DNA test ordering and raw data analysis
- [23andMe](https://www.23andme.com/) — ~$99–229/kit — no official ordering API; affiliate/partner programs exist but are not fully programmatic
- [AncestryDNA](https://www.ancestry.com/dna/) — ~$99/kit — no official API

**Free tier:** No  
**Compliance required:** Yes — GINA applies; health-specific genomic reports require physician oversight in some states; FDA oversight applies to health-related reports  
**MCP exists:** No  
**Reversible:** No — once sequenced and stored, genetic data persists

---

### Schedule a Telehealth Appointment

> A booking record is created in a licensed provider's scheduling system and a consultation slot is reserved.

**Providers**
- [Healthie API](https://www.gethealthie.com/) — from $99/mo — API key + subscription — US; HIPAA-compliant scheduling, EHR integration, telehealth video
- [NexHealth API](https://nexhealth.com/) — custom pricing — API key + contract — US; EHR-synced scheduling with intake forms
- [HealthTap API](https://www.healthtap.com/) — custom enterprise — partner agreement — US; white-label telehealth including scheduling, Rx, and async messaging

**Free tier:** No  
**Compliance required:** Yes — HIPAA required; state medical practice laws govern cross-state prescribing  
**MCP exists:** No  
**Reversible:** Yes — appointments can be cancelled up to provider-defined cutoff windows

---

### Apply for Health Insurance via Broker API

> An ACA-compliant insurance application is submitted on behalf of a consumer to a federal or state marketplace, creating an active enrollment record with a carrier.

**Providers**
- [CMS Marketplace API](https://developer.cms.gov/marketplace-api/) — free — API key (CMS approval required) — US; official federal API for plan lookup, eligibility, and enrollment
- [HealthSherpa](https://www.healthsherpa.com/) — free for licensed brokers — broker NPN + CMS registration — US; largest private ACA enrollment platform with quoting, APTC estimation, and enrollment API

**Free tier:** Yes (HealthSherpa is free for licensed brokers)  
**Compliance required:** Yes — agent/broker must hold valid NPN and complete annual CMS certification; consumer documented consent required before accessing Marketplace data  
**MCP exists:** No  
**Reversible:** Yes — enrollments can be cancelled during SEP/OEP windows

---

### File a Health Insurance Claim

> An 837 transaction is transmitted to a payer or clearinghouse, creating a formal claim record that triggers adjudication and payment workflows.

**Providers**
- [Stedi](https://www.stedi.com/) — usage-based (see stedi.com/pricing) — API key + billing — US; modern JSON-in/837-out clearinghouse, developer-friendly REST API
- [Availity](https://www.availity.com/) — custom enterprise — enrollment agreement per payer — US; REST + FHIR APIs for 837, 276 claim status, and 278 auth
- [Change Healthcare (Optum)](https://www.changehealthcare.com/) — custom — enterprise contract — US; highest payer reach (~1M+ providers)

**Free tier:** No  
**Compliance required:** Yes — HIPAA X12 5010 standards required; NPI and payer enrollment required per payer  
**MCP exists:** No  
**Reversible:** No — claims can be voided or corrected with a subsequent 837 void transaction, but the original submission is permanent

---

### Submit a Prior Authorization Request to an Insurer

> A structured authorization request for a non-drug service is transmitted to a payer, which must respond with approval, denial, or pend status within regulatory timeframes.

**Providers**
- [Availity Prior Auth API](https://www.availity.com/) — custom enterprise — enrollment + payer agreement — US; supports FHIR-based PAS and legacy X12 278
- [CMS FHIR Prior Authorization API](https://www.cms.gov/priorities/electronic-prior-authorization/overview) — free (payer-side implementation) — SMART on FHIR / OAuth 2.0 — US; mandated for MA, Medicaid, CHIP, Marketplace plans; full rollout by Jan 1, 2027

**Free tier:** No  
**Compliance required:** Yes — HIPAA; CMS-0057-F mandates FHIR PA implementation guides; payer-specific enrollment required  
**MCP exists:** No  
**Reversible:** No — a submitted PA request is logged; can be cancelled but the original is an auditable record

---

## Real Estate

### Sign a Lease Agreement Digitally

> Legally binding electronic signatures are applied to a lease document by all parties, creating an enforceable contract.

**Providers**
- [DocuSign eSign API](https://developers.docusign.com/) — from $75/mo (40 envelopes); overage ~$4.80/envelope — API key + subscription — US/international; deep real estate and property management integrations
- [Dropbox Sign API](https://sign.dropbox.com/) — from $25/mo; API plan from $75/mo — API key + subscription — US/international; simpler integration, embedded signing flow
- [Adobe Acrobat Sign API](https://www.adobe.com/sign/developer-program.html) — custom enterprise / from $23/mo per user — API key + contract — US/international; strong compliance posture

**Free tier:** Yes (DocuSign developer sandbox; Dropbox Sign limited trial)  
**Compliance required:** No for standard residential leases; some jurisdictions require wet signatures for leases over 3 years  
**MCP exists:** No  
**Reversible:** No — once all parties sign, the executed document is legally binding

---

### Pay Rent

> An ACH or card payment is initiated from a tenant's bank account to a landlord or property manager's account, recorded against a lease ledger.

**Providers**
- [Stripe](https://stripe.com/) — 2.9% + $0.30/card; 0.8% ($5 cap)/ACH debit — API key + account — US/international; used by most rent platforms
- [Baselane](https://www.baselane.com/) — free for ACH; 2.99% for card — API key — US; landlord-native banking + rent collection with built-in ledger
- [DoorLoop API](https://www.doorloop.com/) — $69–179/mo platform + payment processing — API key + subscription — US; property management with native rent collection

**Free tier:** Yes (ACH is free on Baselane; Stripe has no monthly fee)  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** Partial — ACH returns possible within 2 business days; intentional reversal requires a refund API call

---

### Collect Rent and Distribute to Property Owners

> Tenant payments are aggregated in a property management ledger and then disbursed net of fees to property owners via ACH.

**Providers**
- [Rentvine API](https://www.rentvine.com/) — custom pricing — API key + contract — US; fully open API; owner distribution, trust accounting, ledger sync
- [AppFolio API](https://www.appfolio.com/) — $1.40+/unit/mo platform — API key + enterprise agreement — US; industry-standard for larger portfolios
- [Rentec Direct Open API](https://www.rentecdirect.com/) — free for existing clients (platform from $45/mo) — API key + Rentec account — US; April 2026 launch

**Free tier:** No  
**Compliance required:** Yes — property management trust accounting laws vary by state; some states require a licensed property manager  
**MCP exists:** No  
**Reversible:** Partial — scheduled distributions can be cancelled before processing; completed ACH transfers can be reversed only within NACHA return window

---

### List a Property on Airbnb or VRBO

> A property listing (title, description, photos, availability calendar, pricing) is created or updated on a short-term rental platform, making it bookable by guests.

**Providers**
- [Hostaway](https://www.hostaway.com/) — ~$20–40/listing/mo — API key + subscription — US/international; certified Airbnb and VRBO connectivity partner; real-time API sync across 60+ OTAs
- [Guesty](https://www.guesty.com/) — ~$40/listing/mo (quote-based) — API key + contract — US/international; enterprise-grade channel manager
- [OwnerRez](https://www.ownerrez.com/) — from £72/mo (1–5 properties) — API key + subscription — US/UK; VRBO-certified, direct Airbnb API integration

**Free tier:** No  
**Compliance required:** Yes — many cities require STR permits, business licenses, and TOT tax registration  
**MCP exists:** No  
**Reversible:** Yes — listings can be unpublished or deleted via API

---

### Pull a Property's Ownership, Lien, and Tax History

> Public records data (deed chain, mortgage/lien filings, tax assessments) is retrieved from county recorder and assessor databases for a specified parcel.

**Providers**
- [ATTOM Data API](https://www.attomdata.com/) — custom enterprise pricing — API key + contract — US; 155M+ properties; ownership history, tax records, foreclosure, lien data; **native MCP integration available**
- [CoreLogic API](https://www.corelogic.com/) — custom enterprise — partner contract — US; industry standard for mortgage-adjacent lien and ownership data
- [First American DataTree API](https://datatree.com/) — custom — API key + enterprise agreement — US; nationwide property and document images, lien, and ownership chains

**Free tier:** No  
**Compliance required:** No for general research; Yes if used for credit/employment decisions (FCRA applies)  
**MCP exists:** Yes (ATTOM has an MCP server)  
**Reversible:** N/A — read-only data retrieval

---

### Get a Title Report on a Property

> A search of public land records is performed to produce a written report documenting the chain of title, encumbrances, liens, and any defects affecting clear ownership.

**Providers**
- [Qualia API](https://www.qualia.com/qualia-api/) — custom pricing — API key + partner contract — US; programmatic title order placement and tracking
- [First American DNA API](https://dna.firstam.com/api) — custom pricing — API key + enterprise agreement — US; instant property reports, AVM, document images, and title data
- [PropMix API](https://pubrec.propmix.io/) — custom pricing — API key + contract — US; nationwide public record APIs covering ownership, liens, and title chain

**Free tier:** No  
**Compliance required:** Yes — certified title search required for most real estate closings; a licensed title agent must review and issue a commitment for insurance purposes  
**MCP exists:** No  
**Reversible:** N/A — read-only report generation

---

## Hiring & Employment

### Post a Job Listing to Major Boards

> A job posting is published on one or more job boards, becoming publicly searchable and eligible to receive candidate applications.

**Providers**
- [Indeed Job Sync API](https://docs.indeed.com/job-sync-api/) — $0.10–5.00 CPC for Sponsored Jobs; free organic limited to 3 posts/mo — partner approval required — US/international
- [LinkedIn Jobs API](https://learn.microsoft.com/en-us/linkedin/talent/job-postings/api/overview) — Recruiter Corporate license required (~$900/mo/seat) — LinkedIn Talent Solutions contract — US/international
- [Broadbean / CareerBuilder API](https://www.broadbean.com/) — custom per-posting fees — API key + contract — US/international; multi-board distribution covering 100+ job boards

**Free tier:** No (Indeed allows 3 free organic posts/mo; LinkedIn has no free API)  
**Compliance required:** Yes — EEOC non-discrimination requirements apply; some states (CA, NY, CO) require salary range disclosure  
**MCP exists:** No  
**Reversible:** Yes — listings can be closed or deleted via API

---

### Hire a Freelancer via Platform API

> A contract is created between a client and an independent contractor on a marketplace platform, establishing terms, rates, and work scope; payment escrow may be activated.

**Providers**
- [Upwork GraphQL API](https://www.upwork.com/developer) — 3% ACH or up to 7.99% card per payment; $0.99–14.99 contract initiation fee — OAuth 2.0 — US/international; job posting, contract creation, custom payments, messaging
- [Fiverr Business API](https://developers.fiverr.com/) — service prices $5–500+; ~5.5% platform fee — API key (enterprise program) — US/international
- [Deel API](https://www.deel.com/api) — from $49/contractor/mo — API key + Deel contract — US/international; contractor onboarding, contract generation, compliance, and payment; covers 150+ countries

**Free tier:** No  
**Compliance required:** Yes — worker classification rules (IRS, FLSA, state AB5 in CA) apply; international contracts require local labor law compliance  
**MCP exists:** No  
**Reversible:** Partial — fixed-price contracts with funded escrow can be disputed before work is approved; hourly contracts pay for logged hours and are not reversible once approved

---

### Enroll an Employee in Benefits

> An employee's health insurance, dental, vision, 401(k), FSA/HSA, and ancillary benefit elections are transmitted to carriers and plan administrators, activating coverage effective the specified date.

**Providers**
- [Rippling Benefits API](https://www.rippling.com/benefits) — modular pricing (included in Rippling HRIS bundle) — API key + Rippling contract — US; 900+ carrier connections
- [Employee Navigator API](https://www.employeenavigator.com/) — custom broker/carrier pricing — API key + partner agreement — US; broker-centric benefits administration with EDI-based carrier feeds
- [PlanSource API](https://www.plansource.com/) — custom enterprise — API key + contract — US; cloud-based enrollment platform

**Free tier:** No  
**Compliance required:** Yes — ERISA governs employer-sponsored plans; ACA reporting required for applicable large employers; HIPAA applies to health data  
**MCP exists:** No  
**Reversible:** Partial — elections can be changed during open enrollment or qualifying life event windows; mid-year changes are restricted by IRS Section 125 regulations

---

## Travel & Reservations

### Book a Flight

> A confirmed airline seat reservation is created in the carrier's reservation system, binding the traveler and airline to a fare contract.

**Providers**
- [Amadeus for Developers](https://developers.amadeus.com/) — negotiated per-booking fee — API key + approved partnership — global; 490+ airlines, largest GDS, self-service sandbox
- [Sabre Dev Studio](https://developer.sabre.com/) — negotiated per-booking fee — partnership agreement — global; 400+ airlines, strong US carrier relationships
- [Travelport](https://developer.travelport.com/) — $4K–15K integration; lower per-booking rates — partnership agreement — global; Galileo/Apollo/Worldspan under one API

**Free tier:** Yes — Amadeus self-service sandbox with test data at no cost  
**Compliance required:** Yes — IATA/BSP accreditation required to issue tickets  
**MCP exists:** No  
**Reversible:** Partial — airlines charge change/cancel fees; some fares are non-refundable

---

### Book a Hotel Room

> A guaranteed room reservation is created at a specific property, charging the guest's payment method per the rate rules.

**Providers**
- [Amadeus Hotel APIs](https://developers.amadeus.com/self-service/category/hotels) — commission-based — API key + partnership — 1.5M+ properties globally; self-service sandbox
- [Expedia EPS Rapid API](https://partner.expediagroup.com/) — commission-based (~25–30%) — partnership approval — 700K+ properties
- [Booking.com Demand API](https://developers.booking.com/) — commission-based — partnership agreement — global; strong European inventory

**Free tier:** Yes — Amadeus sandbox  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** Partial — depends on cancellation policy set by property; free cancellation rates exist

---

### Reserve a Rental Car

> A vehicle hold is placed with a rental agency at a specific location and date range, guaranteeing rate and vehicle class.

**Providers**
- [Expedia Rapid Car API](https://partner.expediagroup.com/) — commission-based — partnership agreement (beta) — 110+ brands, 45K vendors, 190 countries
- [CarTrawler API](https://www.cartrawler.com/) — commission paid at counter — partnership/enterprise contract — 2K+ agents in 50K locations
- [Trawex Car API](https://www.trawex.com/car-booking-api.php) — custom pricing — enterprise agreement — global; aggregates GDS + OTA inventory

**Free tier:** No  
**Compliance required:** No — driver's license verification happens at counter  
**MCP exists:** No  
**Reversible:** Yes — most reservations allow cancellation before pickup with no charge

---

### Make a Restaurant Reservation

> A time slot at a restaurant is held under a guest's name, with the venue committing staffing and table resources.

**Providers**
- [OpenTable API](https://docs.opentable.com/) — negotiated enterprise terms — formal partner agreement + approval review — 50K+ restaurants worldwide
- [Yelp Reservations](https://www.yelp.com/developers) — custom enterprise — partner approval — US; alternative network for venues not on OpenTable
- Note: Resy has no official public API; unofficial wrappers exist

**Free tier:** No — OpenTable requires formal agreement  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** Yes — cancellations generally free up to a threshold; no-show fees at some venues

---

### Book a Private Jet Charter

> A binding charter agreement is created for exclusive aircraft use on a specified route, obligating the operator and triggering cost deposits.

**Providers**
- [Avinode API](https://avinode.com/api/) — access via Ultimate membership tier (pricing on request) — enterprise partnership — global; largest air charter marketplace
- [Jettly API](https://jettly.com/api-intregrations) — custom pricing — partnership agreement — North America/global
- [CharterAPI](https://charterapi.com/) — custom enterprise — contact required — US/international; purpose-built REST API for air charter search and booking

**Free tier:** No  
**Compliance required:** Yes — FAA Part 135 operator certification required for the aircraft  
**MCP exists:** No  
**Reversible:** Partial — deposits typically non-refundable; cancellation windows and penalty schedules vary by operator

---

## Communications at Scale

### Send Bulk Email to a List

> Email messages are delivered to potentially millions of inboxes simultaneously on behalf of the sender, with legal attribution to the sending domain.

**Providers**
- [SendGrid API](https://sendgrid.com/) — $19.95/mo for 50K emails (~$0.40/1K) — API key + billing — global; strong deliverability and developer tooling
- [Mailchimp API](https://mailchimp.com/) — $13/mo for 500 contacts / 5K sends — API key + billing — global; pricing based on contact list size; built-in audience management
- [Resend](https://resend.com/) — free for 3K/mo; ~$0.80/1K above — API key — global; developer-first, excellent React Email support

**Free tier:** Yes — Mailchimp free for up to 500 contacts; Resend 3K/mo free  
**Compliance required:** Yes — CAN-SPAM (US), GDPR (EU), and CASL (CA) require opt-in, unsubscribe mechanisms, and sender identification  
**MCP exists:** No  
**Reversible:** No — email cannot be recalled once delivered

---

### Send an SMS

> A text message is delivered to a mobile handset via the carrier network.

**Providers**
- [Twilio SMS API](https://www.twilio.com/en-us/sms) — $0.0079/segment outbound US; +$1.15/mo per number — API key + billing — global 180+ countries; market leader
- [Vonage Voice/SMS](https://www.vonage.com/communications-apis/) — ~$0.0065/SMS outbound US — API key + billing — global
- [Plivo](https://www.plivo.com/) — ~$0.0055/SMS outbound US — API key + billing — global; lower cost alternative

**Free tier:** Yes — Twilio trial with $15 credit; Vonage free sandbox  
**Compliance required:** Yes — TCPA requires prior express consent for marketing SMS; 10DLC campaign registration required for US A2P messaging  
**MCP exists:** No  
**Reversible:** No — SMS cannot be recalled after delivery

---

### Send a Fax

> A document is transmitted over PSTN or FoIP to a fax machine or fax-to-email service, creating a legally valid transmission record.

**Providers**
- [Phaxio](https://www.phaxio.com/) — $0.07/page US/Canada; $0.10/page UK/EU/JP — API key + prepay — US/international; developer-built, no contracts, clean REST API
- [Telnyx Fax API](https://telnyx.com/products/fax-api) — ~$0.007/page + SIP trunking costs — API key + billing — global; cheapest per-page rate
- [Fax.plus API](https://www.fax.plus/fax-api) — $0.05–0.10/page — API key + subscription — global; HIPAA-compliant

**Free tier:** Yes — Telnyx free trial credits; Fax.plus limited free tier  
**Compliance required:** Partial — HIPAA compliance required for healthcare PHI transmission  
**MCP exists:** No  
**Reversible:** No — fax transmission cannot be recalled once sent

---

### Make a Phone Call (Text-to-Speech or AI Voice)

> An outbound phone call is placed to a real telephone number, delivering synthesized or AI-generated voice audio to the recipient.

**Providers**
- [Twilio Voice API](https://www.twilio.com/en-us/voice) — $0.014/min outbound US; $0.0085/min inbound — API key + billing — global; industry standard, built-in TTS
- [Vonage Voice API](https://developer.vonage.com/en/voice/voice-api/overview) — ~$0.013/min outbound US — API key + billing — global
- [Bland.ai](https://www.bland.ai/) — ~$0.09/min for AI voice calls — API key + billing — US/global; purpose-built for AI phone agents, handles conversation logic natively

**Free tier:** Yes — Twilio $15 trial credit  
**Compliance required:** Yes — TCPA requires consent for telemarketing/robocalls; FCC regulations on AI voice disclosure emerging in 2025–2026  
**MCP exists:** No  
**Reversible:** No — call is delivered in real time; no recall possible

---

### Distribute a Press Release to News Outlets

> A press release is transmitted to a wire service network, redistributed to thousands of newsrooms, creating permanent indexed records.

**Providers**
- [PR Newswire (Cision)](https://www.prnewswire.com/) — $350–8,700/release depending on word count + distribution scope — enterprise/web submission — US national ~$805/release; widest US editorial reach
- [Business Wire](https://www.businesswire.com/) — $475+ for local 400-word — enterprise agreement — global; Berkshire Hathaway-owned, strong financial press distribution
- [EIN Presswire](https://www.einpresswire.com/) — $99–999/release — API key available — global; lower cost, API access available for volume distribution

**Free tier:** No  
**Compliance required:** Partial — SEC Regulation FD if publicly traded company; content must be factually accurate  
**MCP exists:** No  
**Reversible:** No — once distributed to wire, permanent syndication cannot be recalled

---

### Place a Targeted Ad via API

> An ad creative is served to a targeted audience segment across a publisher network, with spend deducted per impression or click.

**Providers**
- [Google Ads API](https://developers.google.com/google-ads/api) — no API fee; pay ad spend only — OAuth2 + developer token — global; powers Search/Display/YouTube/Shopping
- [Meta Marketing API](https://developers.facebook.com/docs/marketing-api) — no API fee; pay ad spend only — OAuth2 + app review — global; Facebook/Instagram/Messenger placements
- [The Trade Desk API](https://api.thetradedesk.com/) — no API fee; ~15–20% of spend platform fee — partnership agreement — global; programmatic display/video/CTV

**Free tier:** No — all require minimum ad spend  
**Compliance required:** Yes — FTC disclosure for sponsored content; platform-specific policies for health, finance, political ads  
**MCP exists:** No  
**Reversible:** Yes — campaigns can be paused immediately; spent budget is not refunded

---

### Post to Social Media Accounts

> Content is published to one or more social platform accounts, appearing publicly with the account's identity attached.

**Providers**
- [Ayrshare API](https://www.ayrshare.com/) — $49–99/mo — API key + billing — 13+ platforms including X, Instagram, TikTok, LinkedIn, Threads, Bluesky
- [Buffer API](https://buffer.com/developers/api) — $6/mo per channel — API key + OAuth — Facebook, Instagram, LinkedIn, X, TikTok, Pinterest, Bluesky, YouTube, Threads
- [X API](https://developer.twitter.com/) — $200/mo Basic tier for posting access — OAuth2 — X only

**Free tier:** Yes — Ayrshare free plan (20 posts/mo); Buffer free (3 channels)  
**Compliance required:** Partial — FTC disclosure for sponsored/paid content  
**MCP exists:** No  
**Reversible:** Yes — posts can be deleted via API after publishing

---

### Put Up a Digital Billboard

> An ad creative is scheduled for display on physical digital out-of-home screens in public spaces, visible to foot and vehicle traffic.

**Providers**
- [Adomni](https://www.adomni.com/) — CPM-based, no minimum spend — self-serve, credit card — US/global; 1M+ connected screens, includes Clear Channel and Lamar inventory
- [Clear Channel Outdoor Programmatic](https://web.clearchanneloutdoor.com/programmatic) — CPM via DSP auction — DSP partnership (DV360, The Trade Desk) — US/global; biddable via private marketplace or open exchange
- [Lamar Programmatic](https://lamar.com/en/products/programmatic) — CPM floors $5–9 for roadside DOOH — DSP integration — US; 4,600+ large-format screens

**Free tier:** No  
**Compliance required:** Partial — local ordinances on ad content; alcohol, cannabis, and political ads subject to platform rules  
**MCP exists:** No  
**Reversible:** Yes — campaigns can be paused before they run; live impressions already served are not refundable

---

### Send a Push Notification to App Users

> A notification is delivered to users' device lock screens via the OS notification system (APNs/FCM), triggering an alert even when the app is closed.

**Providers**
- [Firebase Cloud Messaging (FCM)](https://firebase.google.com/products/cloud-messaging) — free, unlimited sends — Google account + Firebase project — global iOS/Android/Web
- [OneSignal](https://onesignal.com/) — free for unlimited mobile push; paid from $19/mo for journeys/segmentation — API key + SDK — global; most generous free tier, A/B testing
- [Courier](https://www.courier.com/) — free for 10K notifications/mo; $250/mo Professional — API key — global; routing abstraction layer supporting push + email + SMS from one API

**Free tier:** Yes — FCM fully free; OneSignal free for core push  
**Compliance required:** Yes — users must explicitly grant notification permission (iOS requires prompt); GDPR considerations for EU users  
**MCP exists:** No  
**Reversible:** No — notifications delivered to device cannot be recalled

---

## Publishing & Distribution

### Self-Publish a Book on Amazon

> A book title is created and listed for sale on Amazon's global storefront, becoming purchasable by any Amazon customer within ~72 hours.

**Providers**
- [Amazon KDP](https://kdp.amazon.com/) — free to publish; Amazon takes 30% (70% royalty tier for $2.99–9.99 eBooks); 50% of list minus printing cost for paperbacks — KDP account — global; no public API for programmatic submission (web UI only)
- [Draft2Digital](https://draft2digital.com/) — free; takes 10% of list price — account-based — Amazon + 40+ other retailers; distributes to Amazon as aggregator; partner API available for enterprise

**Free tier:** Yes — KDP is free to use  
**Compliance required:** No — except content policy compliance  
**MCP exists:** No  
**Reversible:** Yes — titles can be unpublished at any time; purchased copies cannot be recalled

---

### Distribute a Song/Album to Streaming Platforms

> An audio recording is delivered to 150+ streaming platforms and digital stores globally, making it playable and purchasable to hundreds of millions of listeners.

**Providers**
- [DistroKid](https://distrokid.com/) — $24.99/yr (unlimited uploads, 100% royalties) — account-based web UI; no public API — 150+ platforms; fastest delivery (~24–48h)
- [TuneCore](https://www.tunecore.com/) — $14.99/single or $29.99/album per year — account-based; no public API — global; 100% royalties, strong reporting
- [CD Baby](https://cdbaby.com/) — $9.95/single one-time; $29/album one-time — account-based — global; one-time fee model, physical distribution also available
- Note: No major distributor has a public API; all require web-based submission

**Free tier:** No  
**Compliance required:** Partial — AI-generated music subject to evolving policies per platform (TuneCore/DistroKid updated AI policies in 2025–2026); ISRC codes required  
**MCP exists:** No  
**Reversible:** Yes — releases can be taken down from stores; royalties already paid out are not reversed

---

### Distribute a Podcast to All Directories

> A podcast's RSS feed is registered with Apple Podcasts, Spotify, Amazon Music, YouTube Music, and 20+ other directories, making episodes publicly available and searchable.

**Providers**
- [RSS.com](https://rss.com/) — free plan + $24.99/mo Network for API access — public API (beta, Feb 2026) — global; API for programmatic episode publishing and distribution triggering; auto-submits to Spotify, Apple, Amazon, YouTube Music
- [Captivate](https://www.captivate.fm/) — $17–90/mo — web UI; no public API — global; "Submit to All" one-click distribution
- [Transistor](https://transistor.fm/) — $19–99/mo — web UI with webhook support — global; auto-distribution to all major directories

**Free tier:** Yes — RSS.com free tier distributes to Spotify, Apple, Amazon, YouTube Music  
**Compliance required:** No — standard content policies apply per directory  
**MCP exists:** No  
**Reversible:** Yes — episodes and entire feeds can be removed; directories cache feeds and may take 24–72h to reflect removal

---

## Manufacturing & Physical Objects

### Order a 3D-Printed Part

> A digital model file is submitted and a physical part is manufactured and shipped to any address.

**Providers**
- [Slant 3D](https://www.slant3d.com/slant-3d-printing-api) — pay per part only; no API access fee — API key — US; digital inventory, on-demand production
- [Sculpteo](https://www.sculpteo.com/en/services/api-services/) — per-part pricing — API key + billing — US/EU; automate upload, configure, order
- [Shapeways](https://developers.shapeways.com/) — per-part pricing + 5% transaction fee — API key — US/international; free API access

**Free tier:** No — per-part fees apply  
**Compliance required:** No — ITAR-controlled parts require export licenses  
**MCP exists:** No  
**Reversible:** No — once in production, orders cannot be cancelled

---

### Order a Custom PCB Circuit Board

> A fabrication house manufactures bare printed circuit boards to your Gerber specifications and ships them to your address.

**Providers**
- [JLCPCB](https://jlcpcb.com/) — from ~$2/5-board prototype — web order + Gerber upload; no public REST API — global; fastest and cheapest for prototypes, 24-hour turnaround standard
- [PCBWay](https://www.pcbway.com/) — from ~$5/5-board prototype — partner API at api-partner.pcbway.com (approval required) — global; full API for quote, order, and tracking

**Free tier:** No  
**Compliance required:** No — export controls (EAR/ITAR) apply if boards contain controlled technology  
**MCP exists:** No  
**Reversible:** No — once production begins, cancellation is at manufacturer's discretion

---

### Order Custom Injection-Molded or CNC-Machined Parts

> A manufacturer machines or molds physical parts to your CAD specifications and ships them.

**Providers**
- [Xometry](https://developer.xometry.com/docs/getting-started) — instant quote via web + REST API — API key + account — US and global partner network; full developer API for programmatic quoting, order placement, and job tracking
- [Protolabs](https://www.protolabs.com/) — quote via web upload; no documented public REST API — US/EU; owns its own factories, faster for standard materials; contact sales for enterprise API

**Free tier:** No (Xometry API access is free to integrate; pay per order)  
**Compliance required:** Potentially — ITAR controls apply to defense-related CAD files  
**MCP exists:** No  
**Reversible:** No — once production begins, parts cannot be un-manufactured

---

### Order Custom Packaging Boxes

> A packaging manufacturer produces custom-printed corrugated or folded boxes to your dimensions and artwork, and ships them.

**Providers**
- [Packlane](https://packlane.com/) — ~$1.50–8/box depending on qty + specs — API available for custom integrations (contact sales) — US; no minimum order
- [Arka](https://arka.com/) — custom pricing — API + Shopify/WMS integrations — US; connects directly to warehouses and 3PLs
- [Packola](https://www.packola.com/) — ~$0.80–5/box — web order; no documented public API — US; no minimum order

**Free tier:** No  
**Compliance required:** No (food-contact packaging may require FDA-compliant inks)  
**MCP exists:** No  
**Reversible:** No — custom printed runs are non-returnable; proof approval is the point of no return

---

### Print and Ship Custom Business Cards, Flyers, Banners

> A print shop produces finished printed marketing collateral to your artwork and ships it to a specified address.

**Providers**
- [MOO](https://www.moo.com/us/) — ~$20–50/50 business cards; flyers from ~$30 — enterprise API available — US/international; premium paper quality, white-label API for enterprise partners
- [Vistaprint](https://www.vistaprint.com/) — ~$10–30/100 business cards — enterprise/partner API (contact sales) — US/international; largest product catalog, lowest price point

**Free tier:** No  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** No — custom print jobs are non-refundable after production begins

---

### Print and Ship a Physical Book on Demand

> A print-on-demand facility prints and binds a single copy of a book and ships it to a customer or address, with no inventory held.

**Providers**
- [Lulu](https://developers.lulu.com/) — ~$3–15/book (varies by page count, binding, color) + $1.75 fulfillment fee/order — free REST API at api.lulu.com — global; full developer API with no setup fee
- [IngramSpark](https://www.ingramspark.com/) — ~$4–18/book + setup fee per title — no public API; web portal only — global distribution via Ingram's wholesale network; best for bookstore/library distribution

**Free tier:** API is free to use; pay per print  
**Compliance required:** No (ISBN optional but recommended for retail distribution)  
**MCP exists:** No  
**Reversible:** No — printed books are fulfilled on demand; individual orders cannot be recalled after shipment

---

### Order Custom Labels, Stickers, or Decals

> A print shop produces custom die-cut or kiss-cut stickers/labels to your artwork and ships them.

**Providers**
- [Sticker Mule](https://www.stickermule.com/) — from ~$57/10 die-cut stickers (4"×4") — no order API (web UI only) — global; free proof within hours, 4-business-day production
- [Sticker Giant](https://www.stickergiant.com/) — ~$80/100 stickers — no public API — US; fast turnaround, strong for labels and roll stock

**Free tier:** No (Sticker Mule offers free sample packs)  
**Compliance required:** No (food-contact labels require FDA-compliant materials)  
**MCP exists:** No  
**Reversible:** No — custom print runs are non-returnable after proof approval

---

### Order Custom Embroidered Apparel

> A fulfillment provider embroiders your design onto a garment and ships it directly to the end customer (dropship) or to your inventory.

**Providers**
- [Printful](https://developers.printful.com/docs/) — ~$11–25/embroidered item (e.g., $11.48 for basic tee) — full REST API at developers.printful.com — global; 130+ embroiderable products, auto thread color detection, no MOQ
- [Printify](https://printify.com/printify-api/) — ~$10–22/embroidered item — REST API (Enterprise plan at $29/mo unlocks API + 20% discount) — global; larger print provider network

**Free tier:** Yes — Printful has no monthly fee (pay per order); Printify free plan exists but API requires paid plan  
**Compliance required:** No  
**MCP exists:** No  
**Reversible:** No — once in production, cancellation window is minutes; cannot be changed after start

---

## Domains & Infrastructure

### Register a Domain Name

> A domain name is registered in the global DNS registry under the chosen TLD, exclusively associated with the registrant for 1+ years.

**Providers**
- [Namecheap API](https://www.namecheap.com/support/api/intro/) — ~$8–15/yr — API key + billing — global; full domain lifecycle (search, register, manage, transfer); sandbox available
- [GoDaddy API](https://developer.godaddy.com/doc/endpoint/domains) — ~$10–20/yr — API key + billing — global; availability + registration + DNS management
- [Cloudflare Registrar API](https://blog.cloudflare.com/registrar-api-beta/) — at-cost pricing (no markup) — API key + billing — global; beta, at-cost pricing

**Free tier:** No — registration fees apply  
**Compliance required:** No — WHOIS accuracy required; some TLDs have residency requirements  
**MCP exists:** No  
**Reversible:** Yes — domains can be deleted within the add grace period (typically 5 days, free); after that, requires expiry or transfer

---

## Notarization & Signatures

### Notarize a Document (Remote Online Notarization)

> A document is notarized by a commissioned notary via a live audio-video session; legally valid in 45+ US states.

**Providers**
- [Notarize](https://www.notarize.com/) — ~$25/notarization — API key + billing — US (45 states + DC); integrates into CRM/LOS workflows; largest RON provider
- [Pactima](https://pactima.com/) — custom pricing — API key + billing — US; extensive API endpoints for workflow embedding
- [BlueNotary](https://bluenotary.us/) — ~$25/notarization — API key + billing — US; high-volume, SOC 2 + HIPAA compliant

**Free tier:** No  
**Compliance required:** Yes — legal in 45 states + DC; some document types (wills, adoption) have additional requirements  
**MCP exists:** No  
**Reversible:** No — notarized documents are official records

---

### Collect a Legally Binding E-Signature

> A document is sent to one or more signers who apply a legally binding electronic signature; the signed document is timestamped and stored.

**Providers**
- [DocuSign eSign API](https://developers.docusign.com/docs/esign-rest-api/) — $50–480/mo (40–100 envelopes) — API key + billing — US/international; industry standard; bulk send, template population, field placement
- [Dropbox Sign (HelloSign)](https://sign.dropbox.com/products/dropbox-sign-api) — from $25/mo; API plan from $75/mo — API key + billing — US/international; cleaner DX, free tier available

**Free tier:** Yes — Dropbox Sign has a limited free tier  
**Compliance required:** No — ESIGN Act and UETA make e-signatures legally equivalent to wet signatures in the US  
**MCP exists:** No  
**Reversible:** No — signed documents are executed; voiding requires agreement from all parties

---

## Miscellaneous High-Impact

### Place an Obituary in a Newspaper

> A paid death notice or obituary is published in print and/or online in a partnered newspaper, creating a public record of death.

**Providers**
- [Legacy.com](https://www.legacy.com/) — $50–500+/publication depending on outlet — consumer portal + partner API for funeral homes; covers 2,800+ US newspapers — US
- [Column](https://www.column.us/products-obituaries/) — custom pricing for funeral home partners — white-label API — US; multi-paper placement in one transaction

**Free tier:** No  
**Compliance required:** No — publications verify death information; fraudulent obituaries may result in legal liability  
**MCP exists:** No  
**Reversible:** No — once published in print, cannot be retracted; online versions can sometimes be edited or removed on request

---

### List Items for Sale on eBay or Amazon

> A product listing goes live on a public marketplace, making the item purchasable by millions of consumers worldwide.

**Providers**
- [eBay Sell APIs](https://developer.ebay.com/api-docs/) — free API access; eBay charges ~10–15% final value fee per sale — OAuth2, seller account required — global; full lifecycle API covering listings, orders, inventory, fulfillment, and payments
- [Amazon Selling Partner API (SP-API)](https://developer.amazonservices.com/) — free API access; Amazon charges 8–15% referral fee + optional FBA fees — LWA OAuth, approved developer account — global; programmatic listings, inventory, pricing, orders

**Free tier:** API access is free; you pay per sale  
**Compliance required:** Yes — both require seller account verification, tax information, and compliance with category-specific regulations (FDA for food/supplements, CPSC for toys)  
**MCP exists:** No  
**Reversible:** Yes — listings can be ended programmatically at any time before a sale

---

### Buy a Used Car Programmatically

> A binding purchase contract for a specific vehicle is executed, transferring legal ownership to the buyer upon delivery or pickup.

**Providers**
- [Marketcheck API](https://www.marketcheck.com/) — from ~$99/mo — REST API — US; inventory aggregation API covering millions of listings; does not execute purchases but enables programmatic search
- [Carvana](https://www.carvana.com/) — market price per vehicle — no public API; web/app only — US; fully online purchase flow but no developer API
- Note: No major used-car retailer exposes a public purchase API; Marketcheck for inventory discovery + manual purchase flow is the closest path

**Free tier:** No  
**Compliance required:** Yes — vehicle purchase requires valid driver's license, title transfer, and state registration  
**MCP exists:** No  
**Reversible:** Partial — Carvana offers 7-day return; CarMax 30-day return; neither is API-driven

---

### Sell a Car for an Instant Offer

> A binding cash offer is generated and accepted for a vehicle, obligating the buyer to purchase the car at the agreed price upon inspection.

**Providers**
- [Carvana Instant Offer](https://www.carvana.com/sell-my-car) — pays market value minus margin — no public API; web/app only — US; offer valid 7 days/1,000 miles, same-day pickup
- [CarMax Instant Offer](https://www.carmax.com/sell-my-car) — pays market value minus margin — no public API — US; offer valid 7 days, redeemable in-store
- [Vroom](https://www.vroom.com/sell) — pays market value minus margin — no public API — US; offer valid 2 days/250 miles
- Note: All three are consumer-only; no seller API exists

**Free tier:** N/A (seller receives payment)  
**Compliance required:** Yes — seller must hold clear title; lien release required if loan outstanding; odometer disclosure required by federal law  
**MCP exists:** No  
**Reversible:** Partial — offer can be declined before pickup; once vehicle is surrendered the transaction is final

---

### Adopt a Pet from a Shelter

> A shelter or rescue organization is connected with a prospective adopter, initiating an adoption application process that may result in legal transfer of animal custody.

**Providers**
- [Petfinder API](https://www.petfinder.com/developers/) — free — OAuth2 API key — US + Canada; 14,000+ shelters; read-only (find animals and shelters); actual adoption application happens on the shelter's own site
- [Adopt-a-Pet API](https://partner-apis.adoptapet.com/) — free for shelter partners — API key — US; 1,000+ shelters; partners can read, edit, and update pet info
- Note: No API completes the full adoption transaction; APIs surface listings only; the legal transfer requires shelter-side processing

**Free tier:** Yes  
**Compliance required:** No API-level compliance; actual adoption requires shelter's intake process (home checks, fees, contracts vary)  
**MCP exists:** No  
**Reversible:** Partial — a completed adoption agreement is a legal contract with the shelter

---

### Apply for a Mortgage

> A residential mortgage application is filed, initiating underwriting, credit checks, appraisal ordering, and regulatory disclosure obligations under TILA/RESPA.

**Providers**
- [Blend](https://blend.com/) — custom enterprise pricing — API + white-label embed — US; full digital origination API covering credit pulls, VOI/VOA, disclosures, and e-sign
- [Roostify (CoreLogic)](https://www.roostify.com/) — custom pricing — API + lender integration — US; document intelligence available as standalone API
- [Floify](https://floify.com/) — ~$99–500/mo per LO — Open API — US; LOS-agnostic POS with REST API for mortgage workflow automation

**Free tier:** No  
**Compliance required:** Yes — RESPA, TILA, ECOA, state mortgage licensing; lender must be a licensed originator; HMDA reporting triggered  
**MCP exists:** No  
**Reversible:** Yes — borrower can withdraw before closing; 3-day rescission right exists for refinances
