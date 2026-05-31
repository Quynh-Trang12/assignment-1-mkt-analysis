# MKT10009 Assignment 1 — Complete VS Code Research & Writing Guide (v2.1)
## Applied Consumer Analysis: Cozy Trà Túi Lọc Nhãn Vàng at Lotte Mart Đà Nẵng
### Achieving "Exceeds Expectations" Across All 5 Rubric Criteria

---

## HOW TO READ THIS GUIDE

This guide is divided into **5 Phases**. Each phase has numbered steps. Every step that requires you to talk to GitHub Copilot contains a **ready-to-paste prompt** — copy it exactly as written and paste it into the Copilot Chat panel in VS Code.

**Do not skip phases.** Each phase builds on the previous one. Phases 1–2 take about 20 minutes. Phase 3 (research) takes 40–60 minutes. Phase 4 (writing) takes 30 minutes. Phase 5 (store visit + final update) takes 15 minutes on-site.

**All output will be written in English**, as required for your Swinburne assignment.

---

## YOUR VS CODE TOOLKIT — WHAT EACH TOOL DOES

Before you start, understand what tools are already configured in your `settings.json` and how they contribute to this assignment:

| Tool                                  | What It Is                                        | How It Helps This Assignment                                                                   |
| ------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **GitHub Copilot Chat (GPT-4.1)**     | Your AI assistant inside VS Code                  | Drafts, analyses, cites, and edits your assignment text                                        |
| **`tavily-mcp`**                      | Real-time web search engine for AI                | Finds current prices, promotions, and brand news about Cozy                                    |
| **`firecrawl/firecrawl-mcp-server`**  | Web page scraper — reads full page content        | Extracts product data directly from cozy.vn, lottemart.vn, and Shopee product pages            |
| **`playwright-mcp`**                  | Headless browser — navigates and clicks web pages | Opens and reads JavaScript-rendered pages such as Shopee listings                              |
| **`paper-search-mcp`**                | Academic paper search (Semantic Scholar / arXiv)  | Finds peer-reviewed sources on FMCG distribution, pricing strategy, and tea consumer behaviour |
| **`consensus`**                       | Evidence-based answer engine from research papers | Answers "what does the research say about..." questions with citations                         |
| **`sequential-thinking`**             | Structured step-by-step reasoning tool            | Forces Copilot to reason through complex analyses logically before writing                     |
| **`context7`**                        | Fetches up-to-date documentation                  | Useful for verifying academic framework definitions                                            |
| **Markdown Preview** (`Ctrl+Shift+V`) | Renders your `.md` files as formatted documents   | Write and preview your assignment in real time                                                 |
| **Auto Save**                         | Already enabled in your settings                  | Never lose your work                                                                           |
| **`filesystem` MCP**                  | Reads and writes files in your project folder     | Saves Copilot outputs directly into your `.md` files in the GitHub repo                        |

---

## PHASE 1 — SET UP YOUR WORKSPACE (5 minutes)

### Step 1 — Create Your Assignment Folder Structure

1. Open **VS Code**.
2. Click **File → Open Folder** and create a new folder:
   ```
   Documents/MKT10009/Assignment1/
   ```
3. Open that folder. In the **Explorer panel** (right side, since `workbench.sideBar.location` is set to `right` in your settings), right-click the empty area and select **New File** to create these four files one by one:

   ```
   00_context.md          ← permanent reference: product facts, assignment rules, rubric
   01_research_raw.md     ← ALL Copilot research outputs are saved here by filesystem MCP
   02_analysis_notes.md   ← 4Ps analysis, academic literature, and decision-making research
   03_assignment_draft.md ← your full assignment draft lives here
   ```

4. Open `00_context.md` and paste the block below exactly — you will attach this file in **every** Copilot prompt so Copilot always has the full context without you needing to re-explain the product each time:

```markdown
# ASSIGNMENT CONTEXT — MKT10009 A1

## Product
- Full Vietnamese name: Trà Đen Nhãn Vàng Cozy Túi Lọc (Cozy Yellow Label Black Tea Bags)
- Variant: Hộp 25 gói × 2g (box of 25 bags × 2g each) — 50g total net weight
- Official brand product page: https://cozy.vn/tra-nhan-vang/
- Lotte Mart product listing: https://www.lottemart.vn/vi-pto/product/tra-tui-loc-nhan-vang-cozy-hop-25-goi-x-2g-8936010531086-p12525
- Shopee listing (25 gói): https://shopee.vn/Trà-Đen-Nhãn-Vàng-Cozy-Túi-Lọc-(50gr-25-gói)-Hương-Vị-Đậm-Đà-An-Toàn-Sức-Khoẻ-i.1178040298.24972333525
- Shopee listing (100 túi rời, pha chế): https://shopee.vn/Trà-Đen-Nhãn-Vàng-Cozy-100-Túi-Lọc-Rời-i.268452626.14598692405
- Barcode: 8936010531086
- Producer/Brand: Cozy (manufactured by Hoa Phat Hung Import-Export Trading Production Company, Vietnam)
- Seller/Retailer: Lotte Mart Đà Nẵng, Floor 1, Unit 1F-09, 06 Nại Nam Street, Đà Nẵng City, Vietnam
- Price: [PLACEHOLDER — confirmed from Lotte Mart listing or in-store visit. Use lottemart.vn price as primary source]
- Competitors: Lipton, Phúc Long, Vinatea, Dilmah, Twinings

## Assignment Rules
- Unit: MKT10009 Marketing and the Consumer Experience, Swinburne University of Technology
- Assessment: Assignment 1 — Applied Consumer Analysis
- Word count: 1,500 words ±10% (NOT counting references, figures, tables, or appendix)
- Referencing: APA 7th edition
- Sections: The Market Offering | The Marketing Mix | Mapping My Decision-making | My Customer Experience
- Language: English (formal academic)

## Key References
- Armstrong, G., Denize, S., Volkov, M., Adam, S., Kotler, P., Ang, S., Love, A., Doherty, S., & van Esch, P. (2021). Principles of marketing (8th ed.). Pearson Australia.
- Gahler, M., Klein, J. F., & Paul, M. (2023). Customer experience: Conceptualization, measurement, and application in omnichannel environments. Journal of Service Research, 26(2), 191–211. https://doi.org/10.1177/10946705221119617

## Rubric — Exceeds Expectations Requirements
1. The Market Offering: Clearly identifies product/brand/seller; all three benefit types well-explained; in-store photo present
2. The Marketing Mix: Strong 4Ps analysis with clear purpose and importance cited; all four Ps accurate, insightful, and evidence-supported
3. Mapping My Decision-making: Accurate Consumer Decision Process with references; visual map has all 5 stages; discussion shows genuine insight applied to this product
4. My Customer Experience: Clear CX dimension with reference; discussion strongly links in-store observations to the chosen dimension
5. Professionalism: Well-structured; within word count; strong academic writing; accurate APA 7 referencing throughout
```

---

### Step 2 — Open and Verify Copilot Chat with MCP Tools

1. Press **`Ctrl+Shift+I`** to open the GitHub Copilot Chat panel. It will appear as a stacked panel (your `chat.viewSessions.orientation: "stacked"` setting).

2. At the top of the chat input box, click the **paperclip / attach icon** and select `00_context.md`. This attaches your context file so Copilot reads the full product and assignment details automatically.

3. Verify your MCP servers are active by typing this in the chat:

   ```
   List all currently active MCP tools available to you. For each tool, state its name and one sentence describing what it can do.
   ```

   You should see `tavily-mcp`, `firecrawl`, `playwright-mcp`, `paper-search-mcp`, `consensus`, `sequential-thinking`, `filesystem`, and others listed. **If any critical tool is missing**, open the Command Palette (`Ctrl+Shift+P`), type `MCP: List Servers`, and reconnect any that show as disconnected.

4. Verify that Copilot is using **GPT-4.1** — check the model selector dropdown at the top of the chat panel. If it shows a different model, switch it to `GPT-4.1`.

---

## PHASE 2 — PRODUCT & BRAND RESEARCH (Prompts 1 & 2)

### Step 3 — Run Prompt 1 (Brand, Product & Market Research)

Attach `00_context.md` to the chat (click the paperclip → select the file). Then paste **Prompt 1** exactly as written below:

---

### ▶ PROMPT 1 — Cozy Brand, Yellow Label Tea Product Details & Vietnamese Tea Market

