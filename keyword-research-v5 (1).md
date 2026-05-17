---
name: keyword-research-v5
description: >
  A Comprehensive SEO keyword research skill. Use this whenever a user asks for keyword ideas,
  keyword lists, keyword strategy, keyword clustering, keyword mapping, search intent analysis,
  and topical authority planning. This skill handles everything from seed expansion to intent classification,
  clustering, pillar page mapping, and prioritized output — organized per service.
---

# Keyword Research Skill

**Goal:** Given a business topic, seed keywords, and a list of services, generate a structured,
intent-classified, clustered, and prioritized keyword research plan — organized per service —
ready for SEO content strategy, with no reliance on live data tools.

---

## Scope

This skill handles **keyword research only**. It does not write content, generate meta tags,
perform site audits, or produce schema markup. For those, use the appropriate dedicated skill.

---

## Step 0 — Collect Required Inputs

Before generating any keywords, confirm you have all the required inputs. If any are missing,
ask for them in a single message — do not guess or proceed without them.

**Required:**
1. **Topic / Niche** — The subject area or industry (e.g., "diving")
2. **Seed Keyword(s)** — One or more starting keywords (e.g., "scuba diving, diving courses")
3. **Target Country/City** — Where the audience is located (e.g., "Egypt/Hurghada")
4. **Target Language** — Language of the content (e.g., "English"). Note: if bilingual, run separate keyword lists per language.
5. **Business Type** — local dive shop, liveaboard operator, diving center, dive travel agency, etc.
6. **Target Audience** — Who the content is for (e.g., "beginner divers, family vacationers, certified divers looking for liveaboards")
7. **Competitor URLs** — 1–3 competitors to generate alternative/comparison keywords
8. **Services List (Prioritized)** — A list of the business's specific services, ordered from most to least important to the business (e.g., "1. Open Water Course, 2. Liveaboard Red Sea, 3. Snorkeling Trip, 4. Advanced Course")

**Rules for the Services List:**
- If the user provides services without a priority order, ask them to rank by business importance before proceeding.
- If the user provides no services at all, suggest 5–8 common services based on the Business Type, and ask the user to confirm and rank them before proceeding.
- The output will follow the exact priority order provided — the most important service appears first.

