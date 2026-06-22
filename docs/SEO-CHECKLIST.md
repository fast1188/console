# Console 静态站 SEO 改造清单

> 创建: 2026-06-22 · 适用文件: `D:/Github开源项目/项目源码/console/index.html`
> 预计耗时: 10 分钟 · 改完部署: `git add && commit && push`(console 仓双推)
> **作用**: GitHub Pages 收录 + 微信/Twitter 分享卡片好看 + Gitee 镜像被搜到

---

## 1. 必须加的 `<head>` meta 标签

在 `index.html` 的 `<head>` 里(就在 `<title>` 之后)加:

```html
<meta name="description" content="fast118 AI 工具生态总入口 - 11 个跨 AI 编程工具的开源 Skills 集合 / 多 AI 后端 fallback 路由器 / 桌面切换器 / 控制台 / 飞书机器人">
<meta name="keywords" content="Claude Code, Codex, Cursor, OpenClaw, Hermes, AI Skills, fallback, token优化, 中文开发, 开源">
<meta name="author" content="fast1188">

<!-- Open Graph (微信/Twitter/微博 分享卡片) -->
<meta property="og:title" content="fast118 AI 工具生态 | 控制台">
<meta property="og:description" content="11 个跨 AI 工具的开源 Skills 集合,GitHub + Gitee 双仓 600+ star">
<meta property="og:type" content="website">
<meta property="og:url" content="https://fast1188.github.io/console/">
<meta property="og:image" content="https://fast1188.github.io/console/assets/og-cover.png">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="fast118 AI 工具生态 | 控制台">
<meta name="twitter:description" content="11 个跨 AI 工具的开源 Skills 集合,免费白嫖">
<meta name="twitter:image" content="https://fast1188.github.io/console/assets/og-cover.png">

<!-- canonical 防重复 -->
<link rel="canonical" href="https://fast1188.github.io/console/">

<!-- favicon (放 assets/favicon.ico) -->
<link rel="icon" type="image/x-icon" href="assets/favicon.ico">

<!-- 中文搜索引擎必填 -->
<meta name="baidu-site-verification" content=""><!-- 百度站长平台验证后填 -->
<meta name="360-site-verification" content=""><!-- 360 站长平台验证后填 -->
```

---

## 2. 加 og-cover.png

`assets/og-cover.png` 1200×630 px,包含:
- 大字 "fast118 AI 工具生态"
- 副标题 "11 个开源 Skills · 多 AI fallback · 桌面切换"
- 左下角 fast1188 logo
- 背景用和站内一致的紫绿渐变 (#1e1e2e → #22C55E)

工具: Canva / Figma / PowerPoint 都行,导出 PNG 放 `console/assets/`

---

## 3. 加 Gitee 镜像链接

站内每个 GitHub 按钮下面加一行:

```html
<p style="text-align:center;font-size:12px;color:#888;margin-top:8px">
  镜像: <a href="https://gitee.com/wudijia2026/console">Gitee</a> · 国内更快
</p>
```

(已有 6 个项目按钮,每个加一行)

---

## 4. 顶部加"Star 数 + 项目数"实时统计

替换 `console/index.html` 里 fetch 的 `repos/${r.name}` 部分,改成:

```javascript
const repos = ['ai-agent-skills', 'codex-pp', 'cc-switch', 'free-ai-router',
               'free-ai-router-webui', 'console', 'fast118', 'feishu-bot',
               'ai-empire-v5.1', 'ai-empire-factory'];
Promise.all(repos.map(r =>
  fetch(`https://api.github.com/repos/fast1188/${r}`)
    .then(r => r.json())
    .then(d => ({ name: r, stars: d.stargazers_count, forks: d.forks_count }))
    .catch(() => ({ name: r, stars: 0, forks: 0 }))
)).then(data => {
  const totalStars = data.reduce((s, d) => s + d.stars, 0);
  document.getElementById('total-stars').textContent = totalStars;
  document.getElementById('total-repos').textContent = data.length;
});
```

顶部的 stats-bar 加 `id="total-stars"` 和 `id="total-repos"`。

---

## 5. JSON-LD 结构化数据 (SEO 加成)

`<head>` 末尾加:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "fast118 AI 工具生态",
  "url": "https://fast1188.github.io/console/",
  "description": "11 个跨 AI 编程工具的开源 Skills 集合",
  "author": {
    "@type": "Person",
    "name": "fast1188",
    "url": "https://github.com/fast1188"
  }
}
</script>
```

---

## 6. 提交搜索引擎收录

1. **Google Search Console**: https://search.google.com/search-console → 添加属性 `https://fast1188.github.io/console/` → 用 HTML 标签验证
2. **Bing Webmaster**: https://www.bing.com/webmasters → 同上
3. **百度站长平台**: https://ziyuan.baidu.com → 添加站点 → HTML 验证
4. **Gitee Pages 收录**: 在 Gitee 仓的 issues 提一个"求收录" → Gitee 官方会处理

---

## 7. 验证清单

改完后:

- [ ] https://fast1188.github.io/console/ 加载没 404
- [ ] 浏览器开发者工具 → Elements → 看到 og:title / og:image / description
- [ ] https://www.opengraph.xyz/ 输入 URL → 看到分享卡片预览
- [ ] https://cards-dev.twitter.com/validator 输入 URL → Twitter Card 正确
- [ ] 提交 sitemap (用 https://www.xml-sitemaps.com/ 生成 console 的 sitemap.xml)
- [ ] Google Search Console 提交 sitemap

---

## 优先级

| 步骤 | 时长 | 效果 |
|---|---|---|
| 1. meta 标签 | 5 min | SEO 基础 |
| 2. og-cover.png | 30 min | 分享卡片 |
| 3. Gitee 镜像 | 2 min | 国内流量 |
| 4. 实时 star | 10 min | 数据展示 |
| 5. JSON-LD | 2 min | 富搜索结果 |
| 6. 收录 | 10 min | 长尾流量 |
| 7. 验证 | 5 min | 确认生效 |

**全做完: ~1 小时, 引流效果 = 10x 被动流量**
