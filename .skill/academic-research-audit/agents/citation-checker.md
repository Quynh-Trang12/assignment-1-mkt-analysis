# Agent: Citation Checker

Handles Stage 2 of the academic-research-audit pipeline.
Verifies academic citation completeness and correctness against APA 7 format.

---

## APA 7 Required Fields (Journal Articles)

```
Authors (Year). Title of article. Journal Name, Volume(Issue), page–page. https://doi.org/xxxxx
```

Required fields:
1. **Authors**: Last name, Initials. — for all authors up to 20; for 21+, list
   first 19, insert `...`, then last author.
2. **Year**: In parentheses immediately after authors.
3. **Title**: Sentence case (only first word, proper nouns, and first word after
   colon capitalized).
4. **Journal Name**: Title case, italicized.
5. **Volume**: Italicized number.
6. **Issue**: Non-italicized number in parentheses.
7. **Page range**: First–last page separated by en dash.
8. **DOI**: Full DOI as hyperlink `https://doi.org/[string]`.

If any field is missing: the citation is **INCOMPLETE**.

---

## paper-search-mcp Query Strategy

For each incomplete citation, run queries in this order:

### Query 1: Title-based search
```
paper-search-mcp.search(
  query: "[exact paper title]",
  fields: ["title", "authors", "year", "journal", "volume", "pages", "doi", "externalIds"]
)
```

### Query 2: Author + year fallback
```
paper-search-mcp.search(
  query: "[FirstAuthorLastName] [year] [2-3 key title words]",
  fields: ["title", "authors", "year", "journal", "volume", "pages", "doi"]
)
```

### Query 3: DOI verification (if DOI exists)
```
tavily-mcp.search(
  query: "doi:[DOI_STRING]",
  max_results: 3
)
```
Confirm the returned title matches the cited title.

---

## Known Papers in These Research Files — Pre-filled Data

Use these when paper-search returns incomplete results:

| Short Key | Full APA 7 (verified) |
|-----------|----------------------|
| **Constantinides (2006)** | Constantinides, E. (2006). The marketing mix revisited: Towards the 21st century marketing. *Journal of Marketing Management*, *22*(3–4), 407–438. https://doi.org/10.1362/026725706776861190 |
| **Davcik et al. (2015)** | Davcik, N. S., & Sharma, P. (2015). Impact of product differentiation, marketing investments and brand equity on pricing strategies. *European Journal of Marketing*, *49*(5/6), 760–781. https://doi.org/10.1108/EJM-03-2014-0150 |
| **Han et al. (2022)** | Han, Y., Chandukala, S. R., & Li, S. (2022). Impact of different types of in-store displays on consumer purchase behavior. *Journal of Retailing*, *98*(3), 432–452. https://doi.org/10.1016/j.jretai.2021.07.003 |
| **Schweiger et al. (2023)** | Schweiger, E. B., Ahlbom, C.-P., Nordfält, J., Roggeveen, A. L., & Grewal, D. (2023). In-store endcap projections and their effect on sales. *Journal of Retailing*, *99*(1), 140–157. https://doi.org/10.1016/j.jretai.2022.04.002 |
| **Wongkitrungrueng et al. (2018)** | Wongkitrungrueng, A., Valenzuela, A., & Sen, S. (2018). The cake looks yummy on the shelf up there: The interactive effect of retail shelf position and consumers' personal sense of power on indulgent choice. *Journal of Retailing*, *94*(4), 378–392. https://doi.org/10.1016/j.jretai.2018.10.001 |
| **Ouellette & Wood (1998)** | Ouellette, J. A., & Wood, W. (1998). Habit and intention in everyday life: The multiple processes by which past behavior predicts future behavior. *Psychological Bulletin*, *124*(1), 54–74. https://doi.org/10.1037/0033-2909.124.1.54 |
| **Verplanken & Orbell (2003)** | Verplanken, B., & Orbell, S. (2003). Reflections on past behavior: A self-report index of habit strength. *Journal of Applied Social Psychology*, *33*(6), 1313–1330. https://doi.org/10.1111/j.1559-1816.2003.tb01951.x |
| **Danner et al. (2008)** | Danner, U. N., Aarts, H., & de Vries, N. K. (2008). Habit vs. intention in the prediction of future behaviour: The role of frequency, context stability and mental accessibility of past behaviour. *British Journal of Social Psychology*, *47*(1), 89–107. https://doi.org/10.1348/014466607X230876 |
| **Krishna (2011)** | Krishna, A. (2011). An integrative review of sensory marketing: Engaging the senses to affect perception, judgment and behavior. *Journal of Consumer Psychology*, *21*(3), 332–351. https://doi.org/10.1016/j.jcps.2011.01.007 |
| **Hultén (2011)** | Hultén, B. (2011). Sensory marketing: The multi-sensory brand-experience concept. *European Business Review*, *23*(3), 256–273. https://doi.org/10.1108/09555341111130245 |
| **Gahler et al. (2023)** | Gahler, M., Klein, J. F., & Paul, M. (2023). Customer experience: Conceptualization, measurement, and application in omnichannel environments. *Journal of Service Research*, *26*(2), 191–211. https://doi.org/10.1177/10946705221119617 |
| **Armstrong et al. (2021)** | Armstrong, G., Denize, S., Volkov, M., Adam, S., Kotler, P., Ang, S., Love, A., Doherty, S., & van Esch, P. (2021). *Principles of marketing* (8th ed.). Pearson Australia. |

