# APA 7 Reference Format Rules

Quick reference for the citation checker agent.

---

## Journal Article (most common)

```
Author, A. A., & Author, B. B. (Year). Title of article in sentence case.
  Journal Name in Title Case, Volume(Issue), first–last page.
  https://doi.org/xxxxx
```

**Rules**:
- Up to 20 authors: list all. For 21+: first 19, `...`, last author.
- Year in parentheses immediately after authors, followed by period.
- Article title: sentence case (capitalize only: first word, proper nouns,
  first word after colon/dash).
- Journal name and volume: italicized.
- Issue number: not italicized, in parentheses directly after volume.
- Pages: en dash between first and last (e.g., 191–211, not 191-211).
- DOI as full hyperlink. If no DOI: use stable URL.

---

## Book (textbook)

```
Author, A. A., Author, B. B., & Author, C. C. (Year). Title of book in sentence
  case (Nth ed.). Publisher Name.
```

**Rules**:
- No URL/DOI needed if widely available in print.
- Edition in parentheses: (2nd ed.), (8th ed.) — not italicized.
- Publisher name without country unless needed for disambiguation.

---

## Web Page / Online Source

```
Author, A. A. (Year, Month Day). Title of page. Site Name.
  https://www.example.com/page
```

If no individual author: use organization name as author.
If no date: use `(n.d.)`.

---

## Common APA 7 Errors to Flag

| Error | Example | Correction |
|-------|---------|------------|
| Missing DOI | "Journal, 26(2), 191–211." | Add `https://doi.org/...` |
| Missing volume/issue | "Journal of Retailing, 191–211." | Add volume and issue |
| Missing page range | "Journal Name, 22(3–4)." | Add page range |
| Title case article title | "The Marketing Mix Revisited" | Sentence case: "The marketing mix revisited" |
| Abbreviated journal | "J. Retail." | Full journal name |
| Wrong DOI format | "DOI: 10.1177/..." | `https://doi.org/10.1177/...` |
| "et al." in reference list | "Armstrong et al. (2021)" | List all 9 authors in reference list |

---

## In-Text Citation Rules

| Situation | Format |
|-----------|--------|
| One work, 1–2 authors | (Armstrong & Kotler, 2021) |
| One work, 3+ authors | (Armstrong et al., 2021) |
| Direct quote | (Armstrong et al., 2021, p. 136) |
| Paraphrase with specific idea | (Armstrong et al., 2021, pp. 136–137) |
| General concept, no page needed | (Armstrong et al., 2021) ✓ |
| Definition of a framework | (Armstrong et al., 2021, p. XX) — page recommended |

---

## DOI Verification

To verify a DOI, run:
```
tavily.search("doi.org/[DOI_STRING]")
```
Confirm the returned title matches the cited paper title exactly.
If mismatch: the DOI is wrong — search paper-search-mcp for the correct one.