```
## ROLE
You are a senior marketing research analyst assisting a first-year university student to complete an Applied Consumer Analysis for MKT10009 at Swinburne University of Technology, Australia. The chosen product is Cozy Trà Đen Nhãn Vàng Túi Lọc (Cozy Yellow Label Black Tea Bags), sold in a box of 25 bags × 2g each (50g net), barcode 8936010531086.

## MANDATORY PRIMARY SOURCES — use firecrawl to scrape the FULL page content of each URL below before doing anything else. Do NOT summarise from memory; extract the actual text on the page.
Source 1 — Official Cozy brand product page: https://cozy.vn/tra-nhan-vang/
Source 2 — Lotte Mart product listing: https://www.lottemart.vn/vi-pto/product/tra-tui-loc-nhan-vang-cozy-hop-25-goi-x-2g-8936010531086-p12525
Source 3 — Shopee listing (25 bags): https://shopee.vn/Trà-Đen-Nhãn-Vàng-Cozy-Túi-Lọc-(50gr-25-gói)-Hương-Vị-Đậm-Đà-An-Toàn-Sức-Khoẻ-i.1178040298.24972333525
Source 4 — Cozy brand homepage: https://cozy.vn

## SUPPLEMENTARY WEB SEARCHES — use tavily-mcp for each search below. Run all 6 searches.
Search 1: "Cozy tea brand Vietnam history founded manufacturer Hoa Phat Hung"
Search 2: "Cozy trà nhãn vàng thành phần nguyên liệu" (Cozy Yellow Label tea ingredients)
Search 3: "Cozy tea brand positioning target market Vietnam consumer"
Search 4: "Cozy trà nhãn vàng packaging design features"
Search 5: "Vietnam packaged black tea market FMCG brands 2023 2024 market share"
Search 6: "Cozy tea brand awards certifications quality Vietnam"

## TASKS — Complete ALL tasks in the order listed. Do NOT skip any task.

### TASK 1 — Product Page Scrape & Extraction
From the scraped content of Sources 1, 2, and 3, extract and report the following verbatim (copy the exact text from the page, do not paraphrase or invent):
- Full official product name as displayed on each source
- Complete product description text (all sentences, not summarised)
- Ingredients or tea composition listed (tea type, origin region, additives if any)
- Net weight, number of bags per box, weight per bag
- Any quality claims, certifications, or health claims stated on the product page
- Any usage instructions or serving suggestions
- Price as listed on Lotte Mart's website (exact figure in VND)
- Any customer ratings or review scores visible on Shopee

### TASK 2 — Brand History & Company Overview
From your web research (Sources 1, 4, and Search 1), report the following:
- Full legal company/manufacturer name behind the Cozy brand
- Year of founding and location (city/province in Vietnam)
- Original business focus and how the brand grew to its current scope
- Current product range under the Cozy brand (not just tea — list all categories if found)
- Brand positioning: where does Cozy sit in the Vietnamese tea market — premium, mid-range, or budget/mass-market? Justify with evidence.
- Primary target market: who typically buys Cozy tea bags? Describe demographics (age, income level, occupation, location) and psychographics (lifestyle, values, motivations) based on available evidence

### TASK 3 — Product Benefits Analysis
Based on the product page content and brand research, systematically identify:
- FUNCTIONAL benefits: practical, tangible benefits a consumer gets from using this specific tea (e.g., caffeine content, health properties of black tea, convenience of tea-bag format, consistent brew strength, suitable for both hot and iced tea preparation, suitability for mixed drinks like lemon tea or milk tea)
- SOCIAL benefits: how using or buying this product might affect how others perceive the consumer (e.g., affordable Vietnamese brand with widespread recognition, gifting potential, accessibility as a shared household product)
- PSYCHOLOGICAL benefits: emotional, identity, or experiential benefits (e.g., daily ritual comfort, familiarity of a trusted local brand, sense of simplicity and reliability, cultural connection to Vietnamese tea-drinking habits)
Note: Derive all benefits directly from the product details and brand information found — do not invent benefits not supported by evidence.

### TASK 4 — Vietnamese Tea Market Context
Report the following for market context:
- List the 5 main competitors to Cozy in the packaged black tea bags market in Vietnam: Lipton, Phúc Long, Vinatea, Dilmah, Twinings. For each, write one sentence describing their brand origin, positioning, and approximate price tier.
- What specifically differentiates Cozy from each of these competitors in terms of: brand story and origin, manufacturing location (local vs imported), price point, and product variety?
- Is the Cozy Nhãn Vàng product also marketed for commercial/pha chế (mixed drink) use (as suggested by the 100-bag loose variant)? If so, how does this dual-use positioning affect its market differentiation?

## OUTPUT FORMAT RULES
- Write the entire response in **English**
- Use the exact section headings: TASK 1, TASK 2, TASK 3, TASK 4
- Under each task, present information as numbered bullet points
- For every factual claim, append the source in brackets: [Source: URL or search query used]
- If a specific piece of information is not found after scraping and searching, write: [NOT FOUND — scraped/searched: state what was attempted]
- Do NOT fabricate or hallucinate any product facts, prices, certifications, or dates
- Do NOT summarise from memory — all information must come from the scraped pages or search results
- Response length: as long as needed to complete all 4 tasks fully and accurately

## SAVE OUTPUT
Use the filesystem MCP tool to append the complete response to the file `01_research_raw.md` in the current workspace folder, under the heading `## PROMPT 1 OUTPUT — Brand & Product Research`.
```

---

> ⏳ Wait for Copilot to finish all 4 tasks before sending another message. This prompt scrapes 4 URLs and runs 6 searches — expect 2–4 minutes.

---

### Step 4 — Run Prompt 2 (Pricing, Competitor Prices & Shelf Placement Research)

Keep `00_context.md` attached. Paste **Prompt 2**:

---

### ▶ PROMPT 2 — Price Research, Competitor Price Comparison & In-Store Shelf Placement

```
## ROLE
You are a marketing research analyst continuing the MKT10009 A1 assignment research on Cozy Trà Đen Nhãn Vàng Túi Lọc (25 bags × 2g). This prompt focuses on PRICING and PLACEMENT research only.

## MANDATORY PRIMARY SOURCES — use firecrawl to scrape these pages first
Source 1 — Lotte Mart product listing (primary price source): https://www.lottemart.vn/vi-pto/product/tra-tui-loc-nhan-vang-cozy-hop-25-goi-x-2g-8936010531086-p12525
Source 2 — Shopee 25-bag listing: https://shopee.vn/Trà-Đen-Nhãn-Vàng-Cozy-Túi-Lọc-(50gr-25-gói)-Hương-Vị-Đậm-Đà-An-Toàn-Sức-Khoẻ-i.1178040298.24972333525

## MANDATORY WEB SEARCHES — use tavily-mcp for ALL searches listed below. Do NOT skip any.
Search 1: "Cozy trà nhãn vàng 25 gói giá" (Cozy Yellow Label 25 bags price)
Search 2: site:tiki.vn "Cozy trà nhãn vàng túi lọc 25 gói"
Search 3: site:lazada.vn "Cozy trà nhãn vàng"
Search 4: "Lipton Yellow Label trà túi lọc 25 gói giá Việt Nam siêu thị"
Search 5: "Phúc Long trà hồng túi lọc 25 gói giá"
Search 6: "Vinatea trà túi lọc 25 gói giá siêu thị Việt Nam"
Search 7: "Dilmah PEKOE tea bags price Vietnam supermarket"
Search 8: "Twinings English Breakfast tea bags price Vietnam supermarket"
Search 9: "FMCG tea bags shelf placement Vietnam supermarket category management planogram"
Search 10: "Cozy trà bán ở đâu siêu thị đại lý phân phối" (Cozy tea distribution retailers Vietnam)

## TASKS — Complete ALL tasks in order. Do NOT skip any.

### TASK 1 — Cozy Yellow Label Tea Bags Price Data
From your scraped sources and web searches, compile all prices found for the Cozy Trà Nhãn Vàng 25-bag box:
- Present as a markdown table: Platform | Price (VND) | Notes (e.g., sale price, regular price) | URL
- Extract the exact price shown on the Lotte Mart listing (Source 1) — this is the primary retailer price for the assignment
- If the Lotte Mart price is not listed on the website, write: "Lotte Mart online price not available — in-store verification required at Lotte Mart Đà Nẵng, 06 Nại Nam Street"
- Calculate the average price across all platforms where a confirmed price was found
- State the recommended placeholder price to use in the assignment, with reasoning

### TASK 2 — Competitor Price Comparison Table
For each of the 5 competitors (Lipton, Phúc Long, Vinatea, Dilmah, Twinings), find the current retail price of their standard 25-bag black tea box sold in Vietnam.
Present as a markdown table: Brand | Product Name | Price (VND) | Platform/Retailer | URL
After the table:
- Rank all 6 products (Cozy + 5 competitors) from cheapest to most expensive
- Identify Cozy's price tier: budget/economy, mid-range, or premium

