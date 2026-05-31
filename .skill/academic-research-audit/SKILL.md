---
name: academic-research-audit
description: >
  Automatically audits, corrects, and improves academic research Markdown files
  (research notes, analysis drafts, citation lists) for a university assignment.
  Runs a multi-stage pipeline: (1) source verification via live web scraping,
  (2) academic citation completeness checks, (3) geographic/contextual relevance
  filtering, (4) internal contradiction detection, (5) auto-correction with tracked
  changes, and (6) final quality report.
  Trigger this skill whenever the user wants to audit research notes, fix citations,
  verify sources, remove irrelevant references, correct verbatim mismatches, or
  improve the academic integrity of any research or draft Markdown file.
---

# Academic Research Audit Skill

Automated multi-stage pipeline that audits and corrects research Markdown files
for academic assignments. Designed for VS Code + GitHub Copilot with the MCP
server stack defined in `mcp.json`.

---

## Overview of the Pipeline

```
Stage 1 → Source Verification    (firecrawl / playwright / tavily)
Stage 2 → Citation Completeness  (paper-search-mcp / manual cross-check)
Stage 3 → Relevance Filtering    (sequential-thinking + product context)
Stage 4 → Contradiction Detection (sequential-thinking)
Stage 5 → Auto-Correction         (filesystem write)
Stage 6 → Audit Report            (filesystem write)
```

Each stage reads the target `.md` files from `draft/` and writes corrected
versions plus a structured audit log to `audit/`.

---

## Required Tools (from mcp.json)

| MCP Server              | Used For                                              |
|-------------------------|-------------------------------------------------------|
| `firecrawl`             | Scraping product pages, retailer listings             |
| `playwright-mcp`        | JS-rendered pages (Shopee, Lazada)                    |
| `tavily-mcp`            | Supplementary web search for source verification      |
| `paper-search-mcp`      | Verifying & completing academic paper metadata        |
| `consensus`             | Evidence-based academic claim validation              |
| `sequential-thinking`   | Structured multi-step reasoning for contradiction detection |
| `filesystem`            | Reading input files, writing corrected output files   |
| `scrapeless`            | Fallback scraper for bot-protected pages              |

---

## File Layout (expected workspace structure)

```
project-root/
├── draft/
│   ├── 00_context.md          ← product & assignment context
│   ├── 01_research_raw.md     ← primary research file (INPUT)
│   └── 02_analysis_notes.md   ← academic notes file (INPUT)
├── audit/
│   ├── 01_research_corrected.md   ← corrected version (OUTPUT)
│   ├── 02_analysis_corrected.md   ← corrected version (OUTPUT)
│   ├── audit_log.md               ← full audit trail (OUTPUT)
│   └── corrections_summary.md     ← short summary table (OUTPUT)
└── .skill/
    └── academic-research-audit/   ← this skill
```

---

## Stage 1 — Source Verification

**Goal**: For every URL cited in the research files, confirm the page is
accessible and the verbatim claims match the actual page content.

**Steps**:

1. Use `filesystem` to read `draft/01_research_raw.md` and extract all URLs.
2. For each URL:
   - Attempt scrape with `firecrawl`. If firecrawl returns empty/blocked, fall
     back to `playwright-mcp`, then `scrapeless`.
   - Record: `ACCESSIBLE`, `BLOCKED`, or `INACCESSIBLE` with reason.
3. For each `ACCESSIBLE` URL with a verbatim claim in the research file:
   - Compare the claimed verbatim text against the scraped page content.
   - Flag `MISMATCH` if the text does not appear verbatim on the page.
   - Flag `UNVERIFIABLE` if the page was blocked/inaccessible.
4. Special handling for blocked e-commerce pages (Shopee, Lazada):
   - Mark all data extracted from these as `[UNVERIFIABLE — login/bot wall]`.
   - Replace any hard claims with hedged language:
     `"A search snippet suggests approximately X VND (unverified; direct page inaccessible)."`
5. Write findings to `audit/audit_log.md` under heading `## Stage 1: Source Verification`.

See `agents/source-verifier.md` for detailed URL-by-URL instructions.

---

## Stage 2 — Academic Citation Completeness

**Goal**: Every academic reference must have: Authors, Year, Title, Journal Name,
Volume(Issue), Page Range, and DOI or stable URL — per APA 7.

**Steps**:

1. Use `filesystem` to read both `draft/01_research_raw.md` and
   `draft/02_analysis_notes.md`. Extract every academic citation.
2. For each citation, check completeness against APA 7 requirements.
3. For incomplete citations (missing DOI, pages, volume):
   - Query `paper-search-mcp` using title + first author + year.
   - If found: fill in missing fields and mark `[AUTO-COMPLETED]`.
   - If not found: mark `[INCOMPLETE — manual verification required]`.
4. Validate DOIs: confirm each DOI resolves to the correct paper title using
   `tavily-mcp` search: `doi:[DOI_STRING] site:doi.org`.
5. Flag generic textbook citations (e.g., `Armstrong et al., 2021`) that appear
   without page numbers in contexts where specific page references are needed.
   Suggest adding page numbers for direct definitions or verbatim paraphrases.
