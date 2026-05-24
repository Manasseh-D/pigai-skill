# 批改网AI写作助手

让 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 通过 Playwright MCP 操作[批改网](https://www.pigai.org)平台，自动登录、搜索作业、撰写作文、提交批改并迭代优化至目标分数。

## 功能介绍

- **自动写作文**：AI 帮你根据题目要求自动撰写英语作文，无需手动构思
- **智能修改**：根据批改网的评分反馈自动针对词汇、句子、篇章结构、内容连贯性四个评分维度分别改进
- **灵活目标**：支持自定义目标分数

## 目录

- [使用需求](#使用需求)
- [使用指南](#使用指南)
- [安装](#安装)
- [注意事项](#注意事项)

## 使用需求

### ⚠️ 必须安装 Claude Code 和 Playwright MCP

本工具依赖 **Claude Code** 和 **Playwright MCP**。如果尚未下载安装，可参考笔者发布在微信公众号 **南医春华秋实** 中的推文：

> **《医学生AI副手：Claude Code搭建分享》**

### Token 按量计费

Claude Code 按 token 消耗计费，参考费用：

- 实测在**无参考文章**下使用 **DeepSeekV4-Pro**（`/effort xhigh`）完成一篇作文并迭代至 95 分，花费约 **1RMB**

## 使用指南

推荐使用方式：

1. **新建一个文件夹**，按照上方[安装](#安装)方式将仓库文件下载到该文件夹中
2. 在该文件夹中打开终端，以任意模式启动 Claude Code（若想全自动运行，建议以 **bypass permissions** 模式启动）：

   ```bash
   claude --dangerously-skip-permissions
   ```

3. 告诉 CC 批改网作业号、账号、密码以及目标分数（无要求则默认 94 分），开始运作后等待结果即可

## 安装

### 方式一：一行命令

打开你的 Claude Code，告诉它：

```
帮我安装这个 skill：https://github.com/Manasseh-D/pigai-skill
```

Claude Code 会自动克隆仓库并完成配置。

### 方式二：Git 克隆（推荐）

1. 新建一个空文件夹，在其中打开终端

**Windows（PowerShell）：**

```powershell
git clone https://github.com/Manasseh-D/pigai-skill.git .
```

**macOS / Linux：**

```bash
git clone https://github.com/Manasseh-D/pigai-skill.git .
```

### 方式三：手动下载

1. 点击仓库页面 **Code → Download ZIP**，解压到本地文件夹

## 注意事项

1. **模型选择**：建议使用能力更强的模型（如 DeepSeekV4-Pro、Claude Opus 等），可以加快完成速度并降低重复提交次数

2. **AI 检测**：批改网有 AI 生成检测，建议在 prompt 中要求 AI 模拟学生写作风格，适当加入个性化表达和少量非关键性错误。或者和别的去ai skill合用

3. **缓存文件**：运行中产生的 `.playwright-mcp` 文件夹是 MCP 运行时的缓存文件，可定期删除以节省 token

