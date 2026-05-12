# Name: keyword-research-v3
---

# Description:
A Comprehensive SEO keyword research skill. Use this whenever a user asks for keyword ideas, 
keyword lists, keyword strategy, keyword clustering, keyword mapping, search intent analysis, 
and topical authority planning. This skill handles everything from seed expansion to intent classification, 
clustering, pillar page mapping, and prioritized output.
---
 
# Keyword Research Skill
 
**Goal:** Given a business topic or seed keyword, generate a structured, intent-classified,
clustered, and prioritized keyword research plan ready for SEO content strategy — with no
reliance on live data tools.
 
---
 
## Scope
 
This skill handles **keyword research only**. It does not write content, generate meta tags,
perform site audits, or produce schema markup. For those, use the appropriate dedicated skill.
 
---
 
## Step 0 — Collect Required Inputs
 
Before generating any keywords, confirm you have all required inputs. If any are missing, ask
for them explicitly — do not guess or proceed without them.
 
**Required:**
1. **Topic / Niche** — The subject area or industry (e.g., "diving")
2. **Seed Keyword(s)** — One or more starting keywords (e.g., "scuba diving, diving courses, diving Hurghada")
3. **Target Country/City** — Where the audience is located (e.g., "Egypt/Red Sea/Hurghada")
4. **Target Language** — Language of the content (e.g., "English"). Possibly note “if bilingual, we may run separate keyword lists per language.”
**Optional (ask if relevant):**
5. **Business Type** — local dive shop, liveaboard operator, diving center, dive travel agency, etc.
6. **Target Audience** — Who the content is for (e.g., "beginner scuba divers, certified divers, family vacationers to Hurghada, wreck divers")
7. **Competitor URLs** — 1–3 competitors to generate alternative/comparison keywords
 
If inputs are too broad (e.g., "diving"), ask the user to narrow the niche before
proceeding.
 
---
 
## Step 1 — Keyword Expansion
 
Generate a minimum of **60 keywords**, covering all of the following categories:
 
| Category | Examples |
|---|---|
| **A. Core / Head Terms** | Primary topic keywords, 1–2 words |
| **B. Long-Tail Variants** | 3–6 word phrases, more specific intent |
| **C. Commercial Investigation** | best, top, reviews, comparison, vs, alternative |
| **D. Transactional** | pricing, cost, buy, hire, quote, book, get started |
| **E. Problem-Based** | how to, why, fix, improve, strategy, tips |
| **F. Informational / Educational** | guide, tutorial, checklist, template, what is |
| **G. Competitor Alternatives** | "[Competitor] alternative", "[X] vs [Y]" |
| **H. Location Modifiers** | Country, major cities, "near me" — only if local intent is relevant |
| **I. Industry-Specific Modifiers** | Niche terminology, job titles, tools, certifications |
 
**Expansion Rules:**
- Include both short-tail (1–2 words) and long-tail (3–6 words) keywords
- No duplicate keywords (exact or near-identical phrasing)
- All keywords must be in the target language
- Use natural language phrasing — avoid keyword stuffing or unnatural constructions
- Do not fabricate branded names unless the user provided them
---
 
## Step 2 — Intent Classification
 
For every keyword, assign **both** of the following:
 
**Search Intent:**
- `Informational` — User wants to learn something
- `Commercial` — User is researching before buying
- `Transactional` — User is ready to act (buy, sign up, hire)
- `Navigational` — User is looking for a specific brand or page
**Funnel Stage:**
- `TOFU` (Top of Funnel) — Awareness, problem discovery
- `MOFU` (Middle of Funnel) — Evaluation, comparison
- `BOFU` (Bottom of Funnel) — Decision, conversion
---
 
## Step 3 — Clustering
 
Group keywords into **thematic clusters** based on:
1. Shared search intent
2. Topical similarity (would Google rank the same page for these?)
3. Funnel stage alignment
**Each cluster must contain:**
- **Cluster Name** — A short, descriptive label
- **Pillar Keyword** — The single highest-value, most representative keyword
- **Supporting Keywords** — 10–20 related keywords that support the pillar
**Clustering Rules:**
- Minimum 6 clusters
- Each keyword belongs to exactly one cluster (no duplicates across clusters)
- Pillar keyword must have the highest priority score in its cluster
- Do not merge clusters that have different intents (e.g., informational ≠ transactional)
---
 
## Step 4 — Estimated Metrics
 
You do not have access to live keyword data. Use the following **range labels only** — never
output exact numeric values.
 
### Estimated Search Volume
| Label | Range |
|---|---|
| Very Low | 0–50 searches/mo |
| Low | 50–200 |
| Medium | 200–1,000 |
| High | 1,000–5,000 |
| Very High | 5,000+ |
 
### Estimated CPC
| Label | Range |
|---|---|
| Low | $0.10–$1.00 |
| Medium | $1.00–$5.00 |
| High | $5.00–$20.00 |
| Very High | $20.00+ |
 
### Estimated Difficulty
`Low` | `Medium` | `High`
(Based on: head terms = harder, long-tail = easier, branded/niche = varies)
 
### Priority Score (1–5)
Assign a score using this logic — apply strictly in order:
 
| Score | Criteria |
|---|---|
| **5** | BOFU + Transactional + high commercial relevance + realistic ranking opportunity |
| **4** | MOFU + Commercial + strong buying signal |
| **3** | TOFU + Informational + strong topical authority or content gap value |
| **2** | Weak or unclear intent, tangential relevance |
| **1** | Too broad, too competitive with no realistic opportunity, or low business value |
 
