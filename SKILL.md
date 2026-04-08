---
name: is-real-brand
description: >
  Validate if a brand is a real overseas brand or a fake pseudo-foreign brand (假洋牌).
  Takes a brand name and claimed country of origin, performs 9-step investigation via
  web-access, and outputs a confidence verdict plus a detailed PDF report.
---

# Is Real Brand - Brand Authenticity Validator

Validate whether a consumer brand is a genuine overseas/international brand or a fake
"pseudo-foreign brand" (假洋牌) marketed to Chinese consumers.

## Input Format

The user invokes this skill with:
```
/is-real-brand <brand-name>
```
or:
```
/is-real-brand <brand-name> - <claimed-country>
```

Parse the input to extract:
- **Brand name**: May include Chinese name, English name, or both (e.g., "优思益 (YouthIt)")
- **Claimed country of origin** (optional): The country the brand claims to be from (e.g., "Australia")

If the country is NOT provided, determine it automatically in Step 1 by searching for the brand
and identifying what country it claims to originate from. Do NOT ask the user — figuring out the
origin is part of your job.

## Output Language

**All output MUST be in Chinese (中文).** This includes:
- All chat/terminal output during the investigation (step summaries, evidence, verdict)
- The PDF report (all sections: cover, executive summary, findings, methodology, disclaimer)

Signal ratings (VERIFIED / SUSPICIOUS / NOT_FOUND / RED_FLAG) and verdict labels
(正品品牌 / 大概率正品 / 待定 / 大概率假洋牌 / 假洋牌) should use their Chinese equivalents.

## How to Run This Investigation

You are an investigative researcher. Your job is to determine if a brand is genuinely
from the country it claims, or if it is a Chinese company masquerading as a foreign brand.

Follow these 9 steps sequentially. For each step:
1. Use the **web-access** skill to search the relevant databases and websites
2. Record what you find (evidence, URLs, key data)
3. Assign a signal rating: 已验证, 可疑, 未找到, or 危险信号
4. Assign the numeric score per the scoring rubric

**IMPORTANT:** For all web searches, use the `web-access` skill. This uses the user's
local browser with existing cookies and authentication.

### Reference Files

Before starting, read these reference files for detailed guidance:
- `references/country-databases.md` — URLs and search patterns for each country
- `references/scoring-rubric.md` — How to rate each signal and calculate the final score
- `references/seo-detection-guide.md` — How to detect manufactured SEO content
- `references/report-template.md` — PDF report structure

---

## Step 1: Identify & Prepare

