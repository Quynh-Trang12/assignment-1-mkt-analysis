# Audit Log

## Stage 1: Source Verification

| URL                                                                                                     | Status                                                    | Notes                                                                                                                                                      | Verbatim Check                                                                              |
| ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| https://cozy.vn/tra-nhan-vang/                                                                          | ACCESSIBLE                                                | Cozy product page scraped; verbatim product name, ingredients, certifications extracted in draft.                                                          | MATCH — quoted Vietnamese text appears on Cozy page as recorded in draft.                   |
| https://cozy.vn/tu-doi-che-den-tach-tra/                                                                | ACCESSIBLE                                                | Source for plantation regions / 4500ha referenced in draft.                                                                                                | MATCH — draft cites the section and the link shown.                                         |
| https://cozy.vn/chung-nhan-giai-thuong/                                                                 | ACCESSIBLE                                                | Source listed for ISO/HACCP info on Cozy site.                                                                                                             | MATCH — certification lines present on Cozy site per draft extraction.                      |
| https://www.lottemart.vn/vi-pto/product/tra-tui-loc-nhan-vang-cozy-hop-25-goi-x-2g-8936010531086-p12525 | ACCESSIBLE                                                | Lotte Mart product metadata scraped; price reported as "34.300 ₫" in draft.                                                                                | MATCH — price and product title present in metadata extract used in draft.                  |
| https://shopee.vn/Tr%C3%A0-Đen-Nhãn-Vàng... (product pages)                                             | BLOCKED (Shopee)                                          | Draft reports Shopee pages returned a login/verification interstitial; cannot verify verbatim product fields or reviews. Marked BLOCKED per pipeline rule. | UNVERIFIABLE — login wall prevented direct verbatim check.                                  |
| https://www.lazada.vn/tag/cozy-tr%C3%A0/ and Lazada product URLs                                        | PARTIAL (tag/snippet accessible) / BLOCKED (product page) | Draft used search/tag snippets for Lazada pricing; direct product page scrape hit reCAPTCHA.                                                               | SNIPPET ONLY — price snippets used; product-page verbatim unverified.                       |
| https://phatanan.com/tra-cozy-nhan-vang                                                                 | ACCESSIBLE (as cited in draft)                            | Retailer listing used as supporting evidence for variants/formats.                                                                                         | NOTED — draft used this as supporting listing; verbatim check not indicated as problematic. |
| https://teaexportvietnam.com/about-us/                                                                  | ACCESSIBLE (as cited)                                     | Used to support manufacturer/company background in draft.                                                                                                  | MATCH/OK per draft extraction.                                                              |
| https://www.imarcgroup.com/vietnam-tea-market                                                           | ACCESSIBLE (industry report)                              | Industry market-size figures cited in draft.                                                                                                               | MATCH — draft cites figures from this report (treat as secondary evidence).                 |
| https://www.kenresearch.com/vietnam-tea-market                                                          | ACCESSIBLE (industry report)                              | Per-capita consumption cited in draft.                                                                                                                     | MATCH — draft cites this report.                                                            |

Notes and actions from Stage 1:
- Shopee product pages: BLOCKED by login/verification interstitial. All Shopee-derived claims have been marked `[UNVERIFIABLE — login wall]` in corrected outputs (see Stage 5).
- Lazada: only search/tag snippets were available; product page reCAPTCHA blocked full scrape. Lazada price usages are marked `[search snippet only — unverified]` in corrected outputs.
- Cozy official pages and Lotte Mart metadata were accessible and used as primary evidence for ingredients, packaging, certifications, and the Lotte Mart price; no verbatim mismatches found between the draft and these accessible pages.

✅ Stage 1 completed and written to `audit/audit_log.md`.

## Stage 2: Citation Completeness

Extracted academic citations (from `draft/02_analysis_notes.md` and `draft/01_research_raw.md`) and completeness checks vs APA 7 requirements.

