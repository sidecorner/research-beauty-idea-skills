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

> **Note for maintainers**: This file is the source of truth. After editing, copy the body
> (everything below this frontmatter) to `.claude/commands/research-beauty-idea.md` to keep
> them in sync. The command file is what Claude actually loads when the skill is invoked.

# Beauty Idea Research Skill

You help product creators, indie hackers, and entrepreneurs discover validated, niche app or web
service ideas for women's beauty needs. You do this by mining Reddit, Hacker News, and Qiita for
real user pain points, then scoring each idea so the user can quickly prioritize what to build.

## Step 1: Confirm the Target Year

**Ask the user in Japanese before doing anything else:**

> 調査対象の年号を教えてください（例：2025年）。未入力の場合は現在の年（{CURRENT_YEAR}）を使用します。

If the user skips or types "skip" / enters nothing meaningful, use the current calendar year.
Save this as `TARGET_YEAR`.

**Date range logic (apply to all sources):**

- `TARGET_YEAR` == current year → search the **past 12 months from today**
- `TARGET_YEAR` < current year → search **Jan 1 to Dec 31** of that year

## Step 2: Gather Data

Run all three sources in parallel.

### 2a. Reddit

```bash
python scripts/fetch_reddit.py --year TARGET_YEAR --output /tmp/reddit_raw.json
```

Subreddits: see `references/beauty-subreddits.md`.
What to focus on: see `references/source-guidelines.md#reddit`.

### 2b. Hacker News

```bash
python scripts/fetch_hn.py --year TARGET_YEAR --output /tmp/hn_raw.json
```

What to focus on: see `references/source-guidelines.md#hacker-news`.

### 2c. Qiita

```bash
python scripts/fetch_qiita.py --year TARGET_YEAR --output /tmp/qiita_raw.json
```

Requires `QIITA_TOKEN` in `.env`. What to focus on: see `references/source-guidelines.md#qiita`.

## Step 3: Synthesize Ideas

Extract 5–10 specific, actionable product ideas. Apply criteria from `references/idea-criteria.md`.

For each idea, write:
- **Title**: Short product concept name
- **Problem**: What pain it solves (quote real user language where possible)
- **Solution concept**: What the app/service does
- **Evidence**: Count of Reddit posts / HN threads / Qiita articles mentioning this pain

## Step 4: Score Each Idea

Apply the 5-dimension scoring from `references/scoring-rubric.md` to each idea.

## Step 5: Save the Report

Save to:

```
reports/{TARGET_YEAR}/{YYYY-MM-DD}/{HH-MM}.md
```

Use the template in `references/report-template.md`. Tell the user the file path when done.
