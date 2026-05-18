---
name: keyword-research-v9

description: >
  A Comprehensive SEO keyword research skill. Use this whenever a user asks for keyword ideas,
  keyword lists, keyword strategy, keyword clustering, keyword mapping, search intent analysis,
  and topical authority planning. This skill handles everything from seed expansion to intent classification,
  topic-based clustering, and prioritized output with strategic insights.
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
1. **Website URL** — The business's website (e.g., "https://example.com").
2. **Niche** — The subject area or industry (e.g., "diving")
3. **Seed Keyword(s)** — One or more starting keywords (e.g., "scuba diving, diving courses")
4. **Target Country/City** — Where the audience is located (e.g., "Egypt/Hurghada")
5. **Target Language** — Language of the content (e.g., "English"). Possibly note "if bilingual, we may run separate keyword lists per language."
6. **Business Type** — local dive shop, liveaboard operator, diving center, dive travel agency, etc.
7. **Target Audience** — Who the content is for (e.g., "beginner divers, family vacationers, certified divers looking for liveaboards")
8. **Topics List** — A list of the business's specific topics (e.g., "Scuba Diving, Diving Courses, Snorkeling, Diving Trips, Diving Destinations"). Each topic becomes the name of its keyword cluster. Note: If the user provides no topics at all, suggest 3–5 common topics based on the Business Type, and ask the user to confirm and rank them before proceeding.
 
