# 🔍 真假洋牌识别.skill

**真假洋牌验证器** — AI Agent skill，帮助中国消费者识别假洋牌。

## 功能

输入一个品牌名（无需提供产地，自动识别），自动完成 9 步深度调查：

1. **品牌识别与准备** — 自动识别中英文品牌名、产品类别、声称产地，匹配对应国家数据库
2. **政府与监管数据库**（权重 20%）— 工商注册查询、产品监管备案（TGA/FDA/PMDA）、Google Maps 地址核实
3. **商标时间线分析**（权重 15%）— 对比原产国与 CNIPA 商标注册时间，识别抢注行为
4. **域名与网站分析**（权重 10%）— WHOIS 信息、Wayback Machine 历史快照、服务器/主机位置（是否中国托管）、"关于我们"页面措辞分析（识别"源自"等模糊话术）、可疑域名后缀检测（.cc/.xyz/.top）
5. **零售渠道存在度**（权重 15%）— 原产国主流零售商（Chemist Warehouse / Walgreens / Boots 等）、Amazon、Google Shopping、地区比价网（kakaku / danawa / price.com.hk / FindPrice）、**1688/阿里巴巴批发检测**（出现即为危险信号）、是否仅在中国电商平台有售
6. **社交与职业足迹**（权重 10%）— LinkedIn 公司页面及员工构成、Instagram / Facebook / TikTok 官方账号及互动语言
7. **社区与媒体存在度**（权重 10%）— Reddit / X / YouTube 有机讨论、Google News 当地报道、主流国际媒体（BBC / CNN / NYT / Forbes）、Trustpilot / BBB 评价、专业评测（Wirecutter / Choice / Consumer Reports）、政府网站提及（`inurl:gov` 搜索）
8. **SEO 内容质量分析**（权重 10%）— Google 英文搜索结果分类（真实编辑 vs SEO 水文 vs 新闻稿）、小红书投放协调检测、知乎种草问答识别、百度软文占比、AI 生成内容检测
9. **中国实体交叉验证**（权重 10%）— 企查查/天眼查公司查询、NMPA 蓝帽子注册（保健品）、代工厂线索排查（仙乐健康/汤臣倍健 OEM 等）、进口渠道分析（一般贸易 vs 跨境电商保税仓）、**中国裁判文书网**诉讼记录、**商务部中国商品网**进出口数据

## 判定结果

| 分数范围 | 判定 | 颜色 |
|---------|------|------|
| +60 ~ +100 | 正品品牌 | 🟢 |
| +20 ~ +59 | 大概率正品 | 🟢 |
| -19 ~ +19 | 待定 | 🟡 |
| -20 ~ -59 | 大概率假洋牌 | 🟠 |
| -60 ~ -100 | 假洋牌 | 🔴 |

假洋牌还会标注段位（参考[少数派方法论](https://sspai.com/post/57916)）：

| 段位 | 特征 |
|-----|------|
| **低阶** | 无真实海外背景，山寨域名（.cc/.xyz），中国服务器，仅淘宝/拼多多有售 |
| **中阶** | 海外注册公司，专业双语官网，但 Google 搜不到、海外电商无售 |
| **高阶** | 收购没落外国品牌/购买授权/设立空壳公司回购自有品牌，需深度交叉验证才能识别 |

## 输出

- 终端实时中文调查报告（含品牌名 + 判定 + 可信度）
- 假洋牌标注段位：**低阶**（粗制滥造）/ **中阶**（海外注册但无实际业务）/ **高阶**（收购没落品牌或空壳公司回购）
- 可选生成 PDF 验真报告（中文，调查完成后询问用户）

## 安装

在 Claude Code 中运行：

```
# 1. 添加 marketplace
/plugin marketplace add zhongth/is-this-brand-fake.skill

# 2. 安装插件
/plugin install is-this-brand-fake@zhongth-is-this-brand-fake-skill
```

或者手动安装：将 `skills/is-real-brand/` 目录复制到你项目的 `.claude/skills/` 下即可。

## 使用

```
/is-real-brand 优思益 (YouthIt)
/is-real-brand MUJIE 无印良品
```

## 覆盖地区

内置数据库覆盖以下地区的政府注册、商标、零售渠道：

🇦🇺 澳大利亚 · 🇺🇸 美国 · 🇯🇵 日本 · 🇰🇷 韩国 · 🇳🇿 新西兰 · 🇬🇧 英国/欧盟 · 🇭🇰 香港 · 🇹🇼 台湾

跨国数据库：CNIPA、企查查、天眼查、裁判文书网、Google Shopping、Alibaba/1688 等

## 联网方式

Skill 会自动选择当前环境中可用的最佳联网工具，无需手动配置

## 依赖

- [Claude Code](https://claude.ai/claude-code)
- 联网能力（任意一种即可：web-access skill、playwright、WebSearch/WebFetch）
- `pdf` skill（生成报告，可选）

## License

MIT
