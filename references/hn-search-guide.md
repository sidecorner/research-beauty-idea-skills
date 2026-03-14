# Hacker News Search Guide

## Why HN for beauty idea research?

Hacker News skews technical/entrepreneurial, so beauty discussions there tend to surface:
- Startups raising money in the beauty/wellness space (what VCs are betting on)
- Developers building beauty tools (what's technically possible + what's missing)
- "Ask HN" posts about problems they want solved (direct demand signal)
- "Show HN" posts from builders who tried to solve a beauty problem
- Critical discussions of existing beauty apps (what they're failing at)

This is complementary to Reddit: Reddit gives you the *user* pain, HN gives you the *builder/market* perspective.

---

## Recommended search queries for `fetch_hn.py`

### Direct beauty tech queries
```
skincare app
beauty technology
cosmetics personalization
skin analysis AI
haircare app
makeup recommendation
beauty subscription box
ingredient checker beauty
beauty AI
dermatology app
```

### Adjacent / broader signals
```
personal care startup
wellness app women
skincare routine tracker
beauty ecommerce personalization
cosmetics formulation tool
shade matching technology
```

### Market/investment angle
```
beauty industry software
D2C beauty
beauty brand tech
skincare SaaS
```

---

## Manual HN search tips

If the API returns sparse results, supplement with these manual searches:

1. **Algolia search**: `https://hn.algolia.com/?q=skincare+app&dateRange=pastYear`
2. **Google site search**: `site:news.ycombinator.com "skincare" after:2024`
3. **Ask HN threads**: Search for `Ask HN: skincare` or `Ask HN: beauty`

---

## What to look for in HN threads

### High-value patterns

| Pattern | Example | What it signals |
|---------|---------|-----------------|
| Show HN with low traction | "Show HN: Skin routine tracker" (3 pts) | Attempted but not yet solved |
| Ask HN demand | "Ask HN: Why is there no good X app?" | Validated unmet need |
| Funded startup discussion | "Prose raises $15M for hair care" | Confirmed market, look for gaps |
| Critical review thread | "Curology is overpriced because..." | Specific pain points in funded products |
| Technical breakthrough | "GPT-4 for skin tone matching" | Enabling tech becoming available |

### Red flags (over-crowded)

- Multiple well-funded startups already solving this
- Big beauty brands (L'Oreal, Estée Lauder) already announced similar product
- Multiple "Show HN" posts with high traction on the same idea

---

## Combining with Reddit data

Strong idea candidates appear in **both** sources:

- Reddit: "I wish there was an app that tracks how my skin changes with my cycle"
- HN: "Ask HN: Has anyone built period-skin correlation tracking?"

Cross-platform signal = validated pain point + confirmed interest from builders.