If inputs are too broad (e.g., "diving"), ask the user to narrow the niche before
proceeding. See [Edge Cases](#edge-cases) for handling guidance.

If all required inputs are present, echo back a brief input summary before proceeding:

> **Starting keyword research with the following inputs:**
> - Website: [X]
> - Niche: [X]
> - Seed Keywords: [X]
> - Location: [X]
> - Language: [X]
> - Business Type: [X]
> - Audience: [X]
> - Topics: [X]

Then proceed immediately to Step 1.

---
 
## Step 1 — Keyword Expansion
 
Generate **10–20 keywords per topic**.
The total keyword count across all topics must be a minimum of **50 keywords**.

For each topic, generate keywords across these intent categories:
 
| Category | Examples |
|---|---|
| **A. Core / Head Terms** | Primary topic keywords, 1–2 words |
| **B. Long-Tail Variants** | 3–6 word phrases, more specific intent |
| **C. Commercial Investigation** | best, top, reviews, comparison, vs, alternative |
| **D. Transactional** | pricing, cost, buy, hire, quote, book, enroll, get started |
| **E. Problem-Based** | how to, why, fix, improve, strategy, tips |
| **F. Informational / Educational** | guide, tutorial, checklist, template, what is |
| **G. Location Modifiers** | Country, major cities, "near me" — only if local intent is relevant |
| **H. Industry-Specific Modifiers** | Niche terminology, tools, certifications |

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
 
Each topic provided by the user is its own cluster. The **Cluster Name = Topic Name** (e.g., Topic "Scuba Diving Hurghada" → Cluster "Scuba Diving"). Do not create sub-clusters or merge topics.

**Each cluster must contain:**
- **Cluster Name** — Identical to the topic name
- **Pillar Keyword** — The single highest-value, most representative keyword for that topic
- **Supporting Keywords** — All remaining keywords for that topic

**Clustering Rules:**
- Each topic has exactly one cluster
- Each keyword belongs to exactly one cluster (no duplicates across clusters)
- Pillar keyword must have the highest weighted score in its cluster
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
This score measures **business value and realistic ranking opportunity** — not search volume and not intent type.
A high-value, realistic-to-rank keyword always outscores a high-volume keyword with no conversion path, regardless of intent.

Assign a score using this logic:
 
| Score | Criteria |
|---|---|
| **5** | Very high topical relevance + strong business value (conversion, revenue, or authority) + realistic ranking opportunity |
| **4** | High topical relevance + clear business value signal (buying, booking, or strong research intent) |
| **3** | Moderate topical relevance + content gap or topical authority value |
| **2** | Weak or unclear relevance, limited business value |
| **1** | Too broad, too competitive with no realistic opportunity, or negligible business value |

Keywords are sorted by Weighted Score (highest first) within each topic table.
 
---
 
## Step 5 — Output Format (Mandatory)
 
Always produce **both outputs** in this exact order and structure.
 
---
 
### OUTPUT A — Keyword Table (One Per Topic)

Output one **separate table per topic**.
Each table is preceded by a Topic Header block.

**Topic Header (before each table):**
```
---
### 🟦 Topic: [Topic Name]
- Cluster: [Topic Name]
- Pillar Keyword: [most important keyword for this topic]
- Suggested Page Type: Hub-Service Page
- Suggested URL Slug: /[slug]
---
```

> ⚠️ **Page Type Rule:** Each topic cluster has exactly **one Hub-Service Page** — the Pillar Keyword row only. All other keywords in the table are **Sub-Service Page** or **Blog Post**.

**Table format:**
```
| # | Keyword | Cluster | Intent | Vol. | Weighted | Page Type | Alternatives |
|---|---------|---------|--------|------|----------|-----------|--------------|
```

**Column rules:**
- **#** — Row number within the table, sorted by Weighted Score descending (5 → 1)
- **Keyword** — The target keyword phrase
- **Cluster** — Always the Topic Name for every row in this table
- **Intent:** Informational / Commercial / Transactional / Navigational
- **Vol.:** Medium / High / Very High / Massive
- **Weighted:** 1 / 2 / 3 / 4 / 5
- **Page Type:** Hub-Service Page (Pillar Keyword only, one per table) / Sub-Service Page / Blog Post
- **Alternatives** — Exactly 3 synonym/variant phrasings of the keyword, comma-separated. Example: for "Scuba Diving Hurghada" → "Hurghada Scuba Diving, Diving in Hurghada, Hurghada Dive Experience"

---
 
### OUTPUT B — Strategic Insights

Always include all three sections:

```
## Strategic Insights

### 1. Top 5 Quick Wins
[Keywords with Weighted Score 4–5, Medium+ volume, and realistic ranking opportunity — fastest wins.
Must include the topic/cluster name next to each keyword.]

### 2. Content Gaps
[Topics or intents not covered by existing clusters that represent missed opportunity.
Flag any topic with fewer than 3 high-weighted keywords (score 4–5) as under-served.]

### 3. Topical Authority Notes
[Which topic clusters build the most topical depth and should be prioritized for E-E-A-T signals.
Note which topics have the strongest cross-linking potential.]
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
| **No topics provided** | Suggest 3–5 common topics based on Business Type. Ask user to confirm and rank before proceeding. |
| **Only 1–2 topics provided** | Generate 20 keywords per topic to reach the 50-keyword minimum. |
---
 
## Hard Rules (Never Violate)
 
- ❌ Never output exact numeric search volume values (e.g., "3,600/mo")
- ❌ Never fabricate brand names, competitor names, or product names
- ❌ Never include duplicate keywords across any topic table
- ❌ Never assign Hub-Service Page to more than one keyword per topic table
- ❌ Never skip OUTPUT B — strategic insights are mandatory
- ❌ Never sort by intent — always sort by Weighted Score descending
- ❌ Never output a single combined keyword table — always one table per topic
- ❌ Never output a Cluster + Pillar Page Map section (Output B in old versions) — it has been removed
- ✅ Always use range labels for volume
- ✅ Always generate 10–20 keywords per topic, minimum 50 total
- ✅ Always output A → B in order
- ✅ Always include exactly 3 alternatives per keyword in the Alternatives column
- ✅ Always use Topic Name as the Cluster name for every row in that topic's table

---
 
## Example
 
**Input:**
- Niche: Scuba Diving
- Seed Keyword: Diving Courses, Liveaboard Red Sea
- Country: Egypt/Hurghada
- Language: English
- Business Type: Local dive center with liveaboard operations
- Audience: Beginner divers, divers seeking diving courses, tourist families, adventure travelers booking liveaboards
- Topics: Scuba Diving, Liveaboard, Snorkeling

---

**Example Output A — Topic:**

```
---
### 🟦 Topic: Scuba Diving
- Cluster: Scuba Diving
- Pillar Keyword: Scuba Diving Hurghada
- Suggested Page Type: Hub-Service Page
- Suggested URL Slug: /scuba-diving-hurghada
---
 
| # | Keyword | Cluster | Intent | Vol. | Weighted | Page Type | Alternatives |
|---|---------|---------|--------|------|----------|-----------|--------------|
| 1 | Scuba Diving Hurghada | Scuba Diving | Transactional | Very High | 5 | Hub-Service Page | Hurghada Scuba Diving, Diving in Hurghada, Hurghada Dive Experience |
| 2 | book scuba diving Hurghada | Scuba Diving | Transactional | High | 5 | Sub-Service Page | reserve scuba diving Hurghada, Hurghada diving booking, scuba dive booking Red Sea |
| 3 | best dive sites Hurghada | Scuba Diving | Commercial | High | 4 | Sub-Service Page | top diving spots Hurghada, Hurghada top dive sites, best Hurghada diving locations |
```
 
---
 
## Reference Files
 
- `references/intent-patterns.md` — Detailed keyword patterns per intent type and funnel stage
- `references/industry-modifiers.md` — Industry-specific modifier lists (SaaS, e-commerce, local, health, legal, finance)
Read these only when you need additional pattern examples for niche industries or complex intent classification edge cases.
