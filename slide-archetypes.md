# Slide archetypes — prompt scaffolds and layout notes

One section per archetype from the **Zendesk AI Slides** theme. Each includes:
- **When to use it** — the intent this slide serves
- **Layout** — what's on the slide and where
- **Eyebrow** — what to put in it
- **Imagery rule** — restated inline because the model will skip it otherwise
- **Copy constraints** — headline and body rules specific to this slide type
- **Prompt scaffold** — paste-and-fill prompt for AI drafting
- **On-brand example** — a worked example using the standard draft block

> **Read this with `zendesk-slides-skill.md`.** The main skill defines the preflight, the archetype set, the copy rules, and the imagery decision rule. This file is the per-archetype reference. It restates the bits that are most often skipped, in the place where they're most often skipped.

## Two rules that apply to every archetype below

These are repeated inline in each archetype because models drop them when the rule lives in a separate section. Read them once here, then expect to see them again.

**Eyebrow rule.** Every archetype below carries the theme's eyebrow pill in the top-left **except Closing** (which is wordmark-only on black). The number ties to the section, not the slide index. The label is identical across every slide in a section; don't paraphrase between slides. Format: `NN · Section label`.

**Imagery rule.** For every image region, decide in this order:
1. **REUSE** an existing image already in the deck (from the inventory you took during preflight). Output the image filename from the inventory.
2. **PLACEHOLDER** if no existing image fits. Output `[placeholder: subject, mood]`.
3. **Never generate.** No image-generation tool calls, no base64, no SVG substitutes for photography.

## Standard draft block — use for every slide

Match the format defined in the main skill. Fields beyond Eyebrow / Headline / Subline / Body / Image / Speaker / Quote attribution don't appear in the output.

```
**Slide [N]: [Archetype] ([parameters])**

Eyebrow: [NN] · [SECTION LABEL]
Headline: [headline text]
Subline: [subline text, if applicable]
Body: [body text or column content]
Image: [image filename from inventory OR placeholder description]
Speaker: [name, title, company — Cover only]
Quote attribution: [name, title, company — Quote only]
```

After showing the draft, ask whether the structure works or needs adjustment.

---

## 1. Cover

**When to use it**
The first slide of any deck. Sets the tone and introduces the topic. Two parameter modes:
- `speaker: yes` — conference talks, webinars, anywhere there's a presenter on stage. Includes speaker photo, name, title.
- `speaker: no` — decks sent without a presenter (leave-behinds, async sharing).

**Layout**
- Top-left: eyebrow pill
- Headline area: H1, conversational
- Right or full-bleed: hero photography
- Speaker block (when `speaker: yes`): name, title, optional avatar
- Confidentiality footer is master — don't touch it

**Eyebrow:** Yes. Typically `01 · Overview` or the deck's opening section name.

**Imagery rule:** REUSE first, then PLACEHOLDER, never generate. Cover photography sets the deck's visual tone — flag the choice during preflight if the inventory has multiple candidates.

**Copy constraints**
- Headline: ≤ 6 words, sentence case, no period (per main skill)
- Subline (optional): one supporting line
- Speaker block: Name on one line, Title (and company if external) on the next

**Prompt scaffold**
```
Draft a cover slide for a deck about [TOPIC] presented to [AUDIENCE].
- Mode: [speaker: yes | speaker: no]
- Eyebrow: confirm section number and label from preflight.
- Headline: ≤ 6 words, sentence case, no period.
- Subline (optional): one supporting line.
- Speaker block (if speaker: yes): Name, Title, Company.
- Imagery: check the existing deck inventory first. If a cover-suitable image
  exists, reuse it. Otherwise insert a placeholder describing the photo mood.
```

**Example**
```
**Slide 1: Cover (speaker: yes)**

Eyebrow: 01 · Overview
Headline: Hi, meet Zendesk AI
Subline: A quick tour of what's new this year
Image: [placeholder: confident professional in natural light, holding laptop, warm and forward-looking mood]
Speaker: Jane Doe, Director of Customer Experience, Zendesk
```

---

## 2. Agenda

**When to use it**
Deck roadmap. Lists major sections, optionally with a one-line subline per row. Use early — slide 2 or 3.

**Stop-and-ask:** For short decks (< 8 slides), confirm with the user whether an agenda is wanted before drafting one.

**Layout**
- Top-left: eyebrow pill
- Headline area: "Agenda" or a custom title
- 3–8 rows, each with section name and optional subline
- Numbers right-aligned, items left-aligned