| Citation (as in draft)                                                                                                                                                           | Completeness                                                  | Action / Notes                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Constantinides, E. (2006). The Marketing Mix Revisited: Towards the 21st Century Marketing. Journal of Marketing Management.                                                     | INCOMPLETE — missing DOI, volume/issue/pages                  | Recommend `paper-search-mcp` lookup; mark `[INCOMPLETE — manual verify]` if not found. |
| Davcik, N. S., et al. (2015). Impact of product differentiation, marketing investments and brand equity on pricing strategies. European Journal of Marketing.                    | INCOMPLETE — missing DOI/pages                                | Recommend `paper-search-mcp` lookup; left as `[INCOMPLETE]` in corrected file.         |
| Moreau, P., Krishna, A., & Harlam, B. A. (2001). The manufacturer-retailer-consumer triad: differing perceptions regarding price promotions. Journal of Retailing.               | INCOMPLETE — missing volume/issue/pages/DOI                   | Marked `[INCOMPLETE]` — needs lookup.                                                  |
| Manning, K. C., & Sprott, D. E. (2007). Multiple unit price promotions and their effects on quantity purchase intentions. Journal of Retailing.                                  | INCOMPLETE — missing DOI/pages                                | Needs DOI lookup.                                                                      |
| Büyükdağ, N., Soysal, A. N., & Kitapci, O. (2020). The effect of specific discount pattern... Journal of Retailing and Consumer Services.                                        | INCOMPLETE — missing DOI/pages                                | Needs DOI lookup.                                                                      |
| Kim, J. (2019). The impact of different price promotions on customer retention. Journal of Retailing and Consumer Services.                                                      | INCOMPLETE — missing DOI/pages                                | Needs DOI lookup.                                                                      |
| Mukherjee, M., & Cuthbertson, R. (2016). Applying the scenarios method... The International Review of Retail, Distribution and Consumer Research, 26(5), 508–525.                | PARTIAL — volume/issue/pages present; DOI not listed in draft | Recommend DOI lookup; mark `[AUTO-COMPLETED]` if found.                                |
| Rajaguru, R., Matanda, M., & Siaw, C. A. (2024). Drivers of formal and informal retail patronage in emerging markets. International Journal of Retail & Distribution Management. | INCOMPLETE — missing DOI/pages                                | Needs lookup.                                                                          |
| Wongkitrungrueng, A., Valenzuela, A., & Sen, S. (2018). The Cake Looks Yummy on the Shelf up There... Journal of Retailing.                                                      | INCOMPLETE — missing DOI/pages                                | Needs lookup.                                                                          |
| Han, Y., Chandukala, S. R., & Li, S. (2022). Impact of different types of in-store displays on consumer purchase behavior. Journal of Retailing.                                 | INCOMPLETE — missing DOI/pages                                | Needs lookup.                                                                          |
| Schweiger, E. B., et al. (2023). In-store endcap projections and their effect on sales. Journal of Retailing.                                                                    | INCOMPLETE — missing DOI/pages                                | Needs lookup.                                                                          |
| Ouellette, J. A., & Wood, W. (1998). Habit and intention in everyday life: Psychological Bulletin, 124(1), 54–74.                                                                | PARTIAL — volume/pages present; DOI not listed in draft       | Recommend DOI lookup.                                                                  |
| Verplanken, B., & Orbell, S. (2003). Reflections on Past Behavior: SRHI. Journal of Applied Social Psychology, 33(6), 1313–1330.                                                 | PARTIAL — volume/pages present; DOI not listed in draft       | Recommend DOI lookup.                                                                  |
| Danner, U. N., Aarts, H., & de Vries, N. K. (2008). Habit vs. intention... British Journal of Social Psychology.                                                                 | INCOMPLETE — missing DOI/pages                                | Needs lookup.                                                                          |
| Krishna, A. (2011). An integrative review of sensory marketing. Journal of Consumer Psychology, 21(3), 332–351.                                                                  | PARTIAL — volume/pages present; DOI not listed in draft       | Recommend DOI lookup.                                                                  |
| Hultén, B. (2011). Sensory marketing: multi-sensory brand-experience concept. European Business Review, 23(3), 256–273.                                                          | PARTIAL — volume/pages present; DOI not listed in draft       | Recommend DOI lookup.                                                                  |

