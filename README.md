# 🔍 真假洋牌识别.skill

**真假洋牌验证器** — AI Agent skill，帮助中国消费者识别假洋牌。

## 功能

输入一个品牌名，自动完成 9 步深度调查，判断该品牌是否为真正的海外品牌：

1. **品牌识别** — 自动识别中英文品牌名、产品类别、声称产地
2. **政府与监管数据库**（20%）— 工商注册、监管备案、地址核实
3. **商标时间线**（15%）— 对比原产国与中国商标注册时间
4. **域名与网站分析**（10%）— WHOIS、服务器位置、"关于我们"页面语言分析
5. **零售渠道**（15%）— 原产国零售商、Google Shopping、Alibaba/1688 批发检查
6. **社交与职业足迹**（10%）— LinkedIn、Instagram、Facebook、TikTok
7. **社区与媒体**（10%）— Reddit、YouTube、主流媒体、政府网站提及
8. **SEO 内容质量**（10%）— 小红书、知乎、百度内容真伪分析
9. **中国实体交叉验证**（10%）— 企查查/天眼查、裁判文书网、进出口记录

## 判定结果

| 分数范围 | 判定 | 颜色 |
|---------|------|------|
| +60 ~ +100 | 正品品牌 | 🟢 |
| +20 ~ +59 | 大概率正品 | 🟢 |
| -19 ~ +19 | 待定 | 🟡 |
| -20 ~ -59 | 大概率假洋牌 | 🟠 |
| -60 ~ -100 | 假洋牌 | 🔴 |

假洋牌还会标注段位：**低阶** / **中阶** / **高阶**

## 输出

- 终端实时中文调查报告
- 自动生成 PDF 验真报告（中文）

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