**Eyebrow:** Yes. Section number + label from preflight (the eyebrow numbering is independent of the agenda's row numbers).

**Imagery rule:** No imagery on this slide.

**Copy constraints**
- 3–8 rows (template constraint)
- Each row name: 2–5 words, sentence case, no period
- Optional subline per row: ≤ 8 words

**Prompt scaffold**
```
Draft an agenda slide for a [DECK TYPE] presented to [AUDIENCE].
- Eyebrow: confirm section number and label from preflight.
- 3–8 rows, each 2–5 words, sentence case.
- Optional subline per row, ≤ 8 words.
- If the deck is short (< 8 slides), ask the user whether an agenda is wanted
  before drafting.
```

**Example**
```
**Slide 2: Agenda (rows: 5)**

Eyebrow: 01 · Overview
Headline: Today's agenda
Body:
  01 — Why this matters now
  02 — What we're building
  03 — How it works
  04 — Customer results
  05 — What's next
```

---

## 3. Section divider

**When to use it**
Chapter break between major sections. Re-orients the audience. Two parameter modes:
- `body: no` — section name alone. Use when the name is self-explanatory.
- `body: yes` — section name plus a contextualizing line. Use when the name is cryptic or sets up something specific.

**Layout**
- Top-left: eyebrow pill (this is the slide that announces the section the eyebrow refers to)
- Large H1: section name
- Optional body line below (when `body: yes`)

**Eyebrow:** Yes. The eyebrow on this slide opens its section — its number and label match the section being introduced. The headline typically matches the eyebrow label exactly (eyebrow `02 · Product` → headline `Product`).

**Imagery rule:** No imagery on this slide.

**Copy constraints**
- Headline: ≤ 4 words, sentence case, no period
- Body (if `body: yes`): one sentence, ≤ 15 words, ends with period (per main skill — body text gets periods)

**Prompt scaffold**
```
Draft a section divider for the "[SECTION NAME]" section of a deck on [TOPIC].
- Mode: [body: yes | body: no]
- Eyebrow: this slide opens the section — number and label match the
  section being introduced.
- Headline: section name only, ≤ 4 words. Match the eyebrow label by default.
- Body (if body: yes): one sentence, ≤ 15 words, terminal period.
```

**Example**
```
**Slide 6: Section divider (body: yes)**

Eyebrow: 02 · Product overview
Headline: Product overview
Body: How Zendesk AI handles tickets, conversations, and knowledge in one place.
```

---

## 4. Statement

**When to use it**
A single, memorable sentence that carries the whole deck's message — mission statement, core principle, turning-point moment. Use sparingly: one or two per deck maximum.

**Layout**
- Top-left: eyebrow pill (yes — Statement carries the eyebrow)
- Centered: large bold declarative sentence
- No body, no supporting text

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** No imagery on this slide. The slide is the sentence.

**Copy constraints**
- One sentence only. Period at the end is acceptable — it's a full sentence, not a headline.
- Active voice, declarative tone.
- ≤ 12 words ideal, 16 max.

**Prompt scaffold**
```
Draft a statement slide for [DECK TOPIC].
- Eyebrow: confirm section number and label from preflight.
- One declarative sentence, ≤ 12 words, active voice, terminal period acceptable.
- No body, no supporting text — the sentence is the slide.
```

**Example**
```
**Slide 12: Statement**

Eyebrow: 04 · What we believe
Headline: Every conversation should feel like it was made for you.
```

---

## 5. Quote

**When to use it**
Customer quotes, exec quotes, testimonials, research pull-quotes.

**Layout**
- Top-left: eyebrow pill
- Left: portrait photo
- Right: quote text with attribution below (Name, Title, Company)

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** REUSE first, then PLACEHOLDER, never generate. **Never invent the speaker or fabricate the quote.** If the quote isn't provided, propose drafted options and flag them for human review — don't pass drafted quotes off as real.

**Copy constraints**
- Quote: use curly quotes (" "), not straight quotes
- ≤ 20 words for the quote
- Attribution format: Name, Title, Company

**Prompt scaffold**
```
Draft a quote slide.
- Eyebrow: confirm section number and label from preflight.
- Speaker: [NAME, TITLE, COMPANY]
- Source context: [where the quote came from / what it's about]
- Quote: ≤ 20 words, in the speaker's voice. Use curly quotes.
- If the quote isn't provided, propose 2–3 quote options and flag them as
  DRAFTED (not verbatim) for human review.
- Imagery: check the existing deck inventory first for a portrait. If a
  suitable image exists, reuse it. Otherwise insert a placeholder.
```

**Example**
```
**Slide 8: Quote**

Eyebrow: 03 · Customer story
Body: "Zendesk AI cut our resolution time in half without making our agents feel replaced."
Image: [placeholder: mid-shot portrait of a customer success leader in warm natural light, relaxed and authentic]
Quote attribution: Maria Chen, VP of Support, Acme Corp
```

---

## 6. Content

**When to use it**
Flexible information layout — the workhorse archetype. Parameters:
- `columns: 1` — narrative or single idea with supporting visual.
- `columns: 2` — parallel ideas, before/after, compare/contrast.
- `columns: 3` — three features, three steps, rule-of-three patterns.
- `columns: 4` or `columns: 5` — feature lists, comparison tables, denser process steps.
- `media: image` — hero image above or beside columns.
- `media: icon` — icons paired with column headers.
- `media: none` — text only.

**Layout**
- Top-left: eyebrow pill
- Headline + optional subline at top
- Columnar body below, layout depends on `columns` and `media`

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** REUSE first, then PLACEHOLDER, never generate. With multiple images (e.g., `columns: 3, media: image`), apply the rule to each image independently — fine to reuse one and placeholder another.

**Copy constraints**
- Headline: ≤ 6 words, sentence case, no period
- Subline (optional): one line, ≤ 12 words, no period
- Each column body: full sentences, terminal periods, ≤ 25 words per column for `columns: 3+`, ≤ 30 words for `columns: 1` or `columns: 2`
- All columns must be parallel in structure (all verbs, all noun phrases, etc.)
- Don't pad: if `columns: 4` but only three items exist, use `columns: 3`

**Prompt scaffold**
```
Draft a Content slide on [TOPIC].
- Mode: columns: [1/2/3/4/5], media: [image/icon/none]
- Eyebrow: confirm section number and label from preflight.
- Headline: ≤ 6 words, sentence case, no period.
- Subline (optional): one line, ≤ 12 words.
- Columns: parallel structure across all columns. Each ≤ 25 words for 3+
  columns, ≤ 30 words for 1–2 columns. Terminal periods on body sentences.
- Imagery (if media: image): for each image, check the inventory first; reuse
  if possible, otherwise placeholder.
- If the source material doesn't fill the chosen column count, drop a column
  rather than padding.
```

**Example**
```
**Slide 5: Content (columns: 3, media: none)**

Eyebrow: 02 · Product overview
Headline: Built for teams that scale
Subline: Zendesk grows with your business, from startup to enterprise
Body:
  - Flexible pricing: Pay for what you use, upgrade anytime.
  - Seamless integrations: Connect to Slack, Salesforce, Jira, and 1,000+ apps.
  - Enterprise security: SOC 2, GDPR, HIPAA compliant out of the box.
```

---

## 7. Product plate

**When to use it**
Showing a Zendesk product UI in detail — demos, feature deep-dives, "see it in action" moments.

**Layout**
- Top-left: eyebrow pill
- Left column: headline at top, body text at bottom
- Right column: product screenshot

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** REUSE first, then PLACEHOLDER, never generate. Product screenshots especially benefit from reuse — if an earlier slide introduced a workspace view, a later slide referencing the same view should reuse the exact screenshot.

**Copy constraints**
- Headline: ≤ 6 words, sentence case, no period
- Body: full sentences with terminal periods, ≤ 40 words total
- Don't add captions like "ADMIN WORKSPACE" — the screenshot speaks for itself

**Prompt scaffold**
```
Draft a Product plate slide featuring [PRODUCT AREA].
- Eyebrow: confirm section number and label from preflight.
- Headline: ≤ 6 words describing what the screenshot demonstrates.
- Body: full sentences, ≤ 40 words, terminal periods.
- Imagery: check inventory first for an existing screenshot of this area.
  If found, reuse it. Otherwise placeholder describing the workspace view
  to be captured.
```

**Example**
```
**Slide 9: Product plate**

Eyebrow: 02 · Product overview
Headline: Resolve tickets faster
Body: Agents see AI-generated summaries, suggested replies, and customer history in one view. No tab-switching, no copy-paste.
Image: [placeholder: Agent Workspace screenshot showing AI ticket summary panel and suggested replies]
```

---

## 8. Data display

**When to use it**
Grid of metric callouts — dashboards, ROI summaries, impact reports. Parameter:
- `type: callouts` — the only supported type. Up to 6 callouts per slide.

**Gap note:** The template does not support chart, map, or pricing-table data displays. If the user asks for these, suggest the callout grid or ask whether they'll provide a custom image.

**Layout**
- Top-left: eyebrow pill
- Headline + optional subline at top
- Grid of up to 6 callouts: each is a large number with a subline

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** No imagery on this slide.

**Copy constraints**
- Headline: ≤ 6 words, sentence case, no period
- Each callout number: a single value (percentage, dollar amount, count). Don't combine multiple numbers in one callout.
- Each callout subline: ≤ 8 words explaining the number, terminal period
- **Never invent statistics.** If the data isn't provided, stop and ask.

**Prompt scaffold**
```
Draft a Data display slide showing [METRICS] for [CONTEXT].
- Mode: type: callouts
- Eyebrow: confirm section number and label from preflight.
- Headline: ≤ 6 words.
- Up to 6 callouts. Each: one number + ≤ 8-word subline with terminal period.
- If specific metric values aren't provided, STOP and ask. Do not invent
  statistics.
```

**Example**
```
**Slide 14: Data display (type: callouts)**

Eyebrow: 03 · Customer results
Headline: Impact across the customer base
Body:
  - 47% — Faster average resolution time.
  - $2.3M — Annual savings per enterprise customer.
  - 89% — CSAT score across AI-handled tickets.
  - 12 weeks — Average time to full deployment.
```

---

## 9. Timeline

**When to use it**
Roadmaps, company history, release schedules — anything ordered along a temporal axis. Parameter:
- `milestones: 2–4` — horizontal timeline with this many points.

**Layout**
- Top-left: eyebrow pill
- Headline + optional subline at top
- Horizontal timeline with 2–4 milestones, each with year/date header and body text

**Eyebrow:** Yes. Section number + label.

**Imagery rule:** No imagery on this slide.

**Copy constraints**
- Headline: ≤ 6 words, sentence case, no period
- Each milestone header: date or year, consistent granularity across milestones (don't mix "2024" and "Q4 2024" — pick one)
- Each milestone body: ≤ 15 words, terminal period
- **Never invent dates or milestones.** If the data isn't provided, stop and ask.

**Prompt scaffold**
```
Draft a Timeline slide covering [PROJECT/ROADMAP] from [START] to [END].
- Eyebrow: confirm section number and label from preflight.
- Headline: ≤ 6 words.
- 2–4 milestones. Each: date/year header (consistent granularity) + ≤ 15-word
  body with terminal period.
- If milestone dates or names aren't provided, STOP and ask. Do not invent.
```

**Example**
```
**Slide 16: Timeline (milestones: 4)**

Eyebrow: 05 · What's next
Headline: The road ahead
Body:
  - 2024 — Launched Zendesk AI for ticket triage and summarization.
  - 2025 — Expanded to voice and proactive customer outreach.
  - 2026 — Released agentic workflows for autonomous resolution.
  - 2027 — Industry-specific AI models for regulated verticals.
```

---

## 10. Closing

**When to use it**
Final slide of the deck. Wordmark on black, no text, no CTA — pure brand presence.

**Stop-and-ask:** Some decks end with a CTA slide (contact details, next steps) instead of the wordmark. Before drafting, confirm whether the user wants the Closing archetype or a custom Content slide for the final slide.

**Layout**
- Black background
- Zendesk wordmark centered
- No eyebrow, no headline, no body

**Eyebrow:** No. Closing is the only archetype without an eyebrow.

**Imagery rule:** No imagery beyond the wordmark, which is part of the template.

**Copy constraints**
- No copy. The slide is the wordmark.

**Prompt scaffold**
```
Confirm the deck should end with a Closing slide (wordmark only) rather than
a custom CTA slide with contact details or next steps. If Closing is correct,
no further drafting is needed — the template handles it.
```

**Example**
```
**Slide 20: Closing**

(No eyebrow, no headline, no body — Zendesk wordmark on black, template-rendered.)
```

---

## Quick reference: which archetype for which intent?

| If you want to… | Use this archetype | Eyebrow? |
|---|---|---|
| Start the deck | Cover | Yes |
| Map the deck's structure | Agenda | Yes |
| Transition between sections | Section divider | Yes |
| Land one powerful sentence | Statement | Yes |
| Share a customer or exec voice | Quote | Yes |
| Explain ideas in 1–5 columns | Content | Yes |
| Show the product UI | Product plate | Yes |
| Present metrics as callouts | Data display | Yes |
| Show a roadmap with 2–4 milestones | Timeline | Yes |
| End the deck | Closing | **No** |