### TASK 3 — Pricing Strategy Analysis
Using the price comparison data from Tasks 1 and 2, and applying the frameworks from Armstrong et al. (2021) Principles of Marketing:
1. State clearly where Cozy Nhãn Vàng sits relative to all 5 competitors in price ranking
2. Identify the most fitting pricing strategy from the three options in Armstrong et al. (2021):
   - Customer value-based pricing: price is set based on how much value the consumer perceives the product to be worth
   - Cost-based pricing: price is set by calculating production and distribution costs then adding a profit margin
   - Competition-based pricing: price is set by benchmarking against what competitors charge for similar products
3. Justify your selection with at least 2 specific data points from the price comparison table
4. Write 3 formal academic sentences, suitable for direct use in a university assignment, explaining the identified pricing strategy with evidence. Include a citation to Armstrong et al. (2021).

### TASK 4 — Distribution Channel Analysis (Direct vs Indirect)
1. Does Cozy sell the Nhãn Vàng tea bags DIRECTLY to consumers? Check:
   - Does cozy.vn allow direct online purchasing with checkout/cart functionality?
   - Are there any Cozy-branded physical retail stores in Vietnam?
2. Does Cozy sell INDIRECTLY through intermediaries? Based on the Lotte Mart listing and Shopee searches:
   - List all confirmed retail channels and e-commerce platforms where this product is sold (Lotte Mart, BigC/MM Mega Market, Co.opmart, Winmart, Shopee, Tiki, Lazada, etc.)
   - Classify each as: retailer (indirect), wholesaler (indirect), or e-commerce marketplace (indirect)
3. Determine the channel type: direct-only, indirect-only, or dual-channel (both direct and indirect)
4. Write 3 formal academic sentences explaining Cozy's distribution channel strategy, citing Armstrong et al. (2021) on marketing channels.

### TASK 5 — In-Store Shelf Placement at Vietnamese Supermarkets
Using web research on FMCG planogram and shelf management practices in Vietnamese hypermarkets (Search 9), and any Cozy-specific placement information found:
1. In which department and aisle section would Cozy tea bags typically be found in a large Vietnamese hypermarket like Lotte Mart? (Dry goods / beverages / health foods? Which aisle relative to store entry?)
2. Based on FMCG category management principles and Cozy's positioning as a mass-market mid-range product, predict its most likely shelf position: top shelf (premium tier), eye-level (mid-tier), or lower shelf (economy/bulk tier)? Justify with reference to general FMCG shelving practice.
3. What products are typically placed adjacent to bagged tea in Vietnamese supermarket dry goods aisles? (e.g., instant coffee, sugar, condensed milk, other tea brands)
4. How does the Cozy Nhãn Vàng packaging design (yellow label, colour scheme, typography) function as a visual differentiation tool on the shelf among competitors?
5. Write 3 formal academic sentences describing the placement strategy for this type of FMCG product, citing any credible source found.

## OUTPUT FORMAT RULES
- Write the entire response in **English**
- Use exact section headings: TASK 1, TASK 2, TASK 3, TASK 4, TASK 5
- Present all price data as markdown tables
- Append every factual claim with [Source: URL or search query]
- If data is not found after completing all searches and scrapes, write: [NOT FOUND — attempted: describe what was tried]
- Do NOT estimate or invent prices — distinguish clearly between confirmed prices and estimates
- Do NOT skip any task

## SAVE OUTPUT
Use the filesystem MCP tool to append the full output to `01_research_raw.md` under the heading `## PROMPT 2 OUTPUT — Price, Distribution & Placement Research`.
```

---

## PHASE 3 — ACADEMIC & ANALYTICAL RESEARCH (Prompts 3, 4 & 5)

### Step 5 — Run Prompt 3 (Promotion Research)

---

### ▶ PROMPT 3 — Cozy Promotions, Advertising, Digital Marketing & In-Store Promotional Activities

```
## ROLE
You are a marketing research analyst. Continue the MKT10009 A1 assignment research. This prompt focuses entirely on the PROMOTION element of the 4Ps marketing mix for Cozy Trà Đen Nhãn Vàng Túi Lọc.

## MANDATORY PRIMARY SOURCES — use firecrawl to scrape
Source 1 — Cozy brand website (check for news, campaigns, promotions, social links): https://cozy.vn
Source 2 — Cozy product page (check for any promotional callouts): https://cozy.vn/tra-nhan-vang/
Source 3 — Lotte Mart listing (check for any active promotions, bundle deals, or price-off flags): https://www.lottemart.vn/vi-pto/product/tra-tui-loc-nhan-vang-cozy-hop-25-goi-x-2g-8936010531086-p12525

## MANDATORY WEB SEARCHES — use tavily-mcp for ALL searches below. Run all 8 searches.
Search 1: "Cozy tea Vietnam advertising campaign TVC commercial quảng cáo"
Search 2: "Cozy trà nhãn vàng Facebook fanpage Instagram TikTok social media"
Search 3: "Cozy tea Vietnam Zalo Official Account digital marketing"
Search 4: "Cozy trà khuyến mãi giảm giá promotion 2024 2025"
Search 5: "Cozy tea brand sponsorship PR event Vietnam"
Search 6: "Cozy tea influencer KOL review Vietnam YouTube"
Search 7: "Cozy tea supermarket display end-cap promotional display Lotte Mart Vietnam"
Search 8: "Cozy tea loyalty program membership rewards"

## TASKS — Complete ALL tasks in order. Do NOT skip any.

### TASK 1 — Advertising
1. Has Cozy run TV commercials, YouTube ads, or outdoor/billboard advertising for the Nhãn Vàng tea or for the brand generally? Provide specific examples including campaign name (if available), year, platforms used, and a brief description of the creative content.
2. What does Cozy's paid social media advertising look like — which platforms (Facebook, Instagram, TikTok, YouTube), what type of content (product demonstrations, lifestyle imagery, recipes using the tea)?
3. If direct advertising evidence for the Nhãn Vàng product specifically is sparse, report brand-level advertising and note clearly that the brand equity built by this advertising extends to the packaged tea product line.

### TASK 2 — Sales Promotions
1. Are there any current or recent price discounts, bundle deals (e.g., "buy 2 get 1 free"), multi-buy packs, seasonal promotions, or gift-with-purchase offers for Cozy tea bags?
   - Check the Lotte Mart listing (Source 3) for any active promotional flags
   - Check Shopee for any flash sale, voucher, or bundle pricing
2. Are there any supermarket-level in-store promotions — price-off stickers, loyalty point multipliers, or end-cap displays for this product at Vietnamese supermarkets?

### TASK 3 — Personal Selling
1. Does Cozy use brand ambassadors or product demonstrators in supermarkets for the packaged tea product?
2. If no specific evidence is found for Cozy, briefly describe whether personal selling is a common practice for FMCG tea bag products in Vietnamese supermarkets generally, and whether the absence of personal selling is typical for this product category. (Use search results from FMCG context if needed.)

### TASK 4 — Public Relations
1. Has the Cozy brand received media coverage, industry awards, or government quality recognition in Vietnam?
2. Does Cozy participate in trade fairs, community events, food & beverage expos, or CSR activities that build brand reputation?
3. Are there any notable brand heritage or storytelling PR activities related to Cozy's Vietnamese origin or manufacturing quality?

### TASK 5 — Direct & Digital Marketing
1. Does Cozy have active social media accounts? For each platform found (Facebook, Instagram, TikTok, YouTube), report:
   - Whether the account is verified/official
   - Approximate follower/subscriber count if visible
   - Type of content posted (product features, recipes, lifestyle, promotions)
2. Does Cozy have a mobile app or Zalo OA for direct consumer communication?
3. Is there an email newsletter or loyalty/membership program?
4. Summarise Cozy's overall digital marketing strategy in 2–3 sentences based on what was found.

### TASK 6 — Summary Promotion Mix Paragraph
Write a single paragraph of 4–5 formal academic sentences that summarises Cozy's promotional mix for the Nhãn Vàng tea bags. This paragraph must:
- Name and briefly explain the concept of the promotions mix, citing Armstrong et al. (2021)
- Cover at least 3 of the 5 elements of the promotions mix with specific, evidence-based examples from the research
- Be written in formal third-person academic English, suitable for direct insertion into Section 2 (Promotion) of a first-year university assignment
- End with a sentence that assesses the overall promotional strategy's alignment with Cozy's positioning

## OUTPUT FORMAT RULES
- Write the entire response in **English**
- Use exact section headings: TASK 1 through TASK 6
- Append every factual claim with [Source: URL or platform]
- If a specific promotional element is not found after all searches, write [NOT FOUND] and briefly note what was searched
- Do NOT invent promotional campaigns — report only confirmed findings
- If evidence for product-specific promotion is limited, report brand-level promotion clearly noting it applies to the broader product line