1. Parse the brand name (English + Chinese) and claimed country from the user input
2. If no claimed country was provided, search for the brand to determine what country it
   claims to originate from (check the brand's website, packaging claims, marketing materials)
3. If the user only provided a Chinese name, search for the English name
4. If the user only provided an English name, search for the Chinese name
5. Determine the product category (search the brand to understand what they sell)
6. Look up the country in `references/country-databases.md` to determine which databases to check

**Output:** State the brand name (both languages), country, product category, and which databases you will check.

---

## Step 2: Government & Regulatory Database Check

**Weight: 20% | Score range: -20 to +20**

Using `references/country-databases.md`, search the relevant government databases for the claimed country:

1. **Business registration:** Search the business registry (ABN Lookup, Companies House, etc.)
   - Is the company registered? How long ago? Who are the directors?
   - Is the registered address a real business location?

2. **Regulatory database:** Search product regulatory database (TGA, FDA, PMDA, etc.)
   - Is the product registered/listed?
   - Who is the registered sponsor/manufacturer?

3. **Address verification:** Search Google Maps for the registered business address
   - Is it a real office/warehouse? Or a residential address/virtual office/unrelated business?

Rate per `references/scoring-rubric.md` Step 2 criteria.

---

## Step 3: Trademark Timeline Analysis

**Weight: 15% | Score range: -15 to +15**

1. Search the origin country's IP/trademark database for the brand name
   - Record: filing date, registration date, owner, status

2. Search CNIPA (China's trademark database) for the same brand name
   - Record: filing date, registration date, owner

3. Compare the dates:
   - Origin country first by 2+ years = VERIFIED
   - Within 1 year / simultaneous = SUSPICIOUS
   - China first = RED_FLAG
   - Not found in origin country = NOT_FOUND

Rate per `references/scoring-rubric.md` Step 3 criteria.

---

## Step 4: Domain & Website Analysis

**Weight: 10% | Score range: -10 to +10**

1. Find the brand's official website domain
2. Run a WHOIS lookup:
   - When was the domain registered?
   - Who is the registrant? In which country?
   - Which registrar?

3. Check the Wayback Machine:
   - When was the first snapshot?
   - What language was the original content?

4. Visit the current website:
   - Is it a full multi-page site in the origin country's language?
   - Or a thin/static page primarily in Chinese?
   - Does it have: About page, Contact page, Store locator, Product catalog, Blog?

5. **"About Us" page language analysis:**
   - Does the brand history use vague phrasing like "源自"（derived from）without specifics?
   - Are founding stories verifiable, or do they sound fabricated (e.g., "royal heritage", "century-old tradition")?
   - Is the foreign contact info (email, phone, address) real and reachable?

6. **Server/hosting location check:**
   - Is the website hosted on Chinese servers (Aliyun, Tencent Cloud) despite claiming foreign origin?
   - Does the domain use unusual TLDs (.cc, .xyz, .top) instead of standard ones?

Rate per `references/scoring-rubric.md` Step 4 criteria.

---

## Step 5: Retail Channel Presence

**Weight: 15% | Score range: -15 to +15**

Using `references/country-databases.md`, search the major retail channels in the claimed origin country:

1. Search each retailer's website for the brand name
2. For each result found:
   - How many products are listed?
   - How many reviews? What date range?
   - Is the brand sold by the brand itself or a third-party reseller?

3. Also check global platforms:
   - Amazon (in the origin country's domain)
   - iHerb (for health/supplement brands)
   - **Google Shopping** — search the brand name; real brands show up in shopping results
   - Regional price comparison sites (kakaku.com for Japan, danawa.com for Korea,
     price.com.hk for HK, FindPrice for Taiwan)

4. Check if the product is ONLY available on Chinese platforms (Tmall Global, JD, Xiaohongshu)

5. **Alibaba/1688 wholesale check:** Search the brand on alibaba.com and 1688.com
   - If the brand's products are sold wholesale on these B2B platforms, it suggests
     domestic manufacturing rather than genuine import

Rate per `references/scoring-rubric.md` Step 5 criteria.

---

## Step 6: Social & Professional Footprint

**Weight: 10% | Score range: -10 to +10**

1. **LinkedIn:** Search for the brand's company page
   - Does it exist? How many employees?
   - Are employees from the origin country with real tenure?
   - Or is it empty / only Chinese-based employees?

2. **Instagram:** Search for the brand's account
   - Follower count? Engagement rate?
   - Content in what language? Follower demographics?

3. **Facebook:** Search for the brand's page
   - Exists? Posts in what language? Engagement?

4. **TikTok:** Search for the brand's account
   - Original content? Or just reposted marketing materials?

Rate per `references/scoring-rubric.md` Step 6 criteria.

---

## Step 7: Community & Media Presence

**Weight: 10% | Score range: -10 to +10**

1. **Reddit:** Search for the brand name — are there organic discussions?
2. **X (Twitter):** Search for mentions — organic or promotional?
3. **YouTube:** Search "{brand} review" — reviews by non-Chinese creators?
4. **Local news:** Search Google News for the brand in the origin country
5. **Mainstream international media:** Search for the brand on BBC, CNN, NYT, Forbes, WSJ
   — real brands with global presence get mentioned by major outlets
6. **Trustpilot / BBB:** Search for the brand's profile
7. **Professional reviews:** Search Wirecutter, Choice (AU), Consumer Reports
8. **Government mentions:** Search `"{brand}" inurl:gov` — real brands appear in government
   databases, recalls, import records, or regulatory filings

Rate per `references/scoring-rubric.md` Step 7 criteria.

---

## Step 8: SEO Content Quality Analysis

**Weight: 10% | Score range: -10 to +10**

Refer to `references/seo-detection-guide.md` for detailed heuristics.

1. **English-language analysis:**
   - Google the brand name, analyze first 2-3 pages of results
   - Categorize each result: genuine editorial / SEO content farm / press release / brand's own content
   - Check for cross-site content duplication
   - Check for real author bylines

2. **Chinese-language analysis:**
   - Search Xiaohongshu for the brand — check for coordinated posting campaigns
   - Search Zhihu for the brand — check for planted Q&A patterns
   - Search Baidu — ratio of genuine vs manufactured content

3. **AI/generated content check:**
   - Assess writing quality of articles found
   - Look for generic superlatives, lack of personal experience, interchangeable brand names

Rate per `references/scoring-rubric.md` Step 8 criteria.

---

## Step 9: Chinese Entity Cross-Reference

**Weight: 10% | Score range: -10 to +10**

1. **Qichacha / Tianyancha:** Search for the brand name and any related company names
   - Is there a Chinese company behind the brand?
   - What is the corporate relationship? Subsidiary? Independent operator?
   - Who are the shareholders?

2. **NMPA Blue Hat:** For supplement brands, check if the product has health food registration (蓝帽子)

3. **Contract manufacturer check:** Look for evidence of domestic manufacturing
   - Search for the brand + common OEM manufacturers (仙乐健康, 汤臣倍健, etc.)

4. **Import channel analysis:** Is the product imported via traditional channels or cross-border e-commerce (bonded warehouse)?

5. **中国裁判文书网:** Search `https://wenshu.court.gov.cn/` for the brand or company name
   - Are there lawsuits related to false advertising, trademark disputes, or consumer fraud?
   - Court records can reveal the true corporate structure behind a brand

6. **商务部中国商品网:** Search `https://ccn.mofcom.gov.cn/` for import/export data
   - Real imported brands should have customs/import records
   - Absence of import data for a brand claiming to be foreign is a red flag

Rate per `references/scoring-rubric.md` Step 9 criteria.

---

## Producing the Verdict

After completing all 9 steps:

1. **Sum all scores** to get the raw total (range: -100 to +100)
2. **Map to verdict** per `references/scoring-rubric.md`:
   - +60 to +100 → 正品品牌（REAL BRAND）
   - +20 to +59 → 大概率正品（LIKELY REAL）
   - -19 to +19 → 待定（UNCERTAIN）
   - -59 to -20 → 大概率假洋牌（LIKELY FAKE）
   - -100 to -60 → 假洋牌（FAKE BRAND）
3. **Confidence** = abs(raw_score), capped at 99

**Print the verdict to the terminal immediately (in Chinese):**
```
{中文判定} — 可信度 {confidence}%
```

### Fake Brand Tier Classification (假洋牌段位)

If the verdict is 假洋牌 or 大概率假洋牌, also classify the tier based on the article's
methodology (ref: https://sspai.com/post/57916):

- **低阶假洋牌：** No real foreign presence. Sketchy website (.cc/.xyz domains), Chinese hosting,
  fabricated brand history, only sold on Taobao/Pinduoduo. Easy to spot.
- **中阶假洋牌：** Registered company abroad, professional bilingual website, .com domain.
  But: no Google results internationally, no foreign retail presence, WHOIS/hosting reveals
  Chinese connections.
- **高阶假洋牌：** Nearly indistinguishable. May have acquired a real (often defunct) foreign brand,
  purchased licensing, or created overseas shell companies that re-import domestically-produced
  goods. Requires deep cross-referencing of trademark timelines, corporate structures, and
  import channel analysis to detect.

Include this tier classification in the verdict output and PDF report when applicable.

---

## Generating the PDF Report

After printing the verdict, generate a detailed PDF report:

1. Read `references/report-template.md` for the exact structure
2. Compile all evidence collected during the 9 steps
3. Use the `pdf` skill to generate the report
4. Save as `is-real-brand-{brand-name-slug}-{YYYY-MM-DD}.pdf` in the current working directory

Tell the user:
```
Report saved: is-real-brand-{brand-name-slug}-{YYYY-MM-DD}.pdf
```
