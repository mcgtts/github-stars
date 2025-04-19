---
project: hacker-news
stars: 1628
description: |-
    一个基于 AI 的 Hacker News 中文播客项目，每天自动抓取 Hacker News 热门文章，通过 AI 生成中文总结并转换为播客内容。
url: https://github.com/ccbikai/hacker-news
---

# Hacker News 每日播报

一个基于 AI 的 Hacker News 中文播客项目，每天自动抓取 Hacker News 热门文章，通过 AI 生成中文总结并转换为播客内容。

---

预览地址: <https://hacker-news.agi.li>

订阅地址: <https://hacker-news.agi.li/rss.xml>

## 主要特性

- 🤖 自动抓取 Hacker News 每日热门文章
- 🎯 使用 AI 智能总结文章内容和评论
- 🎙️ 通过 Edge TTS 生成中文播报
- 📱 支持网页和播客 App 收听
- 🔄 每日自动更新
- 📝 提供文章摘要和完整播报文本

## 技术栈

- Next.js 应用框架
- Cloudflare Workers 部署和运行环境
- Edge TTS 语音合成
- OpenAI API 内容生成
- Tailwind CSS 样式处理
- shadcn-ui 组件库

## 工作流程

1. 定时抓取 Hacker News 热门文章
2. 使用 AI 生成中文摘要和播报文稿
3. 通过 Edge TTS 转换为音频
4. 存储到 Cloudflare R2 和 KV
5. 通过 RSS feed 和网页提供访问

## 本地开发

> 项目由一个 Worker 和 Web 程序组成，Worker 负责抓取数据，处理音频。使用了 Cloudflare 的 R2 存储、 KV 存储、工作流和浏览器呈现。
> Web 程序负责展示数据和提供 RSS 订阅。 Web 程序使用 Next.js 开发，可以看下 OpenNext 的 Cloudflare 适配器。

1. 安装依赖:

```bash
pnpm install
```

2. 配置环境变量:

```bash
# .dev.vars
NEXTJS_ENV=development
NEXT_STATIC_HOST=http://localhost:3000/static

# worker/.dev.vars
WORKER_ENV=dev
HACKER_NEWS_WORKER_URL=https://you-worker-url
HACKER_NEWS_R2_BUCKET_URL=https://your-bucket-url
OPENAI_API_KEY=your_api_key
OPENAI_BASE_URL=https://api.openai.com/v1
OPENAI_MODEL=gpt-4.1

```

3. 启动开发服务器:

```bash
# 开发工作流
pnpm dev:worker
# curl -X POST http://localhost:8787 # 手动触发工作流

# 开发 Web 页面
pnpm dev
```

> 注意：
>
> - 本地运行工作流时，Edge TTS 转换音频可能会卡住。建议直接注释该部分代码进行调试。
> - 由于合并音频需要使用 CloudFlare 的浏览器端呈现，不支持本地开发，需要远程调试。 可以使用 `npm run test` 进行测试。

## 部署

项目使用 Cloudflare Workers 部署:

1. 创建 R2 文件存储桶, 绑定域名后，修改 `NEXT_STATIC_HOST` 和 `HACKER_NEWS_R2_BUCKET_URL` 变量。
2. 创建 KV 存储空间
3. 修改 `wrangler.json` 中 KV 和 R2 的值
4. 使用 `wrangler` 脚手架配置线上环境的环境变量:

```bash
# 更新 Worker 的私有变量
wrangler secret put --cwd worker HACKER_NEWS_WORKER_URL # 绑定域名后，修改为绑定域名
wrangler secret put --cwd worker HACKER_NEWS_R2_BUCKET_URL
wrangler secret put --cwd worker OPENAI_API_KEY
wrangler secret put --cwd worker OPENAI_BASE_URL
wrangler secret put --cwd worker OPENAI_MODEL

# 更新 Web 程序的私有变量
wrangler secret put NEXT_STATIC_HOST # 绑定域名后，修改为绑定域名
```

```bash
# 记得恢复注释：wrangler.json 中的 workflows 相关配置
pnpm deploy:worker
pnpm deploy
```

## 贡献

欢迎提交 Issue 和 Pull Request!

## 赞助

1. [在 Telegram 关注我](https://t.me/miantiao_me)
2. [在 𝕏 上关注我](https://404.li/x)
3. [在 GitHub 赞助我](https://github.com/sponsors/ccbikai)

## 免责声明

本项目与 Hacker News 和 Y Combinator 没有任何关联。"Hacker News" 是 Y Combinator 的注册商标。

