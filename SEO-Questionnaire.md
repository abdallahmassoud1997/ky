---
name: seo-questionnaire
description: Generates a client-ready SEO onboarding questionnaire (.xlsx with dropdowns) from just a website URL and business niche (optionally a target country). Use this skill whenever the user mentions "SEO questionnaire". Always trigger this for diving or real estate clients specifically, since dedicated reference question sets exist for those niches — but also trigger for any other industry, since the skill generates concise industry-specific questions on the fly using SEO best practices.
---

# SEO Client Questionnaire Generator

Generates a two-section SEO onboarding questionnaire as a polished `.xlsx` file (dropdowns for multiple-choice questions, matching the style of the reference forms this skill was built from).

## Required inputs from the user

Only two things are strictly required:
1. **Website URL / domain**
2. **Business niche / industry**

Optional:
3. **Target country** (prefills the Country field; otherwise the client fills it in themselves)
4. **Client / company name** (used in the questionnaire title if provided)

If the user gives just a URL and niche (e.g., "Make me a questionnaire for hurghadadivecenter.com, diving business"), proceed immediately — do not ask unnecessary clarifying questions. Only ask if the niche is truly ambiguous (e.g., "services" — services for whom?).

## Workflow

### 1. Always load the general section
Read `references/general_questions.json`. This is Section 1 for every questionnaire, regardless of niche. It already excludes anything that would duplicate a niche-specific reference (company name, website URL, country, contact info, competitor questions, basic audience questions, current-SEO-status questions, technical/CMS access). Never re-add these inside a niche section — that duplication is intentionally avoided.

### 2. Determine the niche category
Classify the user's stated niche into one of three buckets:
- **Diving** — dive centers, liveaboards, diving/snorkeling operators, dive course providers.
- **Real estate** — developers, brokerages/agencies, property management, property portals.
- **Other** — everything else.

### 3a. Diving or Real Estate → use the reference file exactly
- Diving → `references/diving_questions.json`
- Real estate → `references/real_estate_questions.json`

Use these questions as-is for Section 2. Do not invent additional niche questions on top of the reference — it's already scoped to be comprehensive but not excessive. If the user's context suggests a genuinely missing angle for their specific case, you may add at most 1–2 extra questions, but default to using the reference unmodified.

### 3b. Any other niche → generate concise niche-specific questions
Write 6–9 questions covering (pick what's relevant, skip what isn't — don't force all of these):
- Core products/services offered
- What makes them different from competitors (USP) — but only if not already covered by the general competitor questions
- Typical customer journey / how customers usually find or book them
- Service area / delivery model (local, national, online, in-person)
- Seasonality or booking patterns, if relevant to the industry
- Licenses, certifications, or compliance requirements typical of the industry
- Pricing model or packages structure
- Any industry-specific content types worth highlighting (portfolios, case studies, menus, listings, etc.)

Keep it to a tight, high-signal list — the goal is useful onboarding info, not an exhaustive survey. Use `type: "dropdown"` with 3–5 concrete options wherever a question has a natural closed set of answers (Yes/No/Not Sure, size ranges, B2B/B2C/Both, etc.); use `type: "text"` for open-ended questions. Follow the exact JSON schema below.

### 4. Assemble the config and build the file
Write a config JSON combining the general section + chosen niche section, e.g.:

```json
{
  "client_name": "Optional Client Name",
  "website": "https://example.com",
  "country": "Egypt",
  "sections": [
    {"section_title": "SECTION 1: GENERAL SEO & BUSINESS QUESTIONS", "questions": [ ...from general_questions.json... ]},
    {"section_title": "SECTION 2: <NICHE> INDUSTRY QUESTIONS", "questions": [ ...from reference or generated... ]}
  ]
}
```

Save this config to a temp file, then run:

```bash
python3 scripts/build_questionnaire.py config.json /mnt/user-data/outputs/<client-or-niche>_seo_questionnaire.xlsx
```

Requires `openpyxl` (`pip install openpyxl --break-system-packages` if not already available).

### 5. Present the file
Use `present_files` to share the resulting `.xlsx`. Briefly note in 1-2 sentences which niche path was used (reference vs. generated) — no need for a long explanation.

## Question schema reference

```json
{"label": "Question text", "type": "text"}
{"label": "Question text", "type": "dropdown", "options": ["Option A", "Option B", "Option C"]}
{"label": "Website URL", "type": "text", "prefill_key": "website"}
{"label": "Country / Target Market", "type": "text", "prefill_key": "country"}
```

Only the Website URL and Country questions in the general section use `prefill_key` — leave it off for everything else.

## Notes on design intent
- The output favors **breadth of coverage without bloat**: General section is ~15 questions, each niche section is under 16 questions. If a request seems to call for far more than this, keep the file to the sizes above rather than expanding — depth comes from later client conversations, not this intake form.
- The general section intentionally excludes contact details (name/email/phone), keyword guesses, existing-content status, and website/CMS access questions — these were removed as low-value for the initial questionnaire stage.
- Dropdowns exist so a client can fill this out in under 10 minutes without typing long answers for closed-ended fields.
- If asked to update/regenerate a previously generated questionnaire (e.g., new niche for existing client), treat it as a fresh run of this workflow rather than trying to edit the old file in place, unless the user explicitly wants to edit an existing file in `/mnt/user-data/uploads`.