If inputs are too broad (e.g., "diving"), ask the user to narrow the niche before proceeding.
See [Edge Cases](#edge-cases) for handling guidance.

**If all required inputs are present**, echo back a brief input summary before proceeding:

> "Starting keyword research with the following inputs:
> - Topic: [X]
> - Seed Keywords: [X]
> - Location: [X]
> - Language: [X]
> - Business Type: [X]
> - Audience: [X]
> - Competitors: [X]
> - Services (in priority order): [1. X, 2. X, 3. X ...]"

Then proceed immediately to Step 1.

---

## Step 1 — Keyword Expansion Per Service

Generate **10–20 keywords per service**, following the priority order from Step 0.
The total keyword count across all services must be a minimum of **50 keywords**.

For each service, generate keywords across these intent categories — distributed by the
**Intent Distribution Rules** below:

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

### Intent Distribution Rules (Per Service)

Apply this distribution to every service's keyword set:

| Intent | Target Share | Rationale |
|---|---|---|
| **Transactional** | 40–50% | Highest business value — prioritize booking, enrollment, contact keywords |
| **Commercial** | 25–30% | Buyers researching — high conversion potential |
| **Informational** | 20–30% | Topical authority and content gap coverage |
| **Navigational** | 0–5% | Only if the business has a named brand worth targeting |

**Rule:** Never invert this distribution. Transactional keywords must always be the largest group per service.

**Expansion Rules:**
- Include both short-tail (1–2 words) and long-tail (3–6 words) keywords
- No duplicate keywords across any service (exact or near-identical phrasing)
- All keywords must be in the target language
- Use natural language phrasing — avoid keyword stuffing or unnatural constructions
- Do not fabricate branded names unless the user provided them

---

## Step 2 — Intent Classification

For every keyword, assign the following:

**Search Intent:**
- `Informational` — User wants to learn, understand, or explore a topic
- `Commercial` — User is researching options before making a decision
- `Transactional` — User is ready to act — book, buy, enroll, contact, hire
- `Navigational` — User is looking for a specific brand or page

---

## Step 3 — Clustering

Group keywords into **thematic clusters per service** based on:
1. Same search intent — Informational, Commercial, or Transactional (never mix)
2. Same SERP target — Would Google plausibly rank a single page for both keywords?
   Use this test: if targeting both keywords would require two different page structures or two different CTAs, they belong in separate clusters.
3. Same topical scope — Keywords address the same subject at the same level of specificity

**Each cluster must contain:**
- **Cluster Name** — A short, descriptive label
- **Pillar Keyword** — The single highest-value, most representative keyword
- **Supporting Keywords** — Related keywords that support the pillar

**Clustering Rules:**
- Each service must have at least 1 dedicated cluster
- Each keyword belongs to exactly one cluster (no duplicates across clusters)
- Pillar keyword must have the highest priority score in its cluster
- Do not merge clusters that have different intents (e.g., informational ≠ transactional)
- Do not merge clusters from different services

---

## Step 4 — Estimated Metrics

You do not have access to live keyword data. Use the following **range labels only** — never
output exact numeric values.

### Estimated Search Volume
| Label | Range |
|---|---|
| Low | 0–10 searches/mo |
| Medium | 10–100 |
| High | 100–1K |
| Very High | 1K–10K |

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

### OUTPUT A — Keyword Tables (One Per Service)

Output one **separate table per service**, in the same priority order from Step 0.
Each table is preceded by a Service Header block.

**Service Header (before each table):**
```
---
### 🟦 Service [#]: [Service Name]
- Priority: [#] of [total services]
- Pillar Keyword: [most important keyword for this service]
- Suggested Page Type: [Core Page / Hub-Service Page / Sub-Service Page / Blog Post]
- Suggested URL Slug: /[slug]
---
```

**Table format:**
```
| Keyword | Cluster | Intent | Vol. | Weighted | Page Type |
|---------|---------|--------|------|----------|-----------|
```

**Allowed values per column:**
- **Intent:** Informational / Commercial / Transactional / Navigational
- **Vol.:** Low / Medium / High / Very High
- **Weighted:** 1 / 2 / 3 / 4 / 5
- **Page Type:** Core Page / Hub-Service Page / Sub-Service Page / Blog Post

After all service tables, output a **Master Summary Table** with all keywords combined, sorted by Weighted score descending.

---

### OUTPUT B — Cluster + Pillar Page Map (Per Service)

For each service, output all its clusters grouped under a service label:

```
## 🟦 Service [#]: [Service Name]

### Cluster: [Cluster Name]
- Pillar Keyword: [keyword]
- Intent: [intent]
- Page Type: [page type]
- Suggested URL Slug: /[slug — lowercase, hyphens only, no stop words]
- Supporting Keywords: [comma-separated list]
- Content Angle: [1–2 sentence description of the angle this page should take]
- Suggested Internal Links: [2–3 links to other service pages or clusters — cross-service linking encouraged]
```

**Cross-Service Internal Linking Rule:**
Every cluster's "Suggested Internal Links" must include at least one link to a **different service's page**, to build site-wide topical authority and improve crawl depth.

---

### OUTPUT C — Strategic Insights

Always include all three sections:

```
## Strategic Insights

### 1. Top 5 Quick Wins
[Keywords that are low-difficulty, Medium+ volume, and Weighted 4–5 — fastest ranking opportunities.
Must include the service name next to each keyword.]

### 2. Content Gaps
[Topics or intents not covered by existing clusters that represent missed opportunity.
Flag any service with fewer than 3 Transactional keywords as under-served.]

### 3. Topical Authority Notes
[Which service clusters build the most topical depth and should be prioritized for E-E-A-T signals.
Note which services have the strongest cross-linking potential.]
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
| **No services provided** | Suggest 5–8 common services based on Business Type. Ask user to confirm and rank before proceeding. |
| **Services provided without ranking** | Ask user to rank by business importance before proceeding. Do not assume a default order. |
| **Only 1–2 services provided** | Generate 20 keywords per service to reach the 50-keyword minimum. |

---

## Hard Rules (Never Violate)

- ❌ Never output exact numeric search volume values (e.g., "3,600/mo")
- ❌ Never fabricate brand names, competitor names, or product names
- ❌ Never include duplicate keywords across any service table
- ❌ Never merge clusters with different search intents
- ❌ Never merge clusters from different services
- ❌ Never skip OUTPUT C — strategic insights are mandatory
- ❌ Never invert the intent distribution — Transactional must always be the largest group per service
- ❌ Never output a single combined keyword table — always one table per service
- ✅ Always use range labels for volume and difficulty
- ✅ Always generate 10–20 keywords per service, minimum 50 total
- ✅ Always follow the service priority order from Step 0 throughout all outputs
- ✅ Always output A → B → C in order
- ✅ Always include cross-service internal links in Output B

---

## Example

**Input:**
- Topic: Scuba Diving
- Seed Keywords: diving courses, liveaboard Red Sea
- Location: Egypt/Hurghada
- Language: English
- Business Type: Local dive center with liveaboard operations
- Audience: Beginner divers, tourist families, adventure travelers booking liveaboards
- Competitors: redsea-diving.com, divehurghada.com
- Services (priority order): 1. Open Water Course, 2. Liveaboard Red Sea, 3. Snorkeling Trip

---

**Example Output A — Service 1:**

```
---
### 🟦 Service 1: Open Water Course
- Priority: 1 of 3
- Pillar Keyword: Open Water Course Hurghada
- Suggested Page Type: Sub-Service Page
- Suggested URL Slug: /open-water-course-hurghada
---

| Keyword                          | Cluster         | Intent        | Vol.      | Weighted | Page Type        |
|----------------------------------|-----------------|---------------|-----------|----------|------------------|
| Open Water Course Hurghada       | OWD Booking     | Transactional | High      | 5        | Sub-Service Page |
| Book PADI Open Water Egypt       | OWD Booking     | Transactional | Medium    | 5        | Sub-Service Page |
| PADI Open Water cost Hurghada    | OWD Booking     | Transactional | Medium    | 5        | Sub-Service Page |
| best dive center PADI Hurghada   | OWD Research    | Commercial    | High      | 4        | Sub-Service Page |
| Open Water vs Discover Scuba     | OWD Research    | Commercial    | Medium    | 4        | Blog Post        |
| how long does PADI Open Water take | OWD Info     | Informational | Medium    | 3        | Blog Post        |
```

---

**Example Output B — Service 1, Cluster:**

```
## 🟦 Service 1: Open Water Course

### Cluster: OWD Booking
- Pillar Keyword: Open Water Course Hurghada
- Intent: Transactional
- Page Type: Sub-Service Page
- Suggested URL Slug: /open-water-course-hurghada
- Supporting Keywords: book PADI Open Water Egypt, PADI Open Water cost Hurghada, enroll OWD Red Sea, open water diving package Hurghada
- Content Angle: Targets first-time divers ready to get certified during their Hurghada vacation.
  Covers course structure, pool vs open water sessions, what's included, and certification validity worldwide.
  Primary CTA: "Book your PADI Open Water Course"
- Suggested Internal Links: /liveaboard-red-sea (cross-service), /snorkeling-hurghada (cross-service), /dive-center-hurghada
```

---

## Reference Files

- `references/intent-patterns.md` — Detailed keyword patterns per intent type and funnel stage
- `references/industry-modifiers.md` — Industry-specific modifier lists (SaaS, e-commerce, local, health, legal, finance)

Read these only when you need additional pattern examples for niche industries or complex intent classification edge cases.