**Important:** Priority is about business value and ranking opportunity — not just volume.
A low-volume, high-converting BOFU keyword always beats a high-volume TOFU keyword.
 
---
 
## Step 5 — Output Format (Mandatory)
 
Always produce **all three outputs** in this exact order and structure.
 
---
 
### OUTPUT A — Keyword Table
 
```
| Keyword | Cluster | Intent | Funnel | Vol. | CPC | Difficulty | Priority | Page Type |
|---------|---------|--------|--------|------|-----|------------|----------|-----------|
```
 
**Allowed values per column:**
- **Intent:** Informational / Commercial / Transactional / Navigational
- **Funnel:** TOFU / MOFU / BOFU
- **Vol.:** Very Low / Low / Medium / High / Very High
- **CPC:** Low / Medium / High / Very High
- **Difficulty:** Low / Medium / High
- **Priority:** 1 / 2 / 3 / 4 / 5
- **Page Type:** Landing Page / Service Page / Blog Post / Category Page / Comparison Page / FAQ Page
---
 
### OUTPUT B — Cluster + Pillar Page Map
 
For each cluster, output this block:
 
```
## Cluster: [Cluster Name]
- Pillar Keyword: [keyword]
- Intent: [intent]
- Funnel Stage: [stage]
- Page Type: [page type]
- Suggested URL Slug: /[slug]
- Supporting Keywords: [comma-separated list]
- Content Angle: [1–2 sentence description of the angle this page should take]
- Suggested Internal Links: [list 2–3 other clusters/pages this should link to]
```
 
---
 
### OUTPUT C — Strategic Insights
 
Always include all five sections:
 
```
## Strategic Insights
 
### 1. Top 5 Quick Wins
[Keywords that are low-difficulty, medium+ volume, and high priority — fastest ranking opportunities]
 
### 2. Best BOFU Clusters
[Clusters most likely to drive conversions — list cluster name + pillar keyword]
 
### 3. Content Gaps
[Topics or intents not covered by existing clusters that represent missed opportunity]
 
### 4. Recommended Publishing Order (First 10 Pages)
[Ordered list with cluster name, page type, and URL slug]
 
### 5. Topical Authority Notes
[Which clusters build the most topical depth and should be prioritized for E-E-A-T signals]
```
 
---
 
## Edge Cases
 
| Situation | Behavior |
|---|---|
| **Topic too broad** (e.g., "technology") | Ask user to narrow to a sub-niche before proceeding. Suggest 3 options. |
| **Multiple niches provided** | Treat each as a separate seed. Create distinct cluster groups per niche. Label clearly. |
| **No seed keyword provided** | Derive 3–5 seed suggestions from the topic/niche, ask user to confirm before expanding. |
| **No country provided** | Default to United States. State the assumption explicitly. |
| **Local business** | Add location modifier column to keyword table. Include city + region variants. |
| **B2B SaaS** | Weight MOFU/commercial keywords higher. Emphasize comparison, integration, and ROI keywords. |
| **E-commerce** | Weight transactional keywords highest. Add product-type and category keywords. |
| **No competitor URLs** | Skip competitor alternative keywords. Do not fabricate competitor names. |
 
---
 
## Hard Rules (Never Violate)
 
- ❌ Never output exact numeric search volume or CPC values (e.g., "3,600/mo" or "$4.20")
- ❌ Never fabricate brand names, competitor names, or product names
- ❌ Never include duplicate keywords across the keyword table
- ❌ Never merge clusters with different search intents
- ❌ Never skip OUTPUT C — strategic insights are mandatory
- ✅ Always use range labels for volume, CPC, and difficulty
- ✅ Always include a minimum of 60 keywords and 6 clusters
- ✅ Always output A → B → C in order
---
 
## Example
 
**Input:**
- Topic: Project management software
- Seed Keyword: project management tool
- Country: United States
- Language: English
- Business Type: B2B SaaS
- Audience: Small business owners and team leads
**Example Output A rows (abbreviated):**
 
| Keyword | Cluster | Intent | Funnel | Vol. | CPC | Difficulty | Priority | Page Type |
|---|---|---|---|---|---|---|---|---|
| project management software | Core Tools | Commercial | MOFU | Very High | High | High | 4 | Landing Page |
| best project management tool for small teams | Comparison | Commercial | MOFU | Medium | High | Medium | 5 | Comparison Page |
| how to manage remote teams effectively | Remote Work Tips | Informational | TOFU | Medium | Low | Low | 3 | Blog Post |
| project management software pricing | Pricing | Transactional | BOFU | Medium | Very High | Medium | 5 | Landing Page |
| asana alternative | Competitor Alt | Commercial | MOFU | High | High | Medium | 5 | Comparison Page |
 
**Example Output B (one cluster):**
 
```
## Cluster: Pricing & Plans
- Pillar Keyword: project management software pricing
- Intent: Transactional
- Funnel Stage: BOFU
- Page Type: Landing Page
- Suggested URL Slug: /project-management-software/pricing
- Supporting Keywords: project management tool cost, cheap project management software,
  free project management tool, project management software free trial
- Content Angle: Transparent pricing comparison targeting decision-ready buyers evaluating
  plans. Include a pricing table, feature comparison, and free trial CTA.
- Suggested Internal Links: /features, /compare, /get-started
```
 
---
 
## Reference Files
 
- `references/intent-patterns.md` — Detailed keyword patterns per intent type and funnel stage
- `references/industry-modifiers.md` — Industry-specific modifier lists (SaaS, e-commerce, local, health, legal, finance)
Read these only when you need additional pattern examples for niche industries or complex intent classification edge cases.
 
