# CRED Product — Play Store 150K Review Analysis

**What question I was trying to answer:**
CRED has a 4.20 star rating on the Play Store. But when I tried to redeem my coins, the store prices were higher than Amazon — without any coins applied. I wanted to know if this was showing up in the data.

It was.

---

## The Core Finding

Reviews mentioning rewards average **2.48 stars** — against an overall app average of **4.20 stars**.

That is a 1.72 star gap sitting underneath a headline number that looks healthy.

59.8% of all rewards-related reviews are 1 or 2 stars. The word "cashback" appears 3,215 times across 1,50,000 reviews — a single removed feature, still being mentioned years later.

Every complaint theme — rewards, payments, support, performance — classified as a **structural problem**, not a version-specific bug. Complaints are spread evenly across 110 app versions spanning 3+ years. No release caused this. No patch will fix it.

---

## Dataset

| Field | Value |
|---|---|
| Source | Google Play Store (India) |
| App | CRED — com.dreamplug.androidapp |
| Total reviews scraped | 1,50,000 |
| Date range | Oct 2022 — Feb 2026 |
| App versions covered | 233 |
| Versions retained (100+ reviews) | 110 |
| Reviews in final analysis | 1,34,552 |

---

## What the Analysis Does

**Theme classification**
8 themes defined via keyword matching on review text — rewards_devaluation, customer_support, payment_issues, app_performance, ui_ux, loan_issues, trust_privacy, feature_request. Each review tagged to its first matching theme.

**Version-level complaint analysis**
For each theme, calculated what % of negative reviews came from the top 2 most-complained-about versions. Threshold: >60% = version-specific bug, <60% = structural product problem. Every theme came back structural (7–11% concentration).

**Pain index**
Combined two signals into a single priority score:
- 40% weight — complaint volume (review count)
- 60% weight — community validation (thumbs up count)

Both metrics normalised to 0–1 before weighting so scale differences don't distort the result.

**Pain index results:**

| Theme | Pain Index |
|---|---|
| rewards_devaluation | 1.000 |
| customer_support | 0.556 |
| payment_issues | 0.477 |
| app_performance | 0.194 |
| trust_privacy | 0.057 |
| feature_request | 0.025 |
| ui_ux | 0.021 |
| loan_issues | 0.000 |

**Full theme view (all reviews including positive)**

| Theme | All Reviews | Avg Rating | Total Thumbs Up |
|---|---|---|---|
| rewards_devaluation | 9,559 | 2.48 | 42,226 |
| payment_issues | 10,538 | 3.42 | 19,771 |
| customer_support | 5,396 | 2.00 | 15,743 |
| other (no complaint) | 1,01,840 | 4.68 | 2,767 |

The "other" category — users who don't mention any specific problem — averages 4.68. The dissatisfaction is not spread across the app. It is concentrated in users who engage with the rewards system.

---

## Key Numbers

| Metric | Value |
|---|---|
| Overall app rating | 4.20 ★ |
| Rewards theme avg rating | 2.48 ★ |
| Rating gap | 1.72 stars |
| % of rewards reviews that are negative | 59.8% |
| Cashback mentions across dataset | 3,215 |
| Total thumbs up on rewards complaints | 42,226 |
| Most upvoted single complaint | 2,603 thumbs up |

---

## Most Upvoted Complaints (Top 3)

**2,603 thumbs up — Sep 2025**
> "The support system in CRED is absolutely useless. When I go to the rewards section, the contact now option is given but after that, no option to report your issue is visible."

**1,017 thumbs up — Jul 2023**
> "Such a confusing app. Not able to find products, credit card payment options, products are less and expensive."

**715 thumbs up — Apr 2024**
> "The app provides a lot of offers and vouchers which are nothing but scam to make you use the app and then regret later. Even the payments of credit card is not rewarding anymore."

---

## Files in This Repo

```
Analysis.ipynb          — Full analysis notebook
cred_powerbi.csv        — Cleaned review data for Power BI
cred_pain_index.csv     — Pain index summary table
rewards_trend.png       — Monthly rewards complaint trend chart
README.md               — This file
```

---

## Tools Used

- Python 3.12
- google-play-scraper
- pandas
- matplotlib
- Power BI Desktop

---

## Methodology Notes

- Only English-language reviews included (lang='en', country='in')
- Versions with fewer than 100 reviews excluded to avoid small-sample noise
- Theme tagging uses first-match logic — a review matching multiple themes is tagged to the first one found
- Pain index weights (0.4 / 0.6) are a deliberate choice: thumbs up represents independent user confirmation, which is a stronger signal than raw complaint volume
- Structural vs bug classification threshold (60%) is based on the logic that 2 versions accounting for 60%+ of complaints in a 110-version dataset would represent a 33x concentration — a clear spike rather than normal variation

---

## Medium Article

Full writeup with context, findings, and recommendation:
[Link]

---

*Fresher project — built independently to demonstrate product thinking and data analysis for DA / BA / APM roles.*
*Open to feedback on methodology.*