6. Write findings to `audit/audit_log.md` under `## Stage 2: Citation Completeness`.

See `agents/citation-checker.md` for APA 7 rules and completion logic.

---

## Stage 3 — Relevance & Context Filtering

**Goal**: Remove or flag citations that are geographically, taxonomically, or
analytically irrelevant to the specific product and assignment context.

**Steps**:

1. Read `draft/00_context.md` to extract the product context:
   - Product type (e.g., 100% Black Tea)
   - Target market geography (e.g., Đà Nẵng, Vietnam urban retail)
   - Assignment scope (e.g., FMCG consumer analysis, undergraduate)
2. Use `sequential-thinking` to evaluate each citation against:
   - **Product match**: Is the study about the same product type? A green tea
     consumer study is NOT relevant to a black tea product.
   - **Geographic match**: Is the study context compatible with the market being
     analyzed? Studies from unrelated markets need a bridging justification.
   - **Consumer type match**: Producer/farmer studies ≠ retail consumer studies.
   - **Recency**: For market size / trend data, prefer sources ≤ 5 years old.
3. Classify each citation as:
   - `RELEVANT` — keep as-is
   - `MARGINAL` — flag with suggested caveat wording
   - `IRRELEVANT` — remove and suggest a replacement query
4. For `IRRELEVANT` citations, run a replacement search via `paper-search-mcp`
   and `consensus` to suggest a better-fitting source.
5. Write findings to `audit/audit_log.md` under `## Stage 3: Relevance Filtering`.

---

## Stage 4 — Contradiction & Inconsistency Detection

**Goal**: Identify all internal inconsistencies between different parts of the
research files (e.g., conflicting product specs, mixed-language verbatim claims,
conflating different product SKUs).

**Steps**:

1. Use `sequential-thinking` to systematically compare:
   - All product name/format references across the file (look for SKU confusion)
   - All price references (are different platforms being compared fairly?)
   - All verbatim quotes (do they maintain consistent language? no code-switching
     inside a claimed verbatim quote)
   - All benefit claims (are they derived from actual product evidence or inferred?)
   - All "dual-use" or positioning claims (are different product variants conflated?)
2. For each contradiction found:
   - Identify the two (or more) conflicting passages with exact line references.
   - Explain which version is correct based on primary source evidence.
   - Write the corrected version.
3. Write findings to `audit/audit_log.md` under `## Stage 4: Contradictions`.

---

## Stage 5 — Auto-Correction

**Goal**: Apply all identified fixes from Stages 1–4 and write corrected files.

**Steps**:

1. Read the original `draft/01_research_raw.md`.
2. Apply all corrections in order:
   - Replace inaccessible source claims with hedged wording.
   - Insert `[AUTO-COMPLETED]` citation fields where paper-search found data.
   - Mark irrelevant citations with `> ⚠️ RELEVANCE FLAG: [reason]` blockquotes.
   - Resolve contradictions by keeping the primary-source-backed version.
   - Add `> 📝 NOTE: [explanation]` blockquotes after any significant change.
3. Write the corrected file to `audit/01_research_corrected.md`.
4. Repeat steps 1–3 for `draft/02_analysis_notes.md` →
   `audit/02_analysis_corrected.md`.
5. Write a unified diff-style summary to `audit/corrections_summary.md`.

Correction formatting conventions:
- `~~old text~~` → `corrected text` for inline replacements
- `> ⚠️ REMOVED: [reason]` for deleted citations
- `> ✅ COMPLETED: [what was added]` for auto-filled citation fields
- `> 🔄 RESOLVED: [which version kept and why]` for contradictions

---

## Stage 6 — Final Report

**Goal**: Produce a human-readable audit report for the student.

**Steps**:

1. Compile findings from all stages into `audit/audit_log.md`.
2. Write `audit/corrections_summary.md` as a concise table:

```markdown
| # | File | Location | Issue Type | Severity | Action Taken |
|---|------|----------|------------|----------|--------------|
| 1 | 01_research_raw.md | Task 1, Item 14 | Inaccessible source | HIGH | Replaced with hedged wording |
...
```

3. Severity levels: `HIGH` (factual error / missing primary source),
   `MEDIUM` (incomplete citation / marginal relevance),
   `LOW` (wording improvement / caveat suggestion).

4. End the report with:
   - Total issues found
   - Total issues auto-corrected
   - Issues requiring manual follow-up
   - Recommended next steps

---

## Error Handling

- If `firecrawl` and `playwright-mcp` both fail for a URL: mark `INACCESSIBLE`,
  note the specific error, and do NOT fabricate what the page might contain.
- If `paper-search-mcp` cannot find a paper: mark `[NOT FOUND IN DATABASE]`
  and suggest a manual Google Scholar search query.
- If `sequential-thinking` finds ambiguous contradictions: present both
  interpretations and ask the user to decide (do not auto-correct ambiguous cases).
- Never delete a citation entirely from corrected files without leaving a
  `> ⚠️ REMOVED` trace explaining why.

---

## Reference files

- `agents/source-verifier.md` — detailed URL scraping and verbatim-checking logic
- `agents/citation-checker.md` — APA 7 rules, paper-search query patterns
- `references/apa7-rules.md` — complete APA 7 reference format specifications
