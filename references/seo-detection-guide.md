# SEO Content Quality Detection Guide

Heuristics for distinguishing genuine editorial content from manufactured SEO filler,
covering both English-language and Chinese-language ecosystems.

---

## English-Language SEO Detection

### Content Farm Signals
Look for these patterns when analyzing Google search results for the brand:

**Site-level red flags:**
- Domain is a generic keyword domain (e.g., `best-health-supplements.com`, `top10vitamins.net`)
- Site has no "About" page, no editorial team listed, no physical address
- Site covers an impossibly broad range of product categories (supplements AND electronics AND fashion)
- WHOIS shows domain registered recently or by a domain privacy service
- Low Domain Authority / no backlink profile from reputable sites

**Article-level red flags:**
- "Top 10 Best [Category] in [Year]" listicle format where the brand appears alongside well-known brands
- No real author byline, or author has no other published work / no LinkedIn profile
- Article reads as a product description, not a review (no personal experience, no downsides mentioned)
- Same article or very similar text appears on multiple unrelated domains
- Comments section is empty, disabled, or filled with generic "Great article!" bot comments
- Article contains affiliate links to Chinese e-commerce platforms (Tmall, JD) rather than local retailers

**Press release detection:**
- Published via PR Newswire, BusinessWire, GlobeNewswire, or similar wire services
- Headline style: "[Brand Name] Announces Launch of [Product] in [Market]"
- Body text reads like corporate communications, not journalism
- "News" article has no reporter byline, just "Staff" or "PR Newswire"
- Multiple "news" outlets published identical text on the same day

### Genuine Content Signals
- Published by known editorial outlets (newspapers, magazines, established review sites)
- Author has a history of writing about the product category
- Content includes specific personal experience, comparisons with competitors, mentions of downsides
- Unique photos (not stock or manufacturer-supplied)
- Reader comments show genuine engagement and questions

---

## Chinese-Language SEO Detection

### Xiaohongshu (小红书) Patterns

**Coordinated campaign signals:**
- Multiple posts about the brand appearing within a short timeframe (e.g., 20+ posts in one week)
- Posts use similar language, same product photos, same angle/background
- Posters are new accounts or accounts that primarily post brand reviews
- Posts follow a template: "Recently discovered this [Australian/American/Japanese] brand..." (最近发现了这个[澳洲/美国/日本]品牌...)
- Excessive use of superlatives without specific experience details
- No negative or mixed reviews exist — 100% positive is suspicious

**Genuine signals:**
- Posts spread over months/years with varied language and photos
- Posters have diverse content history (not just brand reviews)
- Some posts mention drawbacks or comparisons
- Engagement includes genuine questions and varied responses

### Zhihu (知乎) Patterns

**Planted Q&A signals:**
- Question and top answer posted within hours of each other
- Question is oddly specific: "Is [Brand] a good Australian brand?" (XX品牌是不是正宗澳洲品牌？)
- Top answer reads like marketing copy with bullet-pointed "advantages"
- Answer author has very few other answers, or their other answers are all brand-related
- Multiple questions about the same brand phrased slightly differently

**Genuine signals:**
- Question has been open for months with multiple varied answers
- Answers include both positive and negative perspectives
- Authors have diverse Q&A history on Zhihu

### WeChat / Weixin (微信公众号) Patterns

**Brand-controlled signals:**
- Article is from the brand's own WeChat account
- Article is from a "health" or "lifestyle" account that only promotes products
- Content is pure promotional with no editorial independence
- Account has suspiciously high "reading" numbers but low engagement (comments)

### Baidu Search Patterns

**SEO manipulation signals:**
- First page results are all from Baidu Baike (百度百科), Baidu Zhidao (百度知道), and soft-article platforms
- Baike page was created recently and reads like a company brochure
- "Knowledge" articles all emphasize the same marketing points (imported, premium, natural)
- No results from independent Chinese consumer platforms or media

---

## AI-Generated Content Detection

### Writing Quality Red Flags
- Repetitive sentence structure (Subject-Verb-Object pattern repeating)
- Generic superlatives: "industry-leading," "world-class," "revolutionary," "unparalleled"
- Lack of specific anecdotes or personal experience
- Perfect grammar but zero personality or voice
- Interchangeable brand name — the article would read the same with any brand name substituted
- Paragraphs that sound authoritative but contain no verifiable claims

### Image Red Flags
- Stock photos from common libraries (can sometimes detect via reverse image search)
- Product photos that look like 3D renders rather than real photographs
- "Lifestyle" images with generic models, not real customers
- Same product photos used across all marketing materials with no user-generated content

---

## Scoring Decision Tree

When analyzing search results for a brand, walk through this:

1. **Google first 2 pages in English:** Count results that are (a) genuine editorial, (b) SEO/content farm, (c) press releases, (d) the brand's own content
2. **Baidu/Sogou first 2 pages in Chinese:** Same count
3. **Xiaohongshu search:** Check top 20 posts for coordinated campaign patterns
4. **Zhihu search:** Check top 5 Q&As for planted patterns

**Verdict:**
- Majority genuine editorial + organic social = **VERIFIED**
- Mix of genuine and manufactured = **SUSPICIOUS**
- Very little content total = **NOT_FOUND**
- Overwhelmingly manufactured content, coordinated campaigns = **RED_FLAG**
