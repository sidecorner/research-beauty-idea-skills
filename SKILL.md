---
name: research-beauty-idea
description: >
  Research and surface niche opportunity ideas for women's beauty apps and web services.
  Use this skill whenever you want to identify underserved user needs, pain points, or
  trending topics in the beauty, skincare, haircare, or makeup space. Mines Reddit beauty
  communities, Hacker News, and Qiita for real user frustrations and developer insights.
  Outputs a structured report scoring each idea on feasibility, development time, profitability,
  competitive advantage, and small-team suitability.

  ALWAYS trigger this skill when the user mentions: beauty app ideas, skincare service gaps,
  makeup tool opportunities, beauty industry research, women's wellness product ideas, cosmetics
  startup research, or any request to "find beauty ideas from Reddit/HN/Qiita". Also trigger for
  broader requests like "find a niche product idea" or "research underserved markets" when
  the context involves beauty, skincare, or personal care for women.
---

# Beauty Idea Research Skill

You help product creators, indie hackers, and entrepreneurs discover validated, niche app or web
service ideas for women's beauty needs. You do this by systematically mining Reddit beauty
communities, Hacker News, and Qiita for real user pain points, then scoring each idea so the
user can quickly prioritize what to build.

## Step 1: Confirm the Target Year

**Ask the user in Japanese before doing anything else:**

> 調査対象の年号を教えてください（例：2025年）。未入力の場合は現在の年（{CURRENT_YEAR}）を使用します。

If the user skips or types "skip" / enters nothing meaningful, use the current calendar year.
Save this as `TARGET_YEAR`.

**Date range logic (apply to all data sources):**

- If `TARGET_YEAR` == current year (year not yet complete) → search the **past 12 months from today**
  - Example: Running in March 2026 with `TARGET_YEAR=2026` → search 2025-03 to 2026-03
- If `TARGET_YEAR` < current year (full year has passed) → search **Jan 1 to Dec 31** of that year

## Step 2: Gather Data

Run all three sources in parallel.

### 2a. Reddit — Beauty Community Pain Points

Use `scripts/fetch_reddit.py` to scrape posts from the subreddits listed in
`references/beauty-subreddits.md`. Focus on:

- Posts with high comment counts (community engagement signal)
- Flairs like "Help", "Question", "Rant", "Advice Needed"
- Recurring themes across multiple subreddits (strong signal of unmet need)

```bash
python scripts/fetch_reddit.py --year TARGET_YEAR --output /tmp/reddit_raw.json
```

Parse the output and group posts by theme (e.g., "finding shade match", "ingredient confusion",
"product overwhelm", "routine for X condition").

### 2b. Hacker News — Tech-Forward Beauty Discussions

Use `scripts/fetch_hn.py` to query the Algolia HN Search API for beauty-related threads.
Focus on posts with 10+ points or 5+ comments. See `references/hn-search-guide.md` for
recommended query terms.

```bash
python scripts/fetch_hn.py --year TARGET_YEAR --output /tmp/hn_raw.json
```

Look for: Show HN posts about beauty tech, Ask HN about personal care problems, funded startups
being discussed, and threads lamenting what beauty software still can't do.

### 2c. Qiita — Japanese Developer Perspective

Use `scripts/fetch_qiita.py` to search Qiita for Japanese beauty-tech articles.
This surfaces Japanese market-specific pain points and developer activity invisible in English sources.
Requires `QIITA_TOKEN` in `.env`. See `references/qiita-search-guide.md` for query terms.

```bash
python scripts/fetch_qiita.py --year TARGET_YEAR --output /tmp/qiita_raw.json
```

Look for: articles describing beauty tools built by Japanese developers, discussions of Japanese
beauty API/dataset availability, and UX problems in existing Japanese beauty apps.

## Step 3: Synthesize Ideas

From the raw data, extract 5–10 **specific, actionable product ideas**. A good idea:

- Addresses a **repeatedly mentioned** frustration (not a one-off complaint)
- Has a clear user action (find, track, compare, learn, book, etc.)
- Can be scoped to a small team (see `references/scoring-rubric.md`)

For each idea, write:
- **Title**: Short product concept name
- **Problem**: What pain it solves (quote real user language where possible)
- **Solution concept**: What the app/service does
- **Evidence**: Number/examples of Reddit posts + HN threads + Qiita articles mentioning this pain

Cross-platform signal (Reddit + HN + Qiita) is the strongest validation. Ideas appearing in
all three sources — especially with both English and Japanese interest — are strong candidates
for Japan-market-focused apps.

## Step 4: Score Each Idea

Apply the 5-dimension scoring from `references/scoring-rubric.md` to each idea.
Be honest — a score of 3 is not a failure, it's useful calibration.

## Step 5: Save the Report

Save the report to:

```
reports/{TARGET_YEAR}/{YYYY-MM-DD}/{HH-MM-SS}.md
```

Use the template in `references/report-template.md`.

After saving, tell the user the file path so they can find it easily.

## Notes on quality

- Prefer ideas with evidence from **multiple sources** — cross-platform signal is stronger.
- Ideas with both English (Reddit/HN) and Japanese (Qiita) signal are especially strong for Japan-focused products.
- Flag ideas that overlap with well-funded startups (competitive risk).
- When you quote user posts, paraphrase to avoid privacy concerns.
- If fetch scripts fail or return sparse data, note it in the report and suggest manual follow-up
  subreddits or HN/Qiita queries from the reference files.
- QIITA_TOKEN is read from `.env` automatically by `fetch_qiita.py`. If missing, the script
  still works but is rate-limited to 60 requests/hour.