## SAVE OUTPUT
Use the filesystem MCP tool to append the full output to `01_research_raw.md` under the heading `## PROMPT 3 OUTPUT — Promotions Research`.
```

---

### Step 6 — Run Prompt 4 (Academic Literature Research)

This prompt uses `paper-search-mcp` and `consensus` to find peer-reviewed academic support for the marketing mix analysis — which is what pushes the assignment from "Meets Expectations" to "Exceeds Expectations."

---

### ▶ PROMPT 4 — Academic Literature Research for 4Ps Analysis and CX Framework

```
## ROLE
You are an academic research librarian. Your task is to find peer-reviewed academic papers that support the theoretical frameworks used in this MKT10009 A1 assignment. The product is Cozy Trà Đen Nhãn Vàng (a mass-market FMCG packaged black tea product sold in Vietnamese supermarkets).

## TOOLS TO USE — mandatory for each task
- Use paper-search-mcp (Semantic Scholar) for all academic paper searches
- Use consensus for all evidence-based questions
- Use tavily-mcp as a fallback if paper-search-mcp returns no relevant results

## TASKS — Complete ALL tasks in order. Do NOT skip any.

### TASK 1 — Marketing Mix / 4Ps Framework (supports Section 2 introduction)
Using paper-search-mcp, run these searches:
Query A: "marketing mix 4Ps FMCG consumer packaged goods effectiveness"
Query B: "importance of marketing mix strategy consumer goods emerging markets"

Report:
- 2 peer-reviewed papers directly relevant to the 4Ps marketing mix framework for consumer packaged goods
- For each paper: Authors (Year). Title. Journal Name, Volume(Issue), pages. DOI. — formatted in APA 7
- A 1-sentence summary of each paper's contribution to understanding the 4Ps
- Note: Armstrong et al. (2021) is the primary textbook reference; these academic papers serve as supplementary evidence

### TASK 2 — Pricing Strategy for FMCG / Beverage Products (supports Section 2, Price)
Using paper-search-mcp, run these searches:
Query A: "competition-based pricing strategy FMCG packaged beverages"
Query B: "value-based pricing consumer goods developing markets"
Query C: "price sensitivity tea coffee FMCG Vietnam consumer behaviour"

Using consensus, ask:
"What pricing strategy do mass-market FMCG tea brands typically use in price-sensitive developing markets?"

Report:
- 2 peer-reviewed papers relevant to FMCG pricing strategy, with full APA 7 citation details
- The consensus answer with its evidence rating
- 2 formal academic sentences summarising the pricing insight that can be applied to Cozy's pricing strategy analysis

### TASK 3 — Distribution Channels & Shelf Placement for FMCG (supports Section 2, Placement)
Using paper-search-mcp, run these searches:
Query A: "indirect distribution channels FMCG retail emerging markets intermediaries"
Query B: "retail shelf placement consumer packaged goods purchase behaviour supermarket"
Query C: "planogram shelf position FMCG consumer choice visibility"

Using consensus, ask:
"How does shelf position and in-store placement affect consumer purchase decisions for FMCG products?"

Report:
- 2–3 peer-reviewed papers on FMCG distribution channels or shelf placement with full APA 7 citation details
- The consensus answer with evidence rating
- 2 formal academic sentences about FMCG distribution and shelf placement that can be inserted directly into the Placement sub-section

### TASK 4 — Consumer Decision-Making for Low-Involvement FMCG Products (supports Section 3)
Using paper-search-mcp, run these searches:
Query A: "low involvement consumer decision making FMCG repeat purchase"
Query B: "habitual buying behaviour tea beverage FMCG brand loyalty"

Report:
- 2 peer-reviewed papers on consumer decision-making for low-involvement or FMCG products
- Full APA 7 citation details for each
- A brief note (2–3 sentences) on whether tea bag purchases are typically classified as low-involvement or high-involvement, and what this means for how a consumer moves through the 5-stage Consumer Decision Process (i.e., some stages may be abbreviated or skipped for habitual purchases)

### TASK 5 — Sensorial Customer Experience in Retail Environments (supports Section 4)
Using paper-search-mcp, run these searches:
Query A: "sensory marketing retail store atmosphere consumer behaviour purchase"
Query B: "sensorial customer experience supermarket visual auditory olfactory"
Query C: "retail environment sensory stimuli consumer response"

Report:
- 2–3 peer-reviewed papers on sensory/sensorial customer experience in retail or supermarket environments
- Full APA 7 citation details for each
- For each paper, 1–2 sentences from the paper's key findings that directly support the sensorial CX analysis of a supermarket shopping experience

## OUTPUT FORMAT RULES
- Write the entire response in **English**
- Use exact section headings: TASK 1 through TASK 5
- For every paper found, provide a complete APA 7 reference: Authors (Year). Title. Journal Name, Volume(Issue), pages. DOI or URL.
- If page numbers are unavailable, note: "(page numbers unavailable — online first or no pagination)"
- If no relevant paper is found after 3 queries, write: [NO RELEVANT PAPER FOUND — queries used: list them]
- Do NOT fabricate or hallucinate citations, DOIs, journal names, or page numbers under any circumstances — if uncertain about a specific detail, note it explicitly

## SAVE OUTPUT
Use the filesystem MCP tool to append the full output to `02_analysis_notes.md` under the heading `## PROMPT 4 OUTPUT — Academic Literature & Citations`.
```

---

### Step 7 — Run Prompt 5 (Consumer Decision-Making + CX Analysis)

---

### ▶ PROMPT 5 — Consumer Decision-Making Process & Sensorial Customer Experience Analysis

```
## ROLE
You are a consumer behaviour analyst and academic writing assistant. You are helping a first-year student write Sections 3 and 4 of their MKT10009 A1 assignment. The product is Cozy Trà Đen Nhãn Vàng Túi Lọc (Cozy Yellow Label Black Tea Bags, 25 bags × 2g) purchased at Lotte Mart Đà Nẵng, Floor 1, 06 Nại Nam Street, Vietnam.

## TOOLS TO USE — mandatory
- sequential-thinking: use this tool to reason through the consumer decision process and CX analysis step by step before writing any final text
- tavily-mcp: search for contextual information as specified in the tasks below
- paper-search-mcp: retrieve any academic support needed

## CONSUMER PERSONA
Vietnamese university student or young adult, aged 18–25, living in Đà Nẵng. Health-conscious and aware of dietary choices. Familiar with Vietnamese tea culture and regular tea consumption at home. Uses Lotte Mart for weekly or occasional grocery shopping. Has seen Cozy tea bags at home or at friends' homes. Potentially interested in making homemade lemon tea (trà chanh) or milk tea using this product.

## PRIMARY ACADEMIC REFERENCES
- Armstrong, G., Denize, S., Volkov, M., Adam, S., Kotler, P., Ang, S., Love, A., Doherty, S., & van Esch, P. (2021). Principles of marketing (8th ed.). Pearson Australia.
- Gahler, M., Klein, J. F., & Paul, M. (2023). Customer experience: Conceptualization, measurement, and application in omnichannel environments. Journal of Service Research, 26(2), 191–211. https://doi.org/10.1177/10946705221119617

## TASKS — Complete ALL tasks in order. Do NOT skip any.

### TASK 1 — Consumer Decision-Making Process: Stage-by-Stage Breakdown
Use sequential-thinking to work through each stage before writing.

For each of the 5 stages of the Consumer Decision-Making Process as described in Armstrong et al. (2021), provide ALL FOUR of the following sub-parts. Label each sub-part clearly.

Stage 1: Need Recognition
Stage 2: Information Search
Stage 3: Evaluation of Alternatives
Stage 4: Purchase Decision
Stage 5: Post-Purchase Behaviour

For EACH stage, provide:
(a) ACADEMIC DEFINITION — 1–2 sentences defining what occurs at this stage, citing Armstrong et al. (2021). Use page numbers where possible; if unsure, cite as (Armstrong et al., 2021) without a page number — do NOT invent page numbers.
(b) APPLIED EXAMPLE — A specific, realistic, and detailed description of what the consumer persona (18–25 year old student in Đà Nẵng) would actually do, think, and feel at this stage when deciding to purchase Cozy Yellow Label Tea Bags at Lotte Mart. The example must reference the product and the specific retail context — do NOT write generic examples.
(c) ASSIGNMENT-READY SENTENCE — 1–2 formal academic sentences written in first person ("I") that could be used directly in the Section 3 discussion. The sentence must name the product and demonstrate clear understanding of the stage.
(d) VISUAL ICON SUGGESTION — A specific, free icon from flaticon.com or icons8.com, or a common emoji, that best visually represents what happens at this stage. State the icon name and why it fits.

Additionally, for Stage 4 (Purchase Decision) specifically:
- Identify whether this purchase would be a TRIAL purchase, REPEAT purchase, or LONG-TERM COMMITMENT purchase (as defined in Armstrong et al., 2021), and justify your answer given that Cozy is a widely available, affordable, mass-market product
- Identify 2 realistic factors that could disrupt the purchase intention before the final decision is made: (1) attitudes of others and (2) unexpected situational factors — provide specific examples relevant to this product and retail context

