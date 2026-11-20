# AEGIS-1 Master Expansion Blueprint v2.0
Owner: Seamon Exchange LLC · CAGE 210G7
Status: PROPOSED DEVELOPMENT SPECIFICATION — not implemented in Base44 or Emergent
Date: 2026-11-20
Existing Base44 application: 6b002490eecf0e5038f70903
Existing source repository: leonardseamon1-rgb/SEAEXGCHAT-1

## Mission
Build an owner-governed procurement intelligence and execution assistant that discovers manageable government product opportunities, confirms eligibility, verifies exact factory-new sources, learns from award history, evaluates margins and cash flow, prepares but never sends outreach or bids without approval, and records evidence. Support DLA DIBBS, SAM.gov, Minnesota SWIFT, county/local opportunities as data access allows.

## Owner mandatory defaults (never silently override)
- Small-business set-aside opportunities are the primary search filter; check NAICS size standards, nonmanufacturer rule/waivers and procurement-specific eligibility. Unrestricted opportunities only if owner enables.
- Prioritize lower-value/feasible opportunities. Proposed $25,000 cap is NOT owner-approved; keep numeric value configurable and unset until owner confirms.
- Exact approved manufacturer, CAGE, part number and applicable NSN FIRST. Verify actual product and acquisition restrictions. No inference of approved source merely from past award.
- Factory NEW and unused by default. Rebuilt, remanufactured, refurbished, used, surplus and alternatives held for solicitation-specific written acceptability review. New surplus is NOT automatically equivalent to factory new.
- Alternative part research is secondary and separately labeled. Draft clarification request to solicitation contracting officer; no claim of approval without applicable written contracting authority decision/formal source approval.
- Supplier search geography: Twin Cities / Brooklyn Center first, then rest Minnesota, adjacent Midwest, nationally; geography is preference not reason to reject a uniquely qualified farther source.
- Never automatically send RFQs, emails, bids, purchase orders, sign documents, accept financing or otherwise commit the owner. Explicit owner approval per action.
- No restricted technical data, CUI, export-controlled drawings, credentials or proprietary quotes to external cloud tools without verified authority and a suitable approved security boundary. A UI banner is not a technical security guarantee.
- Every research output needs official/source link, retrieval time, uncertainty and evidence status. Claims must not be fabricated.
- Test with synthetic records and confirmed publicly releasable metadata. Do not run real procurement automation on a synthetic exercise.

## Modules
1. Solicitation ingestion: DIBBS, SAM.gov, MN SWIFT, county resources; solicitation and amendments, deadlines/timezones, line items, NSN, PSC, NAICS, set-aside, approved sources, drawing restrictions, quantity, delivery, packaging, inspection and quality clauses. Re-check before bid.
2. Supplier intelligence: exact OEM/authorized-distributor search, credible evidence and traceability, verified-capability versus prospect statuses, supplier contact, location, price, quote expiration, lead time, packaging capacity; duplicate detection; source URLs; pipeline history.
3. Historical award intelligence: identify past award winner, UEI/CAGE if available, recipient location versus performance versus shipping destination (not assumed identical), award date, award amount and unit price if actually available; quantity, scope and price normalization.
4. Agency and competitor intelligence: departments/subagencies/contracting offices; historical obligations, recurring purchases, active and upcoming work, forecasts, recompetes, sources sought, office contacts, responsible contracting officer, prime/subcontractor relationships, vehicles and publicly disclosed interested vendors. Never characterize interested vendors as proven bidders or expose confidential bid prices.
5. Contract finances: acquisition + tax if applicable + packaging + shipping + quality checks + platform costs + labor + financing costs, target margin, cash requirement, supplier terms, uncertainty; line-of-credit need and lender matches are leads, not approvals; invoice factoring only where eligible receivables exist.
6. Bid eligibility/readiness: independent compliance gates (set-aside, technical exactness, factory-new, source traceability, packaging, delivery, cybersecurity/export restrictions, nonmanufacturer, financing). BID/HOLD/PASS with HOLD when missing evidence. Competitive-readiness score separate from legal/technical eligibility; confidence and assumptions displayed. PWin estimates cannot be treated as calibrated winning probabilities without measured track record.
7. Workflow: draft technical clarification emails, supplier RFQs, packaging RFQs, capability statements, compliance matrix, amendment reminders, follow-up tasks. All sends/quotes/submissions owner-approved, audited.
8. Data integrity, security and governance: source-of-truth link, timestamps, provenance, role-based permissions, review queue, audit logs, backup/version control, minimal scoped OAuth/API tokens, encryption and retention rules, post-award feedback loop. Hard policy controls immutable by autonomous agents.
9. Quality testing: synthetic fixture TEST-AEGIS-001 with manufacturer AEGIS Test Manufacturing, fictional CAGE TEST1, part AEGIS-HHCS-100, qty 100 EA; validate extraction of line item/manufacturer/part/CAGE and amendments; confirm no actual sourcing or outbound outreach for test records. Existing Base44 extraction previously missed manufacturer/part/CAGE; retest needed.

## Official data sources researched (2026-11-20)
- https://www.usaspending.gov/ and https://api.usaspending.gov/docs/endpoints (award search, recipient and place-of-performance locations, subawards, agency spending; award value is not unit price by default).
- https://sam.gov/contracting and https://open.gsa.gov/api/get-opportunities-public-api/ (opportunities); https://open.gsa.gov/api/contract-awards/ (awards, account/API access may be needed).
- https://www.dibbs.bsm.dla.mil/ DLA supply-specific solicitation and award records; sensitive technical access restrictions apply.
- https://mn.gov/admin/osp/vendors/overview-for-vendors/ (Minnesota SWIFT vendor resources).
- CLEATUS agent/MCP at https://www.cleat.ai/agents and https://www.cleat.ai/api/mcp/mcp — evaluate pricing, permission, licensing and data coverage before connecting; not yet integrated.

## Suggested build order
Phase 0: backup live Base44 app data; baseline capabilities; confirm paid-tier access, quotas and pricing; record tests. Do not upgrade before evaluating.
Phase 1: exact factory-new source search and verifiable supplier database; robust PDF parsing and screening.
Phase 2: official award data connection (USAspending + SAM award API); geographies, incumbent discovery, comparable unit-cost evidence.
Phase 3: agency / competitor / forecast dashboard and usable county/state sources.
Phase 4: full landed-cost, credit requirement and conditional bid/readiness score.
Phase 5: approved workflow automations and cross-platform integrations, test+security audits.

## Integration / cost safeguards
GitHub is the versioned source of truth; Base44 remains the working UI until deliberate migration. Emergent is an optional build/testing environment and CLEATUS an optional external intelligence feed. Track recurring subscription fees, per-message build credits, integration/runtime costs, rate limits, OAuth scopes and renewal/cancellation dates. Avoid recreating paid data subscriptions if official API supplies the needed fields; don't assume public APIs contain DLA-specific exact source or NSN detail.

## Open items
- Owner to set preferred max contract value / whether all amounts or flexible tier.
- Confirm whether Base44 paid subscription is needed for GitHub sync and APIs for selected plan.
- Verify API field availability, data accuracy, no guaranteed shipping location in USAspending.
- Confirm county $168,000 opportunity identity before assigning PWin scorecard to a specific record.
- Confirm actual availability of credit line preaward, not merely factoring.
