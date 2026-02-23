# Content Inspiration Watchlist

Scrape these profiles ONE AT A TIME to avoid session expiration.

---

## Individual Thought Leaders

Use `get_person_posts` for these profiles. Use `get_person_profile` if you need bio/background context.

| Username | Name / Focus | What to Watch |
|---|---|---|
| noelleai | Noelle Russell — AI leadership, responsible AI | Enterprise AI adoption, ethical AI framing, executive-level tone |
| danielsolove | Daniel Solove — Privacy law & AI | AI governance, privacy regulation, legal perspective on AI |
| lexfridman | Lex Fridman — AI researcher & podcaster | Deep technical AI conversations, interview-driven insights, audience engagement |
| alliekmiller | Allie K. Miller — AI strategy & investing | AI business strategy, startup ecosystem, enterprise adoption trends |
| emollick | Ethan Mollick — AI + business/education | AI research translation, practical AI frameworks, management-AI intersection |
| satyanadella | Satya Nadella — Microsoft CEO | Enterprise AI strategy, Copilot positioning, big-tech AI narrative |
| luizajarovsky | Luiza Jarovsky — AI & data privacy | AI regulation, digital ethics, consumer-facing AI risks |
| conorgrennan | Conor Grennan — AI in education/business | AI training for non-technical audiences, generative AI workshops |
| azhar | Azeem Azhar — Exponential View | Macro AI trends, geopolitics of AI, economic impact framing |
| boxaaron | Aaron Levie — Box CEO | Enterprise AI adoption, SaaS-AI intersection, witty tech takes |

---

## Companies

Use `get_company_posts` for these profiles. Use `get_company_profile` if you need company background.

| Company Slug | Company | What to Watch |
|---|---|---|
| the-future-of-privacy-forum | Future of Privacy Forum | AI governance, privacy frameworks, regulatory trends |
| a16z | Andreessen Horowitz (a16z) | AI investment theses, market narratives, startup ecosystem |

---

## How to Use This Watchlist

### Auto-Scraping Pipeline

When asked to scrape the watchlist, iterate through ALL profiles automatically:

1. **Phase 1 — Scrape:** Loop through every profile above (one at a time). Use `get_person_posts` for individuals, `get_company_posts` for companies. Collect findings in memory.
2. **Phase 2 — Analyze:** Compile all scraped data into ONE research file: `research/YYYY-MM-DD-watchlist-analysis.md`. Identify top content, trending topics, engagement patterns, and content gaps.
3. **Phase 3 — Draft:** Write posts inspired by the best content found, but in Grey AI's voice. Save each to `drafts/`.

If the scraper fails, follow the Scraper Failure Protocol in `CLAUDE.md`.

### Analysis Prompts

When analyzing scraped profiles, answer these questions:

1. What topics are they posting about this week/month?
2. What post format are they using? (list, story, hot take, data, question)
3. What's getting the most engagement (likes, comments, reposts)?
4. What's their angle/positioning — how do they frame AI?
5. Where is there a gap that Grey AI can fill with our voice?
6. What specific post could we create inspired by this — but sharper, more analytical, more structured?

### Drafting From Research

When creating a post inspired by watchlist profiles:

- Based on [username]'s recent post about [topic]:
  - Their angle: [what they said]
  - Our angle: [how Grey AI would reframe this — more analytical, timeline-driven, specific]
  - Format: [Pattern Interrupt / Micro-Lesson / Relatable Rant / Case Study]
  - Pillar: [which content pillar this maps to]