### TASK 2 — Miro Visual Map Instructions (Step-by-step)
Provide exact instructions to create the visual Consumer Decision-Making Map using Miro Free (miro.com/apps). The map specifications are:
- Layout: 5 boxes connected by rightward arrows, arranged horizontally in a single row
- Each box contains: one icon/emoji at the top, the stage name in bold (5–7pt), and a 3–5 word descriptive phrase below
- Colour scheme: use Cozy brand colours — yellow/gold (#F5C518 or similar) for box fills, dark navy or charcoal (#1A2035) for text, white arrows between boxes
- Style: clean, minimal, professional — suitable for a first-year university assignment

Instructions must include:
- Step 1: How to create the first box and style it
- Step 3: How to add free icons to Miro's icon library (search terms to use for each stage)
- Step 4: What arrows to add between boxes
- Step 5: What stage names and short text to each box should be added
- Step 6: What caption should be used for "Figure 2" to insert to a Word document

### TASK 3 — Sensorial CX Analysis for Lotte Mart Đà Nẵng

#### 3a. Academic Definition
Write a precise 2-sentence academic definition of the Sensorial CX dimension as defined in Gahler et al. (2023, p. 194). The definition must:
- Cite Gahler et al. (2023) with the page number 194
- Name all five external senses: visual, auditory, tactile, olfactory, and gustative
- Use formal academic language

#### 3b. Contextual Research on Lotte Mart Đà Nẵng
Use tavily-mcp to run these searches:
Search A: "Lotte Mart Đà Nẵng Nại Nam store layout shopping experience review"
Search B: "Lotte Mart Vietnam hypermarket store atmosphere environment"
Search C: "Vietnamese supermarket sensory shopping environment music displays"

From the search results, report:
- Any specific information about Lotte Mart Đà Nẵng's store environment (layout, lighting, music, décor, sections)
- General characteristics of the shopping atmosphere in large Korean-owned hypermarkets in Vietnam (Lotte Mart format)
- What the dry goods / beverages aisle typically looks and feels like in this type of store

#### 3c. Draft Section 4 Text (~300 words)
Write a first-person academic account of the sensorial CX experience at Lotte Mart Đà Nẵng while browsing for and selecting Cozy Yellow Label Tea Bags. This draft must satisfy ALL of the following requirements:
- Open with the academic definition of the Sensorial dimension, citing Gahler et al. (2023, p. 194)
- Describe the VISUAL sense: what the student sees — store lighting, aisle layout, signage, the tea products on the shelf, and specifically how the Cozy Nhãn Vàng yellow packaging stands out visually among competitors
- Describe the AUDITORY sense: what the student hears — background music (Korean/pop typically in Lotte Mart stores), PA announcements in Vietnamese, ambient sounds from other shoppers or nearby departments
- Describe the OLFACTORY sense: what the student smells — any nearby food counters (bakery, fresh produce, cooked food section near entry), subtle scents in the dry goods aisle
- Describe the TACTILE sense: what the student feels when handling the product — the texture and weight of the cardboard box, the individual bag packaging inside
- Include at least 2 sensory details that are specific to the Cozy product itself (e.g., visual: the bold yellow label and Vietnamese-language text on the box; tactile: the individual foil-free or envelope tea bags inside)
- Write in first person throughout ("I noticed...", "As I walked...", "Picking up the box...")
- Include one Gahler et al. (2023) in-text citation in the body of the text
- End with a sentence reflecting on how the cumulative sensorial experience of the store and the product influenced the likelihood of selecting the product
- Add this note at the very end in italics: *[Personalisation note: Replace the above descriptions with your specific in-store observations when you visit Lotte Mart. Confirm the actual shelf appearance, sounds, and scents you personally experienced.]*
- Target length: 280–320 words

## OUTPUT FORMAT RULES
- Write the entire response in **English**
- Use exact section headings: TASK 1, TASK 2, TASK 3
- Under TASK 1, label each stage as "Stage 1: Need Recognition", "Stage 2: Information Search", etc., with sub-parts (a), (b), (c), (d) clearly labelled
- All academic sentences must include proper APA 7 in-text citations
- Do NOT write vague or generic examples — every applied example (sub-part b) must specifically reference Cozy Yellow Label Tea Bags and the Lotte Mart Đà Nẵng shopping context
- The Section 4 draft (Task 3c) must be 280–320 words — count carefully
- Do NOT hallucinate page numbers for Armstrong et al. (2021) — if unsure, omit the page number

## SAVE OUTPUT
Use the filesystem MCP tool to append the full output to `02_analysis_notes.md` under the heading `## PROMPT 5 OUTPUT — Consumer Decision Process & CX Analysis`.
```

---

## PHASE 4 — WRITING THE ASSIGNMENT (Prompts 6, 7 & 8)

### Step 8 — Compile Your Research Before Writing

Before running Prompt 6, open `01_research_raw.md` and `02_analysis_notes.md` side by side in VS Code (right-click a tab → "Open to the Side") and quickly verify:

- [ ] Cozy brand history and product details are present (from Prompt 1)
- [ ] Price data with a recommended placeholder is present (from Prompt 2)
- [ ] All 4Ps have research evidence (from Prompts 2 and 3)
- [ ] At least 3–4 academic references in APA 7 format are listed (from Prompt 4)
- [ ] Consumer Decision Process stage breakdowns are present (from Prompt 5)
- [ ] Section 4 sensorial CX draft is present (from Prompt 5)

Now attach **both `01_research_raw.md` and `02_analysis_notes.md`** to Copilot Chat using the paperclip icon before running Prompt 6. Also keep `00_context.md` attached.

---

### ▶ PROMPT 6 — Full Assignment Draft (Sections 1–4 + Reference List)

```
## ROLE
You are an expert academic writing assistant. Write the complete first draft of Assignment 1 (Applied Consumer Analysis) for MKT10009 at Swinburne University of Technology. The attached files contain all research findings — `01_research_raw.md` (brand, price, placement, promotions research) and `02_analysis_notes.md` (academic literature, consumer decision process analysis, and CX draft).

## CRITICAL CONSTRAINT
You must use ONLY information that exists in the attached research files (`01_research_raw.md` and `02_analysis_notes.md`) and the context file (`00_context.md`). Do NOT use information from your training data or general knowledge about Cozy tea, Vietnamese supermarkets, or the tea market that was not researched and recorded in these files.

## ASSIGNMENT SPECIFICATIONS
- Main body target: 1,400–1,500 words (exclude headings, reference list, figure captions, placeholder notes)
- Language: Formal academic English, third-person in Sections 1 & 2, first-person in Sections 3 & 4
- Referencing: APA 7th edition, in-text citations throughout
- No bullet points in assignment body — write in full paragraphs only

## STRICT GUARDRAILS — follow ALL of these
1. DO NOT fabricate any facts, prices, statistics, or product details not found in the research files
2. DO NOT hallucinate citations — use only Armstrong et al. (2021) and Gahler et al. (2023) as the two primary references, plus any supplementary academic papers confirmed in `02_analysis_notes.md`
3. DO NOT use bullet points anywhere in the assignment body text
4. DO NOT write vague or filler sentences — every sentence must contribute specific analytical content
5. If the exact Lotte Mart price is confirmed in the research files, use it; if a placeholder was used, write: "The product retails at approximately [PLACEHOLDER: confirm in-store price] VND at Lotte Mart Đà Nẵng"
6. Insert figure placeholders exactly as written here — do not change the wording:
   - In Section 1: [FIGURE 1: Photograph of Cozy Trà Đen Nhãn Vàng Túi Lọc on shelf at Lotte Mart Đà Nẵng — to be inserted from in-store visit]
   - In Section 3: [FIGURE 2: Consumer Decision-Making Map — to be inserted (see Canva instructions in 02_analysis_notes.md)]
7. Include personalisation note at end of Section 4 exactly as written in the research files
8. Word count: stay within 1,350–1,650 words in the main body

## SECTION-BY-SECTION WRITING INSTRUCTIONS

### SECTION 1 — The Market Offering (target: 150–200 words)
Write in formal third-person academic voice. Structure as one flowing paragraph followed by the photo placeholder. Include:
- Full product name in Vietnamese and English (e.g., "Cozy Trà Đen Nhãn Vàng Túi Lọc, or Cozy Yellow Label Black Tea Bags...")
- The producer/brand: Cozy (manufactured in Vietnam)
- The seller/retailer: Lotte Mart Đà Nẵng, with full address (Floor 1, Unit 1F-09, 06 Nại Nam Street, Đà Nẵng)
- Insert Figure 1 placeholder
- A substantive paragraph (not a list) explaining all three benefit types for this specific product:
  * Functional: be specific to black tea and the tea-bag format — reference the product's suitability for pha chế (mixing) if supported by the research
  * Social: be specific to Cozy's mass-market recognition in Vietnam and its role in household and social settings
  * Psychological: be specific to the comfort, ritual, and familiarity associated with this widely trusted Vietnamese brand

### SECTION 2 — The Marketing Mix (target: 650–750 words)
Open with a 3–4 sentence introductory paragraph defining the marketing mix, stating its purpose and strategic importance for marketers, and naming all four elements — cite Armstrong et al. (2021).

Then write four sub-sections, each with a bold heading:

**Product**
Apply the Three Levels of Products framework (Armstrong et al., 2021). For each level, write substantive analytical sentences — not a list:
- Core customer value: What is the consumer really purchasing beyond the physical tea bag? Analyse the deeper need — convenience, hydration, the ritual of daily tea, the ability to make homemade lemon tea or milk tea affordably
- Actual product: Describe specific, confirmed physical and packaging attributes of Cozy Nhãn Vàng from the research: the yellow label design, box format, 25 individual bags, 2g per bag, Vietnamese text, brand name, net weight 50g, and any quality signals identified
- Augmented product: What does Cozy provide beyond the physical product? Based on research findings: available through multiple retail channels including the brand website, supermarkets, and e-commerce platforms; any loyalty or service elements found

**Price**
- State the confirmed or placeholder price in VND
- Present a mini comparison table (inline as a sentence or in a 3-column table) comparing Cozy's price to at least 2 competitors from the research
- Identify and name the pricing strategy from Armstrong et al. (2021), justify it with 2 specific data points from the price comparison, and cite Armstrong et al. (2021)

**Placement**
- State and justify the distribution channel classification (direct, indirect, or dual-channel) using specific evidence from the research (name the actual retail and e-commerce channels found)
- Describe the in-store shelf placement: aisle/department location, likely shelf position, visual adjacencies, and how physical placement functions as a marketing tool to drive visibility
- Cite Armstrong et al. (2021) on marketing channels and/or any academic source from the research files on shelf placement

**Promotion**
- Define the promotions mix, citing Armstrong et al. (2021)
- Analyse at least 3 of the 5 promotional mix elements (advertising, sales promotion, personal selling, public relations, direct and digital marketing), with specific real examples from the research for each element discussed
- Close with a sentence evaluating how the overall promotional strategy aligns with Cozy's positioning as a mass-market, value-oriented Vietnamese tea brand

### SECTION 3 — Mapping My Decision-Making (target: 250–300 words)
Write in first person.

Opening paragraph: Define the Consumer Decision-Making Process in 2–3 sentences, citing Armstrong et al. (2021). State it consists of 5 stages and note that for a low-cost FMCG product like tea bags, some stages may be brief or habitual.

Insert Figure 2 placeholder.

Discussion (flowing paragraphs, NOT a numbered list): Walk through all 5 stages as they apply to you personally purchasing Cozy Yellow Label Tea Bags at Lotte Mart. Use the applied examples and assignment-ready sentences from `02_analysis_notes.md` as your base. Include:
- The type of purchase (trial/repeat/long-term commitment) with citation
- The 2 disrupting factors (attitudes of others, unexpected situational factors) with specific examples for this product

### SECTION 4 — My Customer Experience (target: 280–320 words)
Write in first person. Use the Section 4 draft from `02_analysis_notes.md` as the base text. Ensure:
- The Gahler et al. (2023, p. 194) definition of the Sensorial dimension appears in the opening sentence(s) with correct citation
- At least 4 senses (visual, auditory, olfactory, tactile) are described with specific, concrete details
- At least 2 sensory observations are directly tied to the Cozy Nhãn Vàng product itself (packaging appearance, physical handling)
- The personalisation note appears at the very end in italics exactly as written in the research files
- Do NOT change the Gahler et al. (2023) citation

### REFERENCE LIST
Format all references in APA 7 at the end of the document. Must include:
1. Armstrong et al. (2021) — full reference
2. Gahler et al. (2023) — full reference with DOI
3. Cozy brand website (APA 7 web source format)
4. Lotte Mart product listing (APA 7 web source format)
5. Any confirmed supplementary academic papers cited in the body

## OUTPUT FORMAT
- Present the complete assignment as clean markdown
- Use `##` for the four main section headings
- Use `**bold**` for the four 4Ps sub-headings within Section 2
- No bullet points in body text
- Include at the end: **Approximate main body word count: [number] words**

## SAVE OUTPUT
Use the filesystem MCP tool to save the complete output as `03_assignment_draft.md` in the workspace folder, overwriting any existing content.
```

---

### Step 9 — Run Prompt 7 (Rubric Audit & Gap Analysis)

After Prompt 6 saves `03_assignment_draft.md`, attach that file along with `02_analysis_notes.md` to the chat and run Prompt 7:

---

### ▶ PROMPT 7 — Rubric Audit: Criterion-by-Criterion Gap Analysis

```
## ROLE
You are a university marking assistant. Audit the attached draft (`03_assignment_draft.md`) against the MKT10009 Assignment 1 rubric for "Exceeds Expectations" and produce a precise, actionable gap analysis.

## TOOLS TO USE
- filesystem MCP: read `03_assignment_draft.md` and `02_analysis_notes.md`
- sequential-thinking: use this to evaluate each criterion methodically before reporting

## RUBRIC — "EXCEEDS EXPECTATIONS" DEFINITION FOR EACH CRITERION

**Criterion 1 — The Market Offering**
Exceeds Expectations requires: Product, producer/brand, and seller are clearly and completely identified. All three benefit types (functional, social, psychological) are relevant to THIS product and well-explained — not merely listed. In-store photo placeholder is present.

**Criterion 2 — The Marketing Mix**
Exceeds Expectations requires: The marketing mix is explained with its purpose and importance using an appropriate reference. Analysis of all four Ps is accurate, insightful, and supported by specific evidence. All four Ps must be present with substantive (not superficial) analysis. The three-levels-of-products framework must be correctly applied. Pricing strategy must be identified AND justified with evidence. Distribution channel must be classified AND justified. At least 3 promotion elements must be discussed with specific examples.

**Criterion 3 — Mapping My Decision-Making**
Exceeds Expectations requires: Consumer Decision Process is accurately defined with appropriate references. A visual map placeholder (Figure 2) is present. The accompanying discussion covers ALL 5 stages with strong, specific application to the chosen product — not generic examples. Purchase type and disrupting factors are addressed.

**Criterion 4 — My Customer Experience**
Exceeds Expectations requires: The chosen CX dimension (Sensorial) is clearly and accurately explained with a citation to Gahler et al. (2023). The in-store experience discussion is well-developed and specifically links sensory observations to the in-store and product context — not vague or generic.

**Criterion 5 — Professionalism**
Exceeds Expectations requires: Well-structured with clear headings. Main body word count within 1,350–1,650 words. Academic writing is strong, consistent, and formal throughout. Referencing follows APA 7 accurately throughout both in-text and in the reference list.

## TASKS — Complete ALL tasks. Do NOT skip any.

### TASK 1 — Criterion-by-Criterion Audit Table
For each of the 5 criteria, assess the draft and produce the following table:

| Criterion | Current Assessment | Specific Gap(s) | Required Action |
| --------- | ------------------ | --------------- | --------------- |

Assess each criterion as one of:
- ✅ Exceeds Expectations — fully satisfied, no gaps
- ⚠️ Meets Expectations — present but lacks depth/specificity/evidence
- ❌ Does Not Meet Expectations — missing or fundamentally inadequate

For every gap identified, state SPECIFICALLY what is missing or inadequate — do not write generic improvement suggestions.

### TASK 2 — APA 7 Citation Audit
Review every in-text citation and every entry in the reference list. For each issue found, report:
- The exact sentence or reference entry with the error
- The specific APA 7 rule violated
- The corrected version

Also identify: Are there any factual claims in the draft that are not cited but should be?

### TASK 3 — Word Count Audit
Count the words in the main body text ONLY. Exclude: all headings, figure placeholder lines, the reference list heading and entries, and the personalisation note in Section 4.
Report the exact count. Is it within 1,350–1,650 words? If not, state by how many words it is over or under.

### TASK 4 — Academic Writing Quality Audit
Identify up to 5 sentences in the draft that exhibit any of the following weaknesses:
- Too informal in tone for academic writing
- Too vague or generic (could apply to any product, not specifically to Cozy tea at Lotte Mart)
- Padding or repetition that does not add analytical value
- Wording that sounds AI-generated rather than student-authored

For each flagged sentence: quote it exactly, identify the weakness type, and provide a rewritten version that is more specific, analytical, and naturally student-authored.

### TASK 5 — Completeness Checklist
Verify the presence and adequacy of each item:
- [ ] Full product name in Vietnamese and English in Section 1
- [ ] Brand (Cozy) and retailer (Lotte Mart Đà Nẵng with address) identified
- [ ] All 3 benefit types discussed substantively in Section 1
- [ ] Figure 1 placeholder present
- [ ] Marketing mix introductory paragraph with Armstrong et al. (2021) citation
- [ ] All 4 Ps present with bold sub-headings
- [ ] Three levels of products applied (core/actual/augmented) with specific product details
- [ ] Pricing strategy named and justified with competitor price evidence
- [ ] Distribution channel classified (direct/indirect/dual) and justified
- [ ] In-store shelf placement described
- [ ] At least 3 promotion elements analysed with specific examples
- [ ] Section 3 opens with CDP definition and Armstrong et al. (2021) citation
- [ ] All 5 stages addressed in the Section 3 discussion
- [ ] Purchase type (trial/repeat/long-term) stated with citation
- [ ] 2 disrupting factors mentioned
- [ ] Figure 2 placeholder present
- [ ] Section 4 opens with Gahler et al. (2023, p. 194) citation
- [ ] At least 4 senses described in Section 4
- [ ] At least 2 sensory details tied specifically to Cozy product
- [ ] Personalisation note at end of Section 4 in italics
- [ ] Reference list includes Armstrong et al. (2021), Gahler et al. (2023), Cozy website, Lotte Mart listing

## OUTPUT FORMAT RULES
- Write in **English**
- Use exact headings: TASK 1 through TASK 5
- Use the table format specified in TASK 1
- Be precise and direct — do not include encouragement or motivational language
- For TASK 4, quote each flagged sentence exactly as it appears in the draft

## SAVE OUTPUT
Use the filesystem MCP tool to append this complete audit to `02_analysis_notes.md` under the heading `## PROMPT 7 OUTPUT — Rubric Audit`.
```

---

### Step 10 — Run Prompt 8 (Targeted Revisions)

After reviewing the Prompt 7 audit, run Prompt 8 to fix every identified gap:

---

### ▶ PROMPT 8 — Targeted Revision: Apply All Audit Fixes to the Draft

```
## ROLE
You are an academic editor. Apply all improvements identified in the rubric audit to produce a revised, polished assignment draft.

## TOOLS TO USE
- filesystem MCP: read `03_assignment_draft.md` (current draft) and `02_analysis_notes.md` (contains the Prompt 7 audit under "PROMPT 7 OUTPUT — Rubric Audit")
- sequential-thinking: work through each fix in the audit systematically before making any edits — do not jump between sections randomly

## REVISION PROCESS — follow this exact sequence
Step 1: Read the full current draft from `03_assignment_draft.md`
Step 2: Read the complete audit from `02_analysis_notes.md` → "PROMPT 7 OUTPUT — Rubric Audit"
Step 3: Use sequential-thinking to create an ordered list of all fixes to apply, from highest priority (Exceeds Expectations gaps) to lowest (style improvements)
Step 4: Apply all fixes in order
Step 5: Recount the main body word count and adjust if needed

## REVISION RULES — follow ALL strictly
1. Apply EVERY fix identified under TASK 1 (criterion gaps rated ⚠️ or ❌)
2. Apply EVERY APA 7 correction identified under TASK 2
3. If word count is under 1,350: add substantive analytical content (not filler) to the sections flagged as weak in TASK 1. Do not add new information that was not in the original research files.
4. If word count is over 1,650: remove the sentences flagged as generic, vague, or padding in TASK 4 — these are the safest sentences to cut.
5. Replace every sentence flagged in TASK 4 with the improved version provided in the audit
6. Fix all missing items from the TASK 5 completeness checklist
7. Do NOT change the overall four-section structure or the section headings
8. Do NOT change the voice: third-person in Sections 1 & 2, first-person in Sections 3 & 4
9. Do NOT add information that was not present in `01_research_raw.md` or `02_analysis_notes.md`
10. Keep all figure placeholders ([FIGURE 1] and [FIGURE 2]) and the personalisation note at the end of Section 4 exactly as they are

## OUTPUT
Produce the complete revised assignment in full — all 4 sections plus reference list. Do NOT output only the changed sections.

Include at the end:
- **Revision Summary**: A bullet list of each change made (maximum 2 sentences per change)
- **Revised Main Body Word Count**: [number] words

## SAVE OUTPUT
Use the filesystem MCP tool to overwrite `03_assignment_draft.md` with the revised version.
```

---

## PHASE 5 — STORE VISIT, PERSONALISATION & FINAL SUBMISSION (Prompt 9)

### Step 11 — What to Observe During Your Lotte Mart Visit

When you visit Lotte Mart Đà Nẵng (Floor 1, Unit 1F-09, 06 Nại Nam Street), spend 10–15 minutes collecting the following. Take brief notes on your phone.

| What to observe                                                                  | Why it matters in the assignment                 |
| -------------------------------------------------------------------------------- | ------------------------------------------------ |
| Exact shelf price on the price tag (VND)                                         | Replaces placeholder in Section 2 Price          |
| Photograph of product on the shelf — product only, no people                     | Required for Section 1 (must be your own photo)  |
| Which floor, which aisle, aisle number if labelled                               | In-store placement analysis, Section 2 Placement |
| Shelf height: top row, eye-level, mid-shelf, or bottom row                       | Shelf placement strategy analysis                |
| Products immediately to the left and right, above and below                      | Shelf adjacencies — competitive context          |
| Any promotional stickers, price-off tags, or multi-buy labels on the product     | Sales promotion evidence for Section 2 Promotion |
| Any branded display unit, shelf divider, or shelf talker for Cozy                | Visual merchandising evidence                    |
| What you see in the aisle: lighting quality, signage, product density on shelves | Visual sense for Section 4                       |
| What you hear in the store at that time                                          | Auditory sense for Section 4                     |
| What you smell near the aisle                                                    | Olfactory sense for Section 4                    |
| What the box feels like when you pick it up                                      | Tactile sense for Section 4                      |

---

### ▶ PROMPT 9 — Post-Visit Personalisation: Insert Real Observations & Finalise

```
## ROLE
You are an academic editor performing the final personalisation pass on this university assignment. The student has visited Lotte Mart Đà Nẵng and collected the real in-store observations listed below. Your task is to integrate each observation into the correct section of the draft, replace all placeholders, and produce the final submission-ready version.

## TOOLS TO USE
- filesystem MCP: read the current draft from `03_assignment_draft.md`
- sequential-thinking: for each observation, identify which section it belongs to before making any edits

## STUDENT'S IN-STORE OBSERVATIONS
[Fill in your actual notes below before running this prompt. Replace each bracketed placeholder with your real observation.]

- Confirmed shelf price at Lotte Mart: [e.g., 32,900 VND per box of 25 bags]
- Floor and aisle: [e.g., Floor 1, dry goods/beverage aisle, aisle 5]
- Shelf row: [e.g., eye-level shelf, second row from the top]
- Product to the immediate left: [e.g., Lipton Yellow Label Tea]
- Product to the immediate right: [e.g., Cozy 100-bag bulk pack]
- Product directly above: [e.g., Twinings English Breakfast Tea]
- Product directly below: [e.g., Vinatea black tea bags]
- Any promotional label on product: [e.g., "Giảm 15% — 24/3 đến 30/3" sticker OR "No promotion active at time of visit"]
- Any branded shelf display or talker: [e.g., Cozy-branded yellow shelf divider with logo present OR none observed]
- Visual observation: [e.g., The yellow label of the Cozy box was highly visible from two metres away; the bold yellow colour contrasted sharply with the red Lipton box and the plain white Vinatea packaging beside it]
- Auditory observation: [e.g., Soft K-pop instrumental music played in the background; a Vietnamese-language PA announcement about a promotion in the fresh food section was audible every few minutes]
- Olfactory observation: [e.g., A faint smell of freshly baked bread from the in-store bakery located at the store entrance drifted into the dry goods aisle]
- Tactile observation: [e.g., The cardboard box felt light and compact; the outer surface had a slightly matte laminated finish that felt smooth and premium relative to the plain Vinatea packaging]
- Any other notable observation: [add if relevant]

## TASKS — Complete ALL tasks in order

### TASK 1 — Replace All Price Placeholders
1. Find every instance of "[PLACEHOLDER: confirm in-store price]" or any similar price placeholder in the draft
2. Replace with the actual confirmed price: "X,XXX VND"
3. Update the competitor price comparison sentence in Section 2 if the actual price changes the pricing strategy analysis

### TASK 2 — Enrich Section 2 (Placement) with Real Observations
Using the aisle, shelf row, adjacencies, and display observations:
1. Replace or supplement the generic in-store shelf placement description with the student's specific observations
2. Name the actual aisle and shelf height
3. Name the actual adjacent competitor products observed — this adds specificity to the competitive context analysis
4. If a branded display or shelf talker was observed, add one sentence about this as a visual merchandising tool
5. Keep all existing analysis, citations, and the Armstrong et al. (2021) reference intact

### TASK 3 — Enrich Section 2 (Promotion) with Real Observations
1. If a promotional label or discount sticker was observed on the product, add a specific sentence to the Sales Promotions part of the Promotion sub-section, naming the promotion and the discount percentage/type
2. If no promotion was active at time of visit, add a brief neutral sentence: "At the time of the in-store visit, no active sales promotion was observed on the product at Lotte Mart Đà Nẵng"
3. Do not change any other part of the Promotions sub-section

### TASK 4 — Personalise Section 4 (Customer Experience)
Replace the generic sensory descriptions with the student's actual in-store observations:
1. Replace the visual description with what the student actually saw (shelf appearance, Cozy packaging colour impact, competitor visual contrast)
2. Replace the auditory description with what the student actually heard (music, PA announcements, ambient sounds)
3. Replace the olfactory description with what the student actually smelled
4. Replace the tactile description with the student's actual experience of handling the Cozy box
5. Remove the italicised personalisation note at the end of Section 4 — it is no longer needed as the section is now personalised
6. Ensure the Gahler et al. (2023, p. 194) citation remains intact and correctly formatted

### TASK 5 — Final APA 7 & Word Count Check
1. Confirm every in-text citation is in correct APA 7 format: (Author et al., Year, p. X) — flag any that are not
2. Confirm the reference list entries are all correctly formatted in APA 7 — flag any errors
3. Recount the main body word count after all additions (exclude headings, figure placeholders, reference list, any remaining notes)
4. If the word count is now over 1,650: identify and remove 1–3 of the least analytically specific sentences from Sections 2 or 3, and report which sentences were removed
5. Report final confirmed word count

### TASK 6 — Final Submission Readiness Report
Produce a brief checklist:
- [ ] All 4 sections present with correct headings
- [ ] Figure 1 placeholder present — student will insert in-store photo here manually in Word
- [ ] Figure 2 placeholder present — student will insert Canva diagram here manually in Word
- [ ] Confirmed in-store price inserted (no placeholders remaining)
- [ ] All in-store observations personalised (no generic descriptions remaining in Section 4)
- [ ] All factual claims cited with APA 7 in-text citations
- [ ] Reference list complete and correctly formatted in APA 7
- [ ] Main body word count confirmed: [X] words — within 1,350–1,650 range: YES/NO
- [ ] ⚠️ REMINDER: Add GenAI acknowledgement statement to cover page in Word
- [ ] ⚠️ REMINDER: Paste all 9 Copilot prompts and key outputs into the Appendix in Word (Swinburne policy)

## OUTPUT FORMAT
- Produce the complete, final assignment in full markdown — all 4 sections plus reference list
- Include the confirmed word count at the end: **Final main body word count: [X] words**
- Follow with the TASK 6 submission readiness report

## SAVE OUTPUT
Use the filesystem MCP tool to overwrite `03_assignment_draft.md` with the final personalised version.
```

---

## PHASE 6 — CONVERT TO WORD & SUBMIT

### Step 12 — Convert Your Markdown Draft to Word (.docx)

**Option A — Pandoc (automatic, 30 seconds):**

Open the VS Code Terminal (`Ctrl+\``) and run:

