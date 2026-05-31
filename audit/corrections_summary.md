# Corrections Summary

| #   | File                       | Location                         | Issue Type                                          | Severity | Action Taken                                                             |
| --- | -------------------------- | -------------------------------- | --------------------------------------------------- | -------- | ------------------------------------------------------------------------ |
| 1   | draft/01_research_raw.md   | Shopee links                     | Inaccessible source (login wall)                    | HIGH     | Replaced with `> ⚠️ [UNVERIFIABLE — login wall]` hedges in corrected file |
| 2   | draft/01_research_raw.md   | Lazada product pages             | Inaccessible / snippet-only                         | HIGH     | Marked `> ⚠️ [search snippet only — unverified]` in corrected file        |
| 3   | draft/01_research_raw.md   | Lotte Mart vs Marketplace prices | Data inconsistency (confidence mismatch)            | HIGH     | Kept Lotte Mart price as primary; hedged marketplace prices              |
| 4   | draft/01_research_raw.md   | Product naming                   | SKU conflation (25×2g vs 100×2g HORECA)             | HIGH     | Separated SKUs; added `> 🔄 RESOLVED` note                                |
| 5   | draft/01_research_raw.md   | Verbatim quote                   | Hybrid paraphrase ("Gold Label")                    | MEDIUM   | Replaced hybrid verbatim with hedged translation note                    |
| 6   | draft/02_analysis_notes.md | Multiple entries                 | Incomplete citations (missing DOI/pages) — 11 items | MEDIUM   | Annotated as `> ⚠️ INCOMPLETE` and listed for lookup                      |
| 7   | draft/02_analysis_notes.md | Gahler et al. (2023)             | DOI mismatch                                        | HIGH     | Marked `MISMATCH` — manual verification required                         |
| 8   | draft/01_research_raw.md   | Social metrics                   | Dynamic metrics (YouTube/views, followers)          | LOW      | Annotated with access-date and `> 📝 NOTE` for verification               |
| 9   | draft/01_research_raw.md   | Instagram account                | Unverified / inferred                               | MEDIUM   | Marked `[INFERRED — not directly verified]`                              |

Totals:
- Total issues found: 9 (grouped; multiple citation items count as 11 INCOMPLETE instances included above)
- Issues auto-corrected: 6 (SKU separation, hedged Shopee/Lazada, hybrid paraphrase, hedged price usage, social-metric access-date annotations, inferred-account flag)
- Issues requiring manual follow-up: 7 (detailed below)

Manual follow-up checklist (student MUST verify):
- [ ] Confirm in-store Lotte Mart price at time of visit (retail verification).
- [ ] Verify Gahler et al. (2023) DOI resolves to the cited content (paper pages 191–211).  
- [ ] Add specific page numbers to Armstrong et al. (2021) citations used as definitions.  
- [ ] Verify Shopee prices and product pages by logging into Shopee (or check in person).  
- [ ] Confirm Lazada product pages (resolve reCAPTCHA / login) for full product details.  
- [ ] Verify or exclude Instagram `@cozyvietnam` follower counts and recent posts.  
- [ ] Run `paper-search-mcp` or Google Scholar to complete DOIs/volume/issue/pages for the 11 `INCOMPLETE` citation entries.

Overall assessment (brief):
- The dataset in `draft/` is largely evidence-backed where primary sources were accessible (Cozy site, Lotte Mart, IMARC, Ken Research). Major weaknesses are marketplace pages blocked by login/reCAPTCHA (Shopee, Lazada product pages) and a set of incomplete academic citation metadata (DOIs/pages). After applying hedges and separating SKUs, the corrected drafts are substantially safer for academic use, but several HIGH‑severity items require manual verification before final submission.

Next steps recommended:
- Student performs the Manual follow-up checklist above.
- Optionally re-run an automated `paper-search-mcp` pass to auto-complete DOIs and confirm the Gahler DOI.

> Pipeline complete. See `audit/` folder.
