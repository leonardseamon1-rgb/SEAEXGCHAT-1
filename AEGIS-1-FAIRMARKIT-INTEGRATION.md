# AEGIS-1 Fairmarkit Commercial Procurement Integration — Proposal v1.0
Date: 2026-11-20
Status: DESIGN ONLY — NO FAIRMARKIT ACCOUNT CONNECTED OR APP CODE CHANGED
Owner: Seamon Exchange LLC
Companion specification: AEGIS-1-MASTER-EXPANSION-v2.md

## Recommendation
Add Fairmarkit as a distinct commercial-opportunity channel to AEGIS-1, without assuming that Fairmarkit grants supplier-side bulk Marketplace access via API. First use its supported Marketplace filters and category-based email alerts; only connect authorized APIs once available endpoints, permissions, costs, and buyer-content rights are verified.

## Confirmed supplier features (official documentation)
- Supplier registration is free: https://docs.fairmarkit.com/suppliers/suppliers/getting-started/register-as-a-supplier
- Registered suppliers can view and respond to public Marketplace events even without a direct buyer invitation: https://docs.fairmarkit.com/suppliers/suppliers/marketplace-suppliers
- Marketplace event list includes title/event ID, buyer, created/closing dates; search, buyer/category filtering, and custom email alerts. Buyers may close early: https://docs.fairmarkit.com/suppliers/suppliers/marketplace-suppliers/find-marketplace-events
- Event details may contain terms, requirements, item lines and shipping needs; RFQs, RFIs, RFPs, reverse auctions have different obligations: https://docs.fairmarkit.com/suppliers/suppliers/events
- API key guide documents supplier-admin self-service API settings, but presence of API keys does NOT prove supplier accounts may bulk fetch all Marketplace events. Support may need to enable settings: https://developers.fairmarkit.com/docs/authentication-guide

## Legal and technical restrictions — NON-NEGOTIABLE
- Fairmarkit Terms prohibit automated scripts, bots, scrapers, harvesters or data extraction without written consent. Do not automate unauthorized browsing/scraping: https://www.fairmarkit.com/terms-of-service
- Buyer content belongs to buyer and is restricted to procurement participation; do NOT copy buyer confidential terms/content into Base44/Emergent/ChatGPT or store it off-portal without permission.
- Any integration must use an authorized supplier API endpoint in accordance with granted scope, rate limits, security requirements and buyer terms; never store API keys in GitHub or prompts.
- No automatic quote submission, emailing, purchases, pricing commitments or counter-offers. Human approval per submission.

## User-supplied marketplace leads (UNVERIFIED CURRENT STATUS; logged 2026-11-20)
- Perdue Farms: P2632691, 'Wire strippers - Bring to Natasha', listed close 2026-11-23.
- Perdue Farms: A425749, 'ZORO G5210737', listed close 2026-11-25.
- Perdue Farms: A425747, 'ULINE S-25501', listed close 2026-11-25.
- Honeywell Technologies: REQ03237454, closes 2026-11-27.
- Vistra Corp: 4006034 and 4006033, closes 2026-11-25.
- Perdue Farms: P2643315, closes 2026-11-23.
Dates and titles originate from user's pasted Fairmarkit listing; current status, access, quantity and commercial terms not verified.

## Proposed screening and database fields
MarketplaceSource, event_id, buyer_name, buyer_location, shipping_location, title, public/event-only status, sourcing_category, part_number, manufacturer, quantity, condition, close_date_local/timezone, line_items, lead_time, quote_currency, sourcing_confidence, match_type (exact/alternative/unclear), factory_new_evidence, supplier_quote_status, freight_estimate, cost_basis, funding_need, estimated_profit/margin, risk_flags, owner's decision, event_url, source_time, last_checked, permitted_data_storage_scope.
Search priorities: factory-new exact match; target gross margin and finance feasibility; deadlines; lowest-risk items; lower-value opportunities; geographic supplier preference Minnesota first. Commercial opportunities DO NOT inherently have federal small-business set-asides or DLA packaging clauses; apply buyer-specific requirements, not federal defaults blindly.

## Implementation phases
Phase A (no integrations): Complete Fairmarkit company profile; select suitable supplier categories; set email alerts; manually review 1-2 small exact-catalog-item events in the portal.
Phase B (email-to-worklist): Only where lawful and authorized, parse *notification metadata* from opted-in supplier emails into AEGIS's commercial leads queue, with confidentiality controls and source links. Review actual buyer-content restrictions before transfer.
Phase C (API assessment): Verify with Fairmarkit support whether supplier-admin API exposes list/search Marketplace events, notices/webhooks and read-only access; assess contractual consent, quotas and pricing before any implementation.
Phase D (read-only connection): If expressly authorized, implement read-only ingestion, exact-match checks, deadlines, source links and audit logs. No bid submission from agent.
Phase E (owner-approved quoting): Optional official API/portal-supported bid workflow only if expressly permitted; every submission requires user approval and logged evidence.

## Next user actions
- Finish Fairmarkit six-step supplier profile; verify Company description, actual key customers, industrial parts categories.
- In Marketplace, select relevant categories and Create Email Alert. Prefer daily alert initially if available.
- Review Perdue Farms Zoro and Uline requests, exact line items and terms in Fairmarkit directly.
- If API integration desired, ask Fairmarkit support: 'Does Supplier Admin API support read-only listing/searching Marketplace events and retrieving event details for our company's account? Are API access and external processing/recordkeeping permitted? Is there a cost?'