```powershell
# Check if Pandoc is installed
pandoc --version

# Convert your draft to Word
pandoc 03_assignment_draft.md -o "MKT10009_A1_YOURNAME.docx" -f markdown -t docx

# Optional: generate a reference template for better Word styling
pandoc --print-default-data-file reference.docx > reference.docx
pandoc 03_assignment_draft.md -o "MKT10009_A1_YOURNAME.docx" --reference-doc=reference.docx
```

If Pandoc is not installed, run `winget install pandoc` in PowerShell, or download from pandoc.org.

**Option B — Manual copy-paste into Word (5 minutes):**
1. Press `Ctrl+Shift+V` to open Markdown preview of `03_assignment_draft.md`
2. Select all preview text (`Ctrl+A`) → Copy (`Ctrl+C`)
3. Paste into a new Word document
4. Apply **Heading 1** style to the 4 section headings; **Normal** to body text
5. Insert your in-store photo as Figure 1 in Section 1 (Insert → Pictures)
6. Insert your Canva diagram PNG as Figure 2 in Section 3 (Insert → Pictures)

### Step 13 — Final Pre-Submission Checklist

- [ ] Cover page includes: your name, student number, unit code (MKT10009), unit title, teacher name, assessment title
- [ ] GenAI use statement on cover page — e.g. "I used GitHub Copilot (GPT-4.1) via VS Code to assist with web research, marketing analysis, and drafting. Prompts and outputs are included in the Appendix."
- [ ] In-store photo (Figure 1) inserted in Section 1 — product only, no people visible
- [ ] Canva decision-making map (Figure 2) inserted in Section 3
- [ ] Word count is 1,350–1,650 (check via Word: **Review → Word Count**)
- [ ] Four section headings present and labelled
- [ ] All in-text citations in APA 7 format
- [ ] Reference list at end in APA 7 format
- [ ] Appendix: paste all 9 Copilot prompts and key outputs (Swinburne GenAI policy)
- [ ] File saved as `.docx` or `.pdf`
- [ ] Submitted via Canvas Turnitin before **Wednesday 1 April, 11:59pm**

