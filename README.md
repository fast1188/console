# Console (控制台首页)

> fast118 AI 工具生态的统一入口
>
> 一个 HTML 文件,GitHub Pages 免费托管

---

## 这是什么?

[控制台首页](https://fast118.github.io/console/) 是 fast118 所有 AI 工具项目的**统一展示页面**。

**包括的项目:**

| 项目 | 描述 |
|------|------|
| **ai-agent-skills** | 11 个跨 AI 工具 skills |
| **codex-pp** | 国产化 AI 编程 CLI |
| **cc-switch** | AI 工具桌面 GUI 切换器 |
| **free-ai-router** | 多 AI 路由 fallback |
| **api.skillai.top** | 国内直连 API 中转 |

## 特性

- ✓ 单文件 HTML,无构建工具
- ✓ 实时拉取 GitHub stars(forks 统计)
- ✓ 中文优先 UI
- ✓ 响应式设计(桌面/手机都好看)
- ✓ GitHub Pages 免费托管

## 部署

**方式 1: GitHub Pages**

1. 推代码到 `fast118/console` 仓库
2. Settings → Pages → Source 选 `main` 分支
3. 几分钟后访问 `https://fast118.github.io/console/`

**方式 2: 本地预览**

```bash
# 任何 HTTP server 都能跑
py -m http.server 8000
# 访问 http://localhost:8000
```

**方式 3: 直接打开**

`index.html` 双击就能在浏览器看(JS 拉 GitHub API 需要联网)

## 文件结构

```
console/
├── index.html       # 整个控制台(单文件)
├── assets/          # 预留:放 logo / 截图
└── README.md
```

## 实时数据

页面打开时自动拉取:
- 每个仓库的 stars
- forks 数量
- 自动求和到顶部统计

## 推广

- 每个项目 README 末尾放链接到控制台
- 控制台首页互相导流所有项目
- 4 个项目 + 1 个 API 业务,形成生态

## 维护

- 改 index.html 后 push 即可
- GitHub Pages 自动部署
- 几秒后生效

## License

MIT