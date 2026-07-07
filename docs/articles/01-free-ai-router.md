# 别再手动切换 AI 模型了！这个开源工具让你一次配置，永久自动 Fallback

> 免费、开源、零依赖，支持 GitHub Models / Gemini /Groq / OpenRouter 四路并行，一个 API Key 永远不掉线。

---

## 痛点

用 AI 写代码的人都有这个经历：

- DeepSeek 又限流了
- GitHub Models免费额度用完了
- Gemini 突然返回 429
- OpenRouter 节点挂了

然后呢？手动换 key、改配置、重启客户端。一上午能折腾个三四次。

**如果有一个工具，能自动在这四家之间切换——谁可用就用谁，挂了自动换下一个——是不是就省心了？**

这就是 **[Free AI Router](https://github.com/fast1188/free-ai-router)**。开源、零依赖、部署只要 30 秒。

---

## 架构

```
你的 AI 客户端
    ↓
Free AI Router (localhost:8787)
    ↓ 并发请求
  ┌─────┬──────┬──────┬──────────┐
  │GitHub│Gemini│ Groq │OpenRouter│
  │Models│      │      │          │
  └─────┴──────┴──────┴──────────┘
    ↓ 第一个成功即返回
  AI 响应
```

**核心机制**：四路并行发请求，谁先返回有效的就拿谁的结果，其他 abort 掉。

**效果**：
- 四家挂三家都没事，只要还有一家活着，你的 AI客户端就能正常工作
- 不需要等一家超时再试下一家——并发赛马，延迟 = 最快那家的延迟
- 完全无感知切换，你根本不知道背后哪家在干活

---

## 30 秒部署

```bash
git clone https://github.com/fast1188/free-ai-router.git
cd free-ai-router
cp .env.example .env
# 编辑 .env，填你的 API Key（至少填一个）
npm install && npm start
```

访问 `http://localhost:8787`，选一个模型，直接开始聊。

---

## 支持的模型

| 提供商 | 免费额度 | 模型举例 |
|---|---|---|
| **GitHub Models** | 免费（限速）| gpt-4o-mini, gpt-4.1, llama-3.3 |
| **Gemini** | 免费（限速）| gemini-2.5-pro, gemini-2.5-flash |
| **Groq** | 免费（限速）| llama-4-maverick, deepseek-r1-distill |
| **OpenRouter** | 按量付费 | claude-sonnet-4.6, claude-opus-4.8, gpt-5.5 |

**最省钱的方案**：三个免费提供商轮着用，月费零元。

**最强的方案**：免费档日常用 + OpenRouter 兜底（按量付费），有额度时完全不花钱，没额度时才扣一点。

---

## 跟其他方案的对比

| 方案 | 免费 | 自动 Fallback | 并发 | 零依赖 |
|---|---|---|---|---|
| **直接调 API** | ❌ 单点 | ❌ | ❌ | - |
| **OpenRouter** | ❌ 付费 | ❌ | ❌ | ✅ |
| **One API** | ❌ 自己配 | ⚠️轮询 | ❌ | ❌ |
| **Free AI Router** | ✅ | ✅ | ✅ 并发 | ✅ |

---

## 配套工具链

Fast1188 生态里还有几个跟你日常开发相关的工具：

- **[CC Switch](https://github.com/fast1188/cc-switch)** — Windows 桌面 GUI，一键切换 AI 客户端代理模型。零依赖，exe 双击就运行。
- **[AI Agent Skills](https://github.com/fast1188/ai-agent-skills)** — 11 个跨 AI 工具的 Skills（Claude Code / Cursor / Codex / OpenClaw 都能用）。
- **[Console](https://github.com/fast1188/console)** — 10 个 AI 工具的总览入口，GitHub Pages 直接访问。

---

## 下一步

项目还在活跃开发中，如果你觉得有用：

- ⭐ **给个 Star** — 目前 0 star，每一个都算数
- 🐛 **提 Issue** — 遇到问题直接开
- 🔧 **贡献代码** — PR 欢迎
- 📢 **转发本文** — 让更多开发者省掉手动切模型的痛苦

---

> GitHub: [https://github.com/fast1188/free-ai-router](https://github.com/fast1188/free-ai-router)
> Gitee: [https://gitee.com/wudijia2026/free-ai-router](https://gitee.com/wudijia2026/free-ai-router)