---

## QUICK REFERENCE — ALL 9 PROMPTS

| #   | Prompt Name                                         | Primary MCP Tools Used                            | Output Saved To        |
| --- | --------------------------------------------------- | ------------------------------------------------- | ---------------------- |
| 1   | Cozy Brand, Product Details & Market Context        | firecrawl, playwright-mcp, tavily-mcp             | 01_research_raw.md     |
| 2   | Price Data, Competitor Comparison & Shelf Placement | firecrawl, tavily-mcp                             | 01_research_raw.md     |
| 3   | Promotions & Digital Marketing Research             | firecrawl, tavily-mcp                             | 01_research_raw.md     |
| 4   | Academic Literature for 4Ps & CX Frameworks         | paper-search-mcp, consensus, tavily-mcp           | 02_analysis_notes.md   |
| 5   | Consumer Decision Process & Sensorial CX Draft      | sequential-thinking, tavily-mcp, paper-search-mcp | 02_analysis_notes.md   |
| 6   | Full Assignment Draft (Sections 1–4 + References)   | filesystem                                        | 03_assignment_draft.md |
| 7   | Rubric Audit & Gap Analysis                         | filesystem, sequential-thinking                   | 02_analysis_notes.md   |
| 8   | Targeted Revision — Apply All Audit Fixes           | filesystem, sequential-thinking                   | 03_assignment_draft.md |
| 9   | Post-Visit Personalisation & Final Submission Check | filesystem, sequential-thinking                   | 03_assignment_draft.md |