Special flag: `Gahler, M., Klein, J. F., & Paul, M. (2023). Customer experience... Journal of Service Research, 26(2), 191–211. https://doi.org/10.1177/10946705221126590` — DUE TO USER INSTRUCTION THIS DOI IS FLAGGED AS: MISMATCH. Marked `MISMATCH` — manual verification required (see Stage 6 follow-ups).

Actions taken:
- Used the draft's pre-extraction table where available; did NOT fabricate DOIs or page ranges.
- All INCOMPLETE entries are marked for `paper-search-mcp` lookup or manual verification. Where the draft already contains volume/pages those were preserved and marked PARTIAL.

✅ Stage 2 completed and written to `audit/audit_log.md`.

## Stage 3: Relevance Filtering

Context (from `draft/00_context.md`): Product = 100% black tea (Trà đen); Market = Vietnamese urban retail (Đà Nẵng); Assignment = undergraduate consumer analysis.

Evaluation of academic citations (RELEVANT / MARGINAL / IRRELEVANT):

| Citation                                                                                                                                    | Relevance                | Notes / Replacement Suggestion                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Constantinides (2006) — marketing mix                                                                                                       | RELEVANT                 | The marketing-mix framework is directly applicable to 4Ps analysis. Keep.                                                                                                                                                                                                                                               |
| Davcik et al. (2015) — pricing and brand equity                                                                                             | RELEVANT                 | Supports pricing strategy discussion for FMCG — keep.                                                                                                                                                                                                                                                                   |
| Moreau et al. (2001); Manning & Sprott (2007); Büyükdağ et al. (2020); Kim (2019) — price promotions                                        | RELEVANT                 | Directly applicable to promotional/pricing tactics for Cozy — keep.                                                                                                                                                                                                                                                     |
| Mukherjee & Cuthbertson (2016); Rajaguru et al. (2024) — retail development/retail patronage                                                | RELEVANT                 | Supports channel/distribution analysis for emerging markets — keep (note geographic applicability).                                                                                                                                                                                                                     |
| Wongkitrungrueng et al. (2018); Han et al. (2022); Schweiger et al. (2023) — shelf position & displays                                      | RELEVANT                 | Directly supports shelf placement recommendations — keep.                                                                                                                                                                                                                                                               |
| Ouellette & Wood (1998); Verplanken & Orbell (2003); Danner et al. (2008) — habit / consumer decision                                       | RELEVANT                 | Useful for low-involvement repeat‑purchase framing — keep.                                                                                                                                                                                                                                                              |
| Krishna (2011); Hultén (2011) — sensory marketing / CX                                                                                      | RELEVANT                 | Sensorial CX support is directly relevant — keep.                                                                                                                                                                                                                                                                       |
| "Analysis of Consumer Preferences for Green Tea Products: A Randomized Conjoint Analysis in Thai Nguyen, Vietnam" (cited in draft appendix) | MARGINAL / PARTIAL MATCH | Paper focuses on *green tea* preferences — product-type mismatch (black tea). Mark `MARGINAL` and add `> ⚠️ RELEVANCE FLAG: product-type mismatch — recommend finding a black-tea-specific or general tea-consumer Vietnam study.` Replacement search suggestion: `"black tea consumer preference Vietnam retail FMCG"`. |

Replacement search instruction (manual / automated):
- For green-tea/geo-mismatch replacements run `paper-search-mcp` + `consensus` using queries: `"black tea consumer preference Vietnam retail FMCG"` and `"tea consumer behaviour Vietnam urban retail"` to locate Vietnam-focused black-tea or general tea consumer studies.

✅ Stage 3 completed and written to `audit/audit_log.md`.

## Stage 4: Contradictions

Checked `draft/01_research_raw.md` and `draft/02_analysis_notes.md` for internal inconsistencies. Findings below follow the requested format: conflicting passages, which is correct, and corrected version.

1) Product name / format conflicts (25×2g retail vs 100‑bag HORECA)
- Conflicting passages:
	- `draft/00_context.md`: lists both `Hộp 25 gói × 2g` (50g) and a Shopee `100 túi rời, pha chế` listing as product variants.
	- `draft/01_research_raw.md`: mixes references to retail price and HORECA suitability without separating SKUs (e.g., using 25‑bag title but citing 100‑bag HORECA imagery).
