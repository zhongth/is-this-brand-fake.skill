# Country-Specific Validation Databases

Reference map of databases, URLs, and search query templates organized by country.
Used by the is-real-brand skill to determine which checks to perform based on claimed origin.

---

## Australia

### Regulatory & Business Registration
| Database | URL | What to Search | What a Real Brand Shows |
|----------|-----|---------------|------------------------|
| ABN Lookup | `https://abr.business.gov.au/` | Search brand/company name | Active ABN, GST registered, entity type is company (not sole trader), registered 3+ years |
| ASIC Company Search | `https://connectonline.asic.gov.au/` | Search company name | Directors with Australian names, real office address, active filing history, annual reports |
| TGA ARTG | `https://www.tga.gov.au/resources/artg` | Search product/brand name | Product listed or registered (not just "listed" — registered means more scrutiny), sponsor is the brand itself |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| IP Australia | `https://search.ipaustralia.gov.au/trademarks/search/quick` | Search brand name in "Trade Mark" field |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Chemist Warehouse | `https://www.chemistwarehouse.com.au/search?searchtext={brand}` |
| Priceline Pharmacy | `https://www.priceline.com.au/search?q={brand}` |
| Coles | `https://www.coles.com.au/search?q={brand}` |
| Woolworths | `https://www.woolworths.com.au/shop/search/products?searchTerm={brand}` |
| Amazon AU | `https://www.amazon.com.au/s?k={brand}` |

### Local Review/Community
| Platform | Search Pattern |
|----------|---------------|
| ProductReview.com.au | `https://www.productreview.com.au/search?q={brand}` |
| Choice (consumer reviews) | `https://www.choice.com.au/search?q={brand}` |

### Notes
- Australian `.com.au` domains require an ABN — WHOIS is useful here
- TGA "listed" vs "registered" distinction matters: "listed" is low-evidence self-certification, "registered" requires clinical evidence
- Common fake-brand pattern: register a company in Melbourne/Sydney with a Chinese director, use a virtual office address

---

## United States

### Regulatory & Business Registration
| Database | URL | What to Search | What a Real Brand Shows |
|----------|-----|---------------|------------------------|
| FDA Label Search | `https://labels.fda.gov/` | Search brand/product name | Product in FDA database with manufacturer info |
| FDA Import Entries | `https://datadashboard.fda.gov/oii/cd/impentry-table.htm` | Search company name | Import records showing real shipments |
| California SOS | `https://bizfileonline.sos.ca.gov/search/business` | Search company name | Active corporation/LLC with filing history |
| Delaware ICIS | `https://icis.corp.delaware.gov/ecorp/entitysearch/namesearch.aspx` | Search company name | Entity registration details |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| USPTO | `https://tmsearch.uspto.gov/` | Search brand name |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Amazon US | `https://www.amazon.com/s?k={brand}` |
| Walmart | `https://www.walmart.com/search?q={brand}` |
| iHerb | `https://www.iherb.com/search?kw={brand}` |
| CVS | `https://www.cvs.com/search?searchTerm={brand}` |
| Walgreens | `https://www.walgreens.com/search/results.jsp?Ntt={brand}` |

### Local Review/Community
| Platform | Search Pattern |
|----------|---------------|
| BBB | `https://www.bbb.org/search?find_text={brand}` |
| Trustpilot | `https://www.trustpilot.com/search?query={brand}` |
| Consumer Reports | `https://www.consumerreports.org/search/?query={brand}` |
| Wirecutter | `https://www.nytimes.com/wirecutter/?s={brand}` |

---

## Japan

### Regulatory & Business Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| National Tax Agency (法人番号) | `https://www.houjin-bangou.nta.go.jp/` | Search company name in Japanese |
| PMDA | `https://www.pmda.go.jp/english/search_index.html` | Search product/drug name |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| J-PlatPat (JPO) | `https://www.j-platpat.inpit.go.jp/` | Search brand name (English and Japanese) |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Amazon JP | `https://www.amazon.co.jp/s?k={brand}` |
| Rakuten | `https://search.rakuten.co.jp/search/mall/{brand}/` |
| Matsumoto Kiyoshi | `https://www.matsukiyo.co.jp/store/online/search?text={brand}` |

---

## South Korea

### Regulatory & Business Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| MFDS (식약처) | `https://www.mfds.go.kr/eng/index.do` | Search product/company name |
| KIPRIS (Korean IP) | `https://www.kipris.or.kr/` | Search brand name |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Coupang | `https://www.coupang.com/np/search?q={brand}` |
| Olive Young | `https://www.oliveyoung.co.kr/store/search/getSearchMain.do?query={brand}` |

---

## New Zealand

### Regulatory & Business Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| NZ Companies Register | `https://companies-register.companiesoffice.govt.nz/` | Search company name |
| Medsafe | `https://www.medsafe.govt.nz/regulatory/dbsearch.asp` | Search product name |
| IPONZ | `https://app.iponz.govt.nz/` | Search brand name |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Countdown | `https://www.countdown.co.nz/shop/searchproducts?search={brand}` |

---

## United Kingdom / European Union