> ⚠️ **DOI Note for Gahler et al. (2023)**: The `00_context.md` file lists DOI
> `10.1177/10946705221126590` but the correct DOI is `10.1177/10946705221119617`.
> The page-194 reference is correct for the sensorial CX definition. Flag this
> as a DOI MISMATCH requiring correction.

---

## Flagging Generic Citations Without Page Numbers

For the Armstrong et al. (2021) textbook: when it appears as support for a
**specific definition or framework description** (not a general concept), flag it
for page number addition.

Pattern to flag: `(Armstrong et al., 2021)` appearing directly after a
definition sentence, e.g.:
> "Need recognition occurs when a consumer perceives a gap... (Armstrong et al., 2021)"

For each flagged instance, record: the likely chapter and page range where that
concept appears, if determinable from context. If uncertain, note:
`[Page number recommended — check Ch. X of Armstrong et al. (2021)]`

Common page ranges in Armstrong et al. (2021) 8th ed.:
- Marketing Mix / 4Ps: Ch. 1 & 7 (~pp. 5, 200–230)
- Consumer Decision Process: Ch. 5 (~pp. 136–170)
- Pricing strategies: Ch. 9 (~pp. 270–310)
- Distribution channels: Ch. 10–11 (~pp. 330–380)
- Promotions mix: Ch. 12–13 (~pp. 400–440)

---

## Output Format for audit_log.md (Stage 2 section)

```markdown
## Stage 2: Citation Completeness

| # | Citation Key | Status | Missing Fields | Action |
|---|-------------|--------|----------------|--------|
| 1 | Constantinides (2006) | INCOMPLETE | Volume, Issue, Pages, DOI | AUTO-COMPLETED from pre-filled data |
| 2 | Davcik et al. (2015) | INCOMPLETE | Volume, Issue, Pages, DOI | AUTO-COMPLETED from pre-filled data |
| 3 | Gahler et al. (2023) | DOI_MISMATCH | DOI in 00_context.md incorrect | CORRECTED to 10.1177/10946705221119617 |
| 4 | Armstrong et al. (2021) p.? | NO_PAGE_NUM | 12 instances lack page numbers | FLAGGED — manual verification required |

### Completed References (APA 7 full format)
[list all auto-completed references here]
```
