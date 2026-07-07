# 我整理了 11 个 AI 编程助手的通用技能包——Claude Code、Cursor、Codex 都能用

> 开源、免费、跨 IDE、一键安装。不再被单一 AI 工具锁死。

---

## 为什么需要跨AI工具的技能

现在的 AI 编程助手市场非常碎片化：

- 有人用 Claude Code
- 有人用 Cursor
- 有人用 Codex
- 有人用 OpenClaw
- 还有人同时用两三个

每个工具都有自己的配置格式、自己的 skill 目录结构。你想要把一套好用的提示词、工作流、自动化脚本同时用在多个工具上，就得每个工具都手动配一遍。

**AI Agent Skills 就是解决这个问题的。**

---

## 包含的 11 个技能

| 编号 | 技能 | 用途 | 适用工具 |
|---|---|---|---|
| 01 | 提交规范 | 自动生成 Conventional Commits | 全部 |
| 02 | 代码审查 | 自动审查 PR / diff | 全部 |
| 03 | README 生成 | 从代码自动生成 README | 全部 |
| 04 | 发布日志 | 自动生成 CHANGELOG | 全部 |
| 05 | API 文档 | 从代码生成 API 文档 | 全部 |
| 06 | 测试生成 | 为函数自动写单元测试 | 全部 |
| 07 | 重构建议 | 分析代码并给出重构方案 | 全部 |
| 08 | 翻译技能 | 中英文技术文档互译 | 全部 |
| 09 | 截图解说 | 截图→AI 分析→文字说明 | 全部 |
| 10 | 网页抓取 | 结构化提取网页数据 | 全部 |
| 11 | Shell 脚本 | 生成跨平台 Shell 脚本 | 全部 |

所有技能都是**纯 Markdown** 格式，不依赖任何特定工具。直接复制到你用的 AI 助手的 skills 目录就能用。

---

## 一键安装

```bash
git clone https://github.com/fast1188/ai-agent-skills.git
cd ai-agent-skills
# Claude Code
cp skills/* ~/.claude/skills/
# Cursor
cp skills/* .cursor/skills/
# Codex
cp skills/* ~/.codex/skills/
```

就这么简单。不需要装任何依赖，不需要改任何配置。

---

## 为什么做成跨工具通用

很多开发者会在不同的 AI 工具之间切换：

- 日常写代码用 Cursor（便宜、快）
- 复杂重构用 Claude Code（能力强）
- 紧急修复用 Codex（集成 GitHub）

如果你的技能只能在一个工具上用，等于被锁死在一个平台上。跨工具通用意味着**你可以在任何工具里享受同一套工作流**。

---

## 生态系统

Fast1188 开源生态中还有几个配套工具：

- **[Free AI Router](https://github.com/fast1188/free-ai-router)** — 多 AI 模型自动 Fallback，永远不掉线
- **[CC Switch](https://github.com/fast1188/cc-switch)** — Windows 桌面一键切换 AI 客户端
- **[Console](https://github.com/fast1188/console)** — 全部项目的统一入口

---

> GitHub: [https://github.com/fast1188/ai-agent-skills](https://github.com/fast1188/ai-agent-skills)
> Gitee: [https://gitee.com/wudijia2026/ai-agent-skills](https://gitee.com/wudijia2026/ai-agent-skills)
