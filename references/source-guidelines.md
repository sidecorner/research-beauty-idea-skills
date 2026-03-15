# Data Source Guidelines

What to focus on in each source, and how to interpret what you find.

---

## Reddit

See `beauty-subreddits.md` for the full subreddit list.

**Prioritize:**
- Posts with high comment counts (engagement signal)
- Flairs: "Help", "Question", "Rant", "Advice Needed", "Advice Wanted"
- Recurring themes across multiple subreddits (independent co-occurrence = strong signal)

**Strongest subreddits for underserved-needs signal:**
- r/30PlusSkinCare, r/NaturalHair, r/EczemaSupport — most beauty tech ignores these demographics
- r/Hairloss — large female user base with minimal dedicated tooling

**Grouping themes:** Cluster posts into named pain areas, e.g.:
- "finding shade match", "ingredient confusion", "product overwhelm", "routine for X condition"

---

## Hacker News

Use the Algolia HN Search API (`scripts/fetch_hn.py`). Filter: 10+ points or 5+ comments.

**High-signal post types:**
- `Show HN:` — developers who already tried to build something in this space
- `Ask HN:` — unmet personal care problems that reached a technical audience
- Discussion of funded beauty-tech startups (signals investor appetite)
- Threads lamenting what beauty software "still can't do"

**What HN uniquely reveals:**
- Whether developers see a technical angle worth building
- Whether there's B2B or API/data infrastructure missing from the ecosystem

---

## Qiita

Japanese developer platform. Use `scripts/fetch_qiita.py` (requires `QIITA_TOKEN` in `.env`;
without token, rate-limited to 60 req/hour).

**High-signal content:**
- Articles describing beauty tools Japanese developers built themselves (strong demand signal)
- Discussions of Japanese beauty API / dataset availability (infrastructure gap = opportunity)
- UX problem posts about existing Japanese beauty apps

**What Qiita uniquely reveals:**
- Japan-market-specific pain points invisible in English sources
- Whether the Japanese developer community sees this as a solved or unsolved problem
- Localization and regulatory nuances (e.g., quasi-drug labeling, Japanese ingredient naming)

---

## Trusted vs. Weak Sources

| Source type | Trust level | Notes |
|-------------|------------|-------|
| Recurring Reddit pain across 3+ subs | High | Independent co-occurrence is strong |
| HN Show HN with engagement | High | Someone already tried to build it |
| Qiita article with detailed UX critique | High | First-person developer + user perspective |
| Single Reddit post with many upvotes | Medium | May be viral, not structural |
| HN comment (not top-level post) | Medium | Useful context, not primary signal |
| Single Qiita article, low views | Low | Niche, verify against other sources |
| Press release / brand blog | Not used | Marketing, not user pain |
