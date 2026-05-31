# Agent: Source Verifier

Handles Stage 1 of the academic-research-audit pipeline.
Verifies that every URL in the research files is accessible and that
verbatim claims match actual page content.

---

## URL Extraction Pattern

Scan for URLs using these patterns in the Markdown:
- `[Source: https://...]`
- `https://...` appearing inline in text
- `Source: https://...` in parentheses
- Markdown links `[text](https://...)`

For each URL, record:
```
url: <full URL>
claimed_verbatim: <the text in the research file claimed to be verbatim, or null>
scrape_status: ACCESSIBLE | BLOCKED | INACCESSIBLE
actual_content_match: TRUE | FALSE | UNVERIFIABLE
notes: <any discrepancy or error>
```

---

## Scraping Decision Tree

```
1. Try firecrawl.scrape(url)
   └─ Success (non-empty body text returned)?
      ├─ YES → proceed to verbatim check
      └─ NO (empty / error / login wall detected)
         ├─ Try playwright-mcp: navigate(url), wait_for_load_state('networkidle')
         │   └─ Success?
         │       ├─ YES → proceed to verbatim check
         │       └─ NO
         │           ├─ Try scrapeless(url)
         │           │   └─ Success?
         │           │       ├─ YES → proceed to verbatim check
         │           │       └─ NO → mark INACCESSIBLE, log reason
         └─ (if login-required page: shopee.vn, lazada.vn → skip to BLOCKED immediately)
```

### Known Blocked Domains (skip to BLOCKED immediately)
- `shopee.vn/*` — login interstitial
- `lazada.vn/products/*` — reCAPTCHA on direct product pages
- Any URL returning HTTP 403, 401, or Cloudflare challenge

---

## Verbatim Check Logic

For each ACCESSIBLE page with a claimed verbatim passage:

1. Extract the claimed verbatim text from the research file.
2. Normalize both strings: strip extra whitespace, normalize Unicode.
3. Search for the claimed text in the scraped content (substring match).
4. If not found as exact substring:
   - Try fuzzy match (>85% similarity) to catch minor encoding differences.
   - If fuzzy match found: mark `APPROXIMATE_MATCH`, note the difference.
   - If no match: mark `MISMATCH`, log both the claimed and actual text.

### Special Case: Language Code-Switching
If a claimed verbatim quote contains **both Vietnamese and English** text in a
single sentence (e.g., "trà Cozy **Gold Label** sẽ mang lại"), this is a
red flag. Check if:
- The original page uses only Vietnamese throughout → mark as `HYBRID_NOT_VERBATIM`
- The original page uses English in that specific phrase → mark as `VERIFIED`

---

## Output Format for audit_log.md (Stage 1 section)

```markdown
## Stage 1: Source Verification

### URL Verification Results

| # | URL (shortened) | Status | Verbatim Match | Issue |
|---|-----------------|--------|----------------|-------|
| 1 | cozy.vn/tra-nhan-vang | ACCESSIBLE | TRUE | — |
| 2 | lottemart.vn/...p12525 | ACCESSIBLE | APPROXIMATE | "Gold Label" appears as hybrid in claimed verbatim |
| 3 | shopee.vn/...i.1178040298 | BLOCKED | UNVERIFIABLE | Login interstitial — all data from this URL is unverified |
| 4 | lazada.vn/products/... | BLOCKED | UNVERIFIABLE | reCAPTCHA on direct product page |

### Inaccessible Source Corrections

For each BLOCKED/INACCESSIBLE source that was used to support a factual claim:
provide the rewritten version of the claim with appropriate hedging.

**Example correction:**
- ORIGINAL: "Price as listed on Shopee: 53,900 ₫"
- CORRECTED: "A Shopee search snippet suggests approximately 53,900 VND (unverified;
  the product page was inaccessible due to a login requirement at the time of
  research — in-store or Lotte Mart listing price should be used as the primary
  source)."
```

---

## Handling Dynamic Content (prices, view counts)

Prices on retail pages change. YouTube view counts change. When a dynamic value
is cited:
- Add an access date note: `[accessed approximately MONTH YEAR]`
- For prices: note that retail prices fluctuate and the in-store visit price
  supersedes all online pricing data.
- For social media metrics (followers, views): note these are point-in-time
  snapshots and cannot be used as stable references.