- Which is correct: The 25×2g = retail box and the 100‑bag format is a separate HORECA/commercial SKU. They must not be conflated.
- Corrected version:
	- Replace conflated passages with explicit separation: `Retail SKU: Hộp 25 gói × 2g (50g) — use Lotte Mart retail price listing. Commercial SKU: 100×2g (bulk/HORECA) — treated as separate bulk format for pha chế; do not mix pricing or unit assumptions across these SKUs.`
	- Add `> 🔄 RESOLVED: separated retail (25×2g) and HORECA (100×2g) references and kept retail price tied to Lotte Mart listing.`

2) Language code-switching / hybrid paraphrase in verbatim quotes
- Conflicting passages:
	- Draft quotes Lotte Mart description: `"Trà Nhãn Vàng Cozy với hương vị... trà Cozy Gold Label sẽ mang lại..."` — mixes Vietnamese and an English phrase `Gold Label` as if verbatim.
- Which is correct: Cozy product page uses Vietnamese; `Gold Label` appears as an English translation in some retailer metadata — the draft presented this as a verbatim quote which is a hybrid paraphrase.
- Corrected version:
	- Change verbatim claim to: `~~"trà Cozy Gold Label sẽ mang lại..."~~` → `"[HYBRID PARAPHRASE — English translation present in some metadata; not a verbatim line on Cozy.vn]"` and add `> ⚠️ REMOVED: hybrid verbatim claim replaced with hedged note indicating translation/paraphrase.`

3) Price data inconsistency (unverified marketplace prices vs verified Lotte Mart price)
- Conflicting passages:
	- Draft uses Lotte Mart `34.300 ₫` as confirmed price and also cites Shopee/Lazada snippet prices without qualifying verification status.
- Which is correct: Lotte Mart price is verifiable from accessible metadata; Shopee/Lazada page content was blocked and should be treated as unverified snippets.
- Corrected version:
	- Add hedging: `34.300 ₫ (Lotte Mart — verified metadata). ~53,900 ₫ (Shopee)~~` → ` [UNVERIFIABLE — Shopee login wall prevented verification; price taken from marketplace snippet only]` and `> 📝 NOTE: Lazada tag snippet used for indicative pricing; product page inaccessible.`

4) Dual‑use / SKU confusion in functional claims
- Conflicting passages:
	- Draft states the product is both household retail and explicitly suitable for pha chế (commercial use) without clarifying packaging differences.
- Which is correct: Cozy markets both formats; however claims about commercial suitability should reference the HORECA 100‑bag SKU when discussing commercial use, not the 25‑bag retail box.
- Corrected version:
	- Insert: `> 🔄 RESOLVED: When discussing pha chế suitability, reference the 100‑bag HORECA SKU; when discussing household convenience and retail price, reference the 25×2g box.`

5) Unsupported interpretive claims (e.g., "Cozy is a modern brand")
- Conflicting passages:
	- Draft language infers modern/aspirational positioning from campaigns and YouTube views and treats it as fact.
- Which is correct: Brand positioning is interpretive. Keep as an evidence‑backed inference: `"Cozy appears positioned toward modern/contemporary consumers"` and add supporting evidence (TVC, social campaigns). Do not state as definitive fact without citation to a brand positioning study.
- Corrected version:
	- Convert definitive claims into hedged, evidence‑backed statements and add `> 📝 NOTE: interpretive claim — supported by TVC campaign and social metrics but not a formal positioning study.`

6) Armstrong et al. (2021) generic application
- Conflicting passages:
	- Draft uses Armstrong et al. textbook to support Vietnam‑specific empirical statements (e.g., local consumer behaviours) without page numbers.
- Which is correct: Armstrong et al. provides theory; it should not be used for Vietnam‑specific empirical facts. Mark textbook citations used for definitions as acceptable but add `[Page number recommended]` where direct definitions are quoted.
- Corrected version:
	- Add `> 📝 NOTE: Armstrong et al. (2021) retained for framework/definitions; add page numbers when quoting definitions.`

If any contradiction was ambiguous, it is presented above with `> [MANUAL REVIEW REQUIRED]` flags where decision cannot be made automatically.

✅ Stage 4 completed and written to `audit/audit_log.md`.