---

## TROUBLESHOOTING

**Copilot is not using MCP tools (no web searching happening):**
Click the **Tools icon** (plug/wrench symbol) in the Copilot Chat toolbar → verify `tavily-mcp`, `firecrawl`, `paper-search-mcp`, `sequential-thinking`, and `filesystem` are toggled ON. If greyed out: open Command Palette (`Ctrl+Shift+P`) → type `MCP: Restart Server` → select the affected tool. Then re-run the prompt.

**firecrawl cannot scrape a Shopee page (JavaScript-rendered):**
Shopee pages use heavy JavaScript and may block scrapers. If firecrawl returns empty content for a Shopee URL, add to the prompt: `"If firecrawl cannot fully render the Shopee page, use playwright-mcp to navigate to the URL, wait for the page to fully load, then extract all visible text."` Then re-run.

**The filesystem MCP is not saving to the correct files:**
Ensure VS Code has the `Assignment1/` folder open as the workspace root. Check via `Ctrl+Shift+E` that all 4 `.md` files are visible. If needed, tell Copilot the full path explicitly: `"Save to: Documents/MKT10009/Assignment1/01_research_raw.md"`

**paper-search-mcp returns no results for FMCG Vietnam pricing:**
Remove "Vietnam" from the query and search for FMCG pricing in developing markets or Southeast Asian retail generally. Armstrong et al. (2021) is sufficient as the primary reference for pricing strategy frameworks.

**The draft is over 1,650 words after Prompt 8:**
Run: `"Read 03_assignment_draft.md. Without removing any citations, specific product examples, figure placeholders, or the personalisation note: identify 3–5 sentences that are the most generic or that repeat an idea already stated. Remove them. Report each sentence removed and the new word count."`

**The Lotte Mart website shows price as "32.900₫":**
In Vietnamese number formatting, the full stop is a thousands separator (not a decimal point). So "32.900₫" = 32,900 VND (thirty-two thousand nine hundred dong).

---

*Guide version 2.1 — MKT10009 S1 2026, Swinburne University of Technology*
*Product: Cozy Trà Đen Nhãn Vàng Túi Lọc (Hộp 25 Gói × 2g) | Retailer: Lotte Mart Đà Nẵng, 06 Nại Nam Street*