### Regulatory & Business Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| Companies House (UK) | `https://find-and-update.company-information.service.gov.uk/` | Search company name |
| VIES VAT Check (EU) | `https://ec.europa.eu/taxation_customs/vies/` | Check VAT number if available |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| EUIPO eSearch | `https://euipo.europa.eu/eSearch/` | Search brand name |
| UK IPO | `https://trademarks.ipo.gov.uk/ipo-tmtext` | Search brand name |

### Retail Channels
| Retailer | Search URL Pattern |
|----------|-------------------|
| Amazon UK | `https://www.amazon.co.uk/s?k={brand}` |
| Amazon DE | `https://www.amazon.de/s?k={brand}` |
| Boots (UK) | `https://www.boots.com/search?q={brand}` |

---

## Hong Kong

### Company Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| ICRIS (Hong Kong Companies Registry) | `https://www.icris.cr.gov.hk/` | Search company name |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| HK Intellectual Property Dept | `https://ipsearch.ipd.gov.hk/` | Search brand name |

### Price Comparison
| Platform | Search URL Pattern |
|----------|-------------------|
| Price.com.hk | `https://www.price.com.hk/search.php?q={brand}` |

---

## Taiwan

### Company Registration
| Database | URL | What to Search |
|----------|-----|---------------|
| 經濟部商業司 | `https://gcis.nat.gov.tw/pub/cmpy/cmpyInfoListAction.do` | Search company name |

### Trademark
| Database | URL | What to Search |
|----------|-----|---------------|
| 智慧財產局 | `https://tmsearch.tipo.gov.tw/` | Search brand name |

### Price Comparison
| Platform | Search URL Pattern |
|----------|-------------------|
| FindPrice | `https://www.findprice.com.tw/datalist.aspx?key={brand}` |

---

## Cross-Country (Always Check)

### Chinese Trademark (for timeline comparison)
| Database | URL | What to Search |
|----------|-----|---------------|
| CNIPA | `https://sbj.cnipa.gov.cn/` | Search brand name (Chinese + English) |

### Chinese Entity Lookup
| Database | URL | What to Search |
|----------|-----|---------------|
| Qichacha | `https://www.qcc.com/` | Search brand name, company name |
| Tianyancha | `https://www.tianyancha.com/` | Search brand name, company name |
| NMPA (Blue Hat) | `https://www.nmpa.gov.cn/` | Search product name for health food registration |

### Domain Analysis
| Tool | URL | What to Check |
|------|-----|--------------|
| ICANN WHOIS | `https://lookup.icann.org/` | Domain registrant, registration date, registrar location |
| who.is | `https://who.is/` | Alternative WHOIS with parsed output |
| Wayback Machine | `https://web.archive.org/web/` | First snapshot date, original content language |

### Chinese Legal & Trade Records
| Database | URL | What to Check |
|----------|-----|--------------|
| 中国裁判文书网 | `https://wenshu.court.gov.cn/` | Lawsuits, trademark disputes, false advertising cases |
| 商务部中国商品网 | `https://ccn.mofcom.gov.cn/` | Import/export records — real imports leave customs traces |
| 全国企业信用信息公示系统 | `https://gsxt.saic.gov.cn/` | Official business registration (more authoritative than Qichacha) |

### International Business Directories
| Directory | URL | What to Check |
|-----------|-----|--------------|
| Kompass | `https://www.kompass.com/` | International company database — verify company exists abroad |
| Dun & Bradstreet | `https://www.dnb.com/` | Global business credit reports |
| Firmen Wissen (Germany) | `https://www.firmenwissen.de/` | German company lookup |

### Google Shopping & Price Comparison
| Platform | URL | Coverage |
|----------|-----|---------|
| Google Shopping | `https://www.google.com/shopping?q={brand}` | Global — real brands show up here |
| Yahoo Shopping | `https://shopping.yahoo.com/?p={brand}` | US |
| Kakaku (価格.com) | `https://kakaku.com/` | Japan |
| Danawa | `https://www.danawa.com/` | South Korea |

### B2B Wholesale Platforms (Red Flag Check)
| Platform | URL | What to Check |
|----------|-----|--------------|
| Alibaba.com | `https://www.alibaba.com/trade/search?SearchText={brand}` | If "foreign" brand products are sold wholesale here → red flag |
| 1688.com | `https://s.1688.com/selloffer/offer_search.htm?keywords={brand}` | Domestic wholesale — indicates Chinese manufacturing |

### Global Platforms
| Platform | Search URL Pattern |
|----------|-------------------|
| Google | `https://www.google.com/search?q={brand}` |
| Google Maps | `https://www.google.com/maps/search/{brand}+{address}` |
| LinkedIn | `https://www.linkedin.com/company/{brand}/` or search |
| Instagram | `https://www.instagram.com/{brand}/` |
| Facebook | `https://www.facebook.com/search/pages?q={brand}` |
| TikTok | `https://www.tiktok.com/@{brand}` |
| YouTube | `https://www.youtube.com/results?search_query={brand}+review` |
| Reddit | `https://www.reddit.com/search/?q={brand}` |
| X (Twitter) | `https://x.com/search?q={brand}` |
