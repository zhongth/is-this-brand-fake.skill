# Scoring Rubric

Defines signal ratings, weights, score calculations, and verdict thresholds for brand validation.

---

## Signal Ratings

Each investigation step produces one of four signal ratings:

| Rating | Meaning | Score Direction |
|--------|---------|-----------------|
| VERIFIED | Strong evidence of legitimacy | Positive (full weight) |
| SUSPICIOUS | Weak or mixed signals | Small positive |
| NOT_FOUND | Absence of evidence | Small negative |
| RED_FLAG | Strong evidence of deception | Negative (full weight) |

---

## Step Weights and Score Ranges

| Step | Weight | VERIFIED | SUSPICIOUS | NOT_FOUND | RED_FLAG |
|------|--------|----------|------------|-----------|----------|
| 2. Government & Regulatory | 20% | +20 | +8 | -5 | -20 |
| 3. Trademark Timeline | 15% | +15 | +5 | -10 | -15 |
| 4. Domain & Website | 10% | +10 | +3 | 0 | -10 |
| 5. Retail Channels | 15% | +15 | +6 | -8 | -15 |
| 6. Social & Professional | 10% | +10 | +3 | -5 | -10 |
| 7. Community & Media | 10% | +10 | +3 | -5 | -10 |
| 8. SEO Content Quality | 10% | +10 | +3 | 0 | -10 |
| 9. Chinese Entity Cross-Ref | 10% | +10 | +3 | 0 | -10 |

**Total range:** -100 to +100

---

## Signal Rating Criteria

### Step 2: Government & Regulatory

- **VERIFIED (+20):** Active business registration for 3+ years. Real office address confirmed on Google Maps. Product listed in regulatory database (TGA/FDA/PMDA). Directors are local nationals with verifiable identities.
- **SUSPICIOUS (+8):** Registration exists but is recent (<2 years). Virtual office address. Minimal filing history. Directors are non-local with no other local business ties.
- **NOT_FOUND (-5):** No business registration found in claimed country. Not in regulatory databases.
- **RED_FLAG (-20):** Registered address is fake (residential, vacant lot, car repair shop). Company is a shell (no employees, no filings). Registration by a known OEM/marketing company.

### Step 3: Trademark Timeline

- **VERIFIED (+15):** Trademark filed in origin country 2+ years before any Chinese filing. Continuous use evidence.
- **SUSPICIOUS (+5):** Filed in origin country within 1 year of Chinese filing. Or filed simultaneously.
- **NOT_FOUND (-10):** No trademark found in origin country IP database.
- **RED_FLAG (-15):** Chinese CNIPA filing predates origin country filing. Trademark acquired (transferred) rather than filed by the brand.

### Step 4: Domain & Website

- **VERIFIED (+10):** Domain registered 3+ years ago. Registrant is in origin country. Full multi-page English-language website with product details, about page, contact info, store locator. Wayback Machine shows consistent English content history.
- **SUSPICIOUS (+3):** Domain 1-2 years old. Mix of languages. Some depth but feels templated.
- **NOT_FOUND (0):** No domain found, or domain parked/expired. Neutral — some real brands don't have great websites.
- **RED_FLAG (-10):** Domain registered by Chinese entity or via Chinese registrar. Website is Chinese-only or thin English veneer over Chinese content. Domain registered very recently. Wayback Machine shows site appeared only after Chinese market push.

### Step 5: Retail Channels

- **VERIFIED (+15):** Products available in 2+ major local retailers in origin country (Chemist Warehouse, Walgreens, Boots, etc.). Reviews on these platforms spanning months/years.
- **SUSPICIOUS (+6):** Available on Amazon only. Or available in one small retailer. Reviews are sparse or recent.
- **NOT_FOUND (-8):** Zero presence in origin country retail. Not found on Amazon in origin country.
- **RED_FLAG (-15):** Only available on Chinese e-commerce platforms (Tmall Global, JD International, Kaola, Xiaohongshu). Products enter China via cross-border e-commerce (bonded warehouse) exclusively.

### Step 6: Social & Professional Footprint

