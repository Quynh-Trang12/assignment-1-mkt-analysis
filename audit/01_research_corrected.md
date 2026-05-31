# Corrected — 01_research_raw.md

> 📝 NOTE: Corrections applied from Stage 1–4 of the audit pipeline. See `audit/audit_log.md` for full details.

## Key corrected excerpts and inline changes

- Product name (official): "Trà nhãn vàng" [Source: https://cozy.vn/tra-nhan-vang/]

- Ingredients / composition (verified on Cozy page):
  - "Thành phần: Trà đen 100%" [Source: https://cozy.vn/tra-nhan-vang/]

- Net weight / formats (clarified):
  - Retail SKU: ~~"Hộp 25 Gói x 2g"~~ → `Hộp 25 gói × 2g (50g) — retail SKU; use Lotte Mart retail price for this SKU`  
  - Commercial / HORECA SKU: `100×2g (bulk) — commercial pha chế format; treat separately from retail SKU`  
  > 🔄 RESOLVED: separated retail (25×2g) and HORECA (100×2g) references and kept retail price tied to Lotte Mart listing.

- Certifications / quality claims (from Cozy site):
  - "Cozy Nhãn Vàng được sản xuất & đóng gói theo công nghệ từ Đức & Italia; ISO 22000, HACCP, GMP, Halal." [Source: Cozy]

- Price (retail, verified):
  - Lotte Mart listing: `34.300 ₫` [Verified metadata: https://www.lottemart.vn/...]  
  - Shopee listings: ~~(previously cited values)~~ → `> ⚠️ REPLACED: [UNVERIFIABLE — Shopee login/verification wall prevented direct scrape; price taken from marketplace snippet only]`  
  - Lazada: `> ⚠️ REPLACED: [search snippet only — unverified; product page blocked by reCAPTCHA]`

- Hybrid / translation note:
  - ~~"trà Cozy Gold Label sẽ mang lại..."~~ → `"[HYBRID PARAPHRASE — 'Gold Label' appears in some retailer metadata as an English translation; not a verbatim sentence on Cozy.vn]"`  
  > ⚠️ REMOVED: hybrid verbatim claim replaced with hedged note indicating translation/paraphrase.

- Pha chế (commercial use) claims:
  - Explicitly link pha chế suitability to HORECA / 100‑bag SKU. Remove any language that treats the 25‑bag retail box as equivalent for bulk commercial preparation.  
  > 🔄 RESOLVED: When discussing pha chế suitability, reference the 100‑bag HORECA SKU; when discussing household convenience and retail price, reference the 25×2g box.

- Shopee / Lazada derived content and customer ratings:
  - `[UNVERIFIABLE — login wall / reCAPTCHA]` — removed verbatim claims drawn solely from blocked pages; left a hedged summary where marketplace snippets were used.

- Dynamic metrics and social-media claims:
  - YouTube view counts and social follower counts left as cited but annotated with access-date: `Accessed 2026-05-31` (e.g., YouTube video ~6.6M views — note that view counts vary; recommend manual verification before submission).
  - Instagram account: `> ⚠️ INFERRED: Instagram account presence noted but some follower counts could not be verified; user must confirm.`


## Trace items left for manual verification
- Confirm in-store Lotte Mart price at time of visit (recommended).
- Verify Shopee price via manual browsing (or by logging into Shopee) if needed.
- Confirm Lazada product page content (login / reCAPTCHA required).

> ✅ All corrections preserve original structure; content edits are inline with visible evidence and annotated with hedges, notes, and removal traces.
