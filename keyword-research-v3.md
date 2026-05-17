---
name: keyword-research-v3
description: >
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
 
Before generating any keywords, confirm you have all the required inputs. If any are missing, ask
for them in a single message — do not guess or proceed without them.
 
**Required:**
1. **Topic / Niche** — The subject area or industry (e.g., "diving")
2. **Seed Keyword(s)** — One or more starting keywords (e.g., "scuba diving, diving courses")
3. **Target Country/City** — Where the audience is located (e.g., "Egypt/Hurghada")
4. **Target Language** — Language of the content (e.g., "English"). Possibly note “if bilingual, we may run separate keyword lists per language.”
5. **Business Type** — local dive shop, liveaboard operator, diving center, dive travel agency, etc.
6. **Target Audience** — Who the content is for (e.g., "beginner divers, family vacationers, certified divers looking for liveaboards")
7. **Competitor URLs** — 1–3 competitors to generate alternative/comparison keywords
 
If inputs are too broad (e.g., "diving"), ask the user to narrow the niche before
proceeding. See [Edge Cases](#edge-cases) for handling guidance.

If all required inputs are present:
Echo back a brief input summary before proceeding:
"Starting keyword research with the following inputs:
Topic: [X]
Seed Keywords: [X]
Location: [X]
Language: [X]
Business Type: [X]
Audience: [X]
Competitors: [X]"
Then proceed immediately to Step 1. 

---
 
## Step 1 — Keyword Expansion
 
Generate a minimum of **50 keywords**, covering all of the following categories:
 
| Category | Examples |
|---|---|
| **A. Core / Head Terms** | Primary topic keywords, 1–2 words |
| **B. Long-Tail Variants** | 3–6 word phrases, more specific intent |
| **C. Commercial Investigation** | best, top, reviews, comparison, vs, alternative |
| **D. Transactional** | pricing, cost, buy, hire, quote, book, enroll, get started |
| **E. Problem-Based** | how to, why, fix, improve, strategy, tips |
| **F. Informational / Educational** | guide, tutorial, checklist, template, what is |
| **G. Competitor Alternatives** | "[Competitor] alternative", "[X] vs [Y]" |
| **H. Location Modifiers** | Country, major cities, "near me" — only if local intent is relevant |
| **I. Industry-Specific Modifiers** | Niche terminology, tools, certifications |
 
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
- `Informational` — User wants to learn, understand, or explore a topic
- `Commercial` — User is researching options before making a decision
- `Transactional` — User is ready to act — book, buy, enroll, contact, hire
- `Navigational` — User is looking for a specific brand or page
---
 
## Step 3 — Clustering
 
Group keywords into **thematic clusters** based on:
1. Same search intent — Informational, Commercial, or Transactional (never mix)
2. Same SERP target — Would Google plausibly rank a single page for both keywords?
Use this test: if targeting both keywords would require two different page structures or two different CTAs, they belong in separate clusters.
3. Same topical scope — Keywords address the same subject at the same level of specificity (e.g., do not mix course-level keywords with certification-body overview keywords)

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
| Medium | 0–10 searches/mo |
| High | 10–100 |
| Very High | 100–1K |
| Massive | 1K–10K |
 
### Weighted Score (1–5)
This score measures business value and realistic ranking opportunity — not search volume.
A low-volume, high-converting Transactional keyword always outscores a high-volume Informational keyword with no conversion path.

Assign a score using this logic — apply strictly in order:
 
| Score | Criteria |
|---|---|
| **5** | Transactional + very high topical relevance + strong conversion intent + realistic ranking opportunity |
| **4** | Commercial + high topical relevance + clear buying signal |
| **3** | Informational + strong topical relevance + strong topical authority or content gap value |
| **2** | Weak or unclear intent, moderate topical relevance with limited business value |
| **1** | Too broad, too competitive with no realistic opportunity, or low business value |
 
---
 
## Step 5 — Output Format (Mandatory)
 
Always produce **all three outputs** in this exact order and structure.
 
---
 
### OUTPUT A — Keyword Table
 
```
| Keyword | Cluster | Intent | Vol. | Weighted | Page Type |
|---------|---------|--------|------|----------|-----------|
```
 
**Allowed values per column:**
- **Intent:** Informational / Commercial / Transactional / Navigational
- **Vol.:** Low / Medium / High / Very High
- **Weighted:** 1 / 2 / 3 / 4 / 5
- **Page Type:** Core Page (e.g., "diving center") / Hub-Service Page (e.g., "PADI Courses, Liveaboards") / Sub-Service Page (e.g., "Open Water Course, Hurghada Diving Safari, 7-Night Red Sea Liveaboard") / Blog Post
---
 
### OUTPUT B — Cluster + Pillar Page Map
 
For each cluster, output this block:
 
```
## Cluster: [Cluster Name]
- Pillar Keyword: [keyword]
- Intent: [intent]
- Page Type: [page type]
- Suggested URL Slug: /[slug — lowercase, hyphens only, no stop words]
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
[Keywords that are low-difficulty, low or medium+ volume, and high priority — fastest ranking opportunities]
 
### 2. Content Gaps
[Topics or intents not covered by existing clusters that represent missed opportunity]
 
### 3. Topical Authority Notes
[Which clusters build the most topical depth and should be prioritized for E-E-A-T signals]
```
 
---
 
## Edge Cases
 
| Situation | Behavior |
|---|---|
| **Topic too broad** (e.g., "diving") | Ask user to narrow to a sub-niche before proceeding. Suggest 3 options. |
| **Multiple niches provided** | Treat each as a separate seed. Create distinct cluster groups per niche. Label clearly. |
| **No seed keyword provided** | Derive 3–5 seed suggestions from the topic/niche, ask user to confirm before expanding. |
| **No country provided** | Default to Egypt. State the assumption explicitly. |
| **Local business** | Add location modifier column to keyword table. Include city + region variants. |
| **No competitor URLs** | Skip competitor alternative keywords. Do not fabricate competitor names. |
 
---
 
## Hard Rules (Never Violate)
 
- ❌ Never output exact numeric search volume values (e.g., "3,600/mo")
- ❌ Never fabricate brand names, competitor names, or product names
- ❌ Never include duplicate keywords across the keyword table
- ❌ Never merge clusters with different search intents
- ❌ Never skip OUTPUT C — strategic insights are mandatory
- ✅ Always use range labels for volume and difficulty
- ✅ Always include a minimum of 50 keywords and clusters
- ✅ Always output A → B → C in order
---
 
## Example
 
**Input:**
- Topic: Scuba Diving
- Seed Keyword: Diving Courses
- Country: Egypt/Hurghada
- Language: English
- Business Type: Local dive center with liveaboard operations
- Audience: Beginner divers, divers seeking diving courses, tourist families, adventure travelers booking liveaboards
**Example Output A rows (abbreviated):**
 
| Keyword | Cluster | Intent | Vol. | Weighted | Page Type |
| Open Water Course | Diving Course | Transactional | High | 4 | Sub-Service Page |
 
**Example Output B (one cluster):**
 
```
## Cluster: Diving Courses
- Pillar Keyword: Open Water Course Hurghada
- Intent: Transactional
- Page Type: Sub-Service Page
- Suggested URL Slug: /open-water-course
- Supporting Keywords: book OWD course Hurghada, enroll open water course,
PADI courses Red Sea review, how to get PADI certified, Open Water vs Discover Scuba, how long does PADI Open Water take
- Content Angle: Targets first-time divers and vacationers ready to get certified during their Hurghada trip.
Covers course structure, what's included, pool vs open water sessions, and certification validity worldwide.
Primary CTA: "Book your PADI Open Water Course"
- Suggested Internal Links: /beginner-diving-courses, /dive-center-hurghada, /red-sea-dive-sites
```
 
---
 
## Reference Files
 
- `references/intent-patterns.md` — Detailed keyword patterns per intent type and funnel stage
- `references/industry-modifiers.md` — Industry-specific modifier lists (SaaS, e-commerce, local, health, legal, finance)
Read these only when you need additional pattern examples for niche industries or complex intent classification edge cases.
 