- **VERIFIED (+10):** LinkedIn company page with 10+ employees from origin country showing real tenure (1+ years). Instagram/Facebook with organic engagement, diverse follower base. TikTok with original content.
- **SUSPICIOUS (+3):** LinkedIn exists but <5 employees. Social accounts exist but low engagement or mostly promotional.
- **NOT_FOUND (-5):** No LinkedIn company page. No social media accounts found.
- **RED_FLAG (-10):** LinkedIn page with 0 employees from origin country. Social media followers show fake patterns (sudden spikes, bot-like profiles). All engagement is from Chinese-language accounts.

### Step 7: Community & Media

- **VERIFIED (+10):** Organic Reddit discussions in relevant subreddits. YouTube reviews by non-Chinese creators. Local news coverage. Trustpilot/BBB profile with real reviews.
- **SUSPICIOUS (+3):** Few mentions, mostly in promotional contexts. One or two reviews.
- **NOT_FOUND (-5):** Zero English-language community discussion. No Reddit/YouTube/X mentions.
- **RED_FLAG (-10):** Only mentions are Chinese-language SEO content. Paid reviews on YouTube. Fake Reddit posts.

### Step 8: SEO Content Quality

- **VERIFIED (+10):** Genuine editorial coverage from independent publications in both English and Chinese. Diverse authors with real bylines. Content has specific, unique observations.
- **SUSPICIOUS (+3):** Mix of real and SEO content. Some genuine articles alongside templated listicles.
- **NOT_FOUND (0):** Very little content in either language. Neutral — could be a small legitimate brand.
- **RED_FLAG (-10):** Overwhelmingly SEO content: templated listicles, content farm articles, coordinated Xiaohongshu campaigns, planted Zhihu Q&As, press release wires disguised as news. AI-generated content with generic superlatives.

### Step 9: Chinese Entity Cross-Reference

- **VERIFIED (+10):** No hidden Chinese entity found. Or the Chinese entity is clearly a subsidiary/distributor of the foreign parent company.
- **SUSPICIOUS (+3):** A Chinese entity exists and has the brand name, but the corporate relationship is unclear.
- **NOT_FOUND (0):** No Chinese entity found on Qichacha/Tianyancha. Neutral.
- **RED_FLAG (-10):** Chinese entity is the actual operator (owns the trademark, manages marketing, contracts manufacturing). Brand is a facade for a domestic company. Product manufactured by known Chinese contract manufacturers (仙乐健康, 汤臣倍健 OEM, etc.).

---

## Score Calculation

1. Sum all step scores to get `raw_score` (range: -100 to +100)
2. Map to verdict using thresholds below
3. Confidence = `abs(raw_score)`, capped at 99

---

## Verdict Mapping

| Raw Score Range | Verdict (EN) | 判定结果 (CN) | Display Format |
|----------------|-------------|-------------|----------------|
| +60 to +100 | REAL BRAND | 正品品牌 | `正品品牌 — 可信度 {confidence}%` |
| +20 to +59 | LIKELY REAL | 大概率正品 | `大概率正品 — 可信度 {confidence}%` |
| -19 to +19 | UNCERTAIN | 待定 | `待定 — 需人工复核` |
| -59 to -20 | LIKELY FAKE | 大概率假洋牌 | `大概率假洋牌 — 可信度 {confidence}%` |
| -100 to -60 | FAKE BRAND | 假洋牌 | `假洋牌 — 可信度 {confidence}%` |

## Signal Rating Labels (Chinese)

| EN | CN |
|----|-----|
| VERIFIED | 已验证 |
| SUSPICIOUS | 可疑 |
| NOT_FOUND | 未找到 |
| RED_FLAG | 危险信号 |

---

## Evidence Collection

For each step, collect and record:
1. **Signal rating** (VERIFIED / SUSPICIOUS / NOT_FOUND / RED_FLAG)
2. **Score** (numeric value from the table above)
3. **Key evidence** (2-3 bullet points of what was found)
4. **Source URLs** (the actual URLs visited during investigation)
5. **Screenshots or quotes** (relevant excerpts from web pages)
