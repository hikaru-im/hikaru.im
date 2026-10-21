# Akari

基于 [Astro](https://astro.build) 开发的静态博客模板。

## ✨ 功能特性

- [x] 基于 Astro 和 Tailwind CSS 开发
- [x] 流畅的动画和页面过渡
- [x] 亮色 / 暗色模式
- [x] 自定义主题色和横幅图片
- [x] 响应式设计
- [x] 评论
- [x] 搜索
- [x] 文内目录

## 🚀 使用方法

1. 使用此模板[生成新仓库](https://github.com/hikaru-im/akari/generate)或 Fork 此仓库
2. 进行本地开发，Clone 新的仓库，执行 `pnpm install` 和 `pnpm add sharp` 以安装依赖
3. 通过配置文件 `src/config.ts` 自定义博客
4. 执行 `pnpm new-post <filename>` 创建新文章，并在 `src/content/posts/` 目录中编辑
5. 参考[官方指南](https://docs.astro.build/zh-cn/guides/deploy/)将博客部署至 Vercel, Netlify, GitHub Pages 等；部署前需编辑
   `astro.config.mjs` 中的站点设置

## ⚙️ 文章 Front matter

```yaml
---
title: My First Blog Post
published: 2023-09-09
description: This is the first post of my new Astro blog.
image: ./cover.jpg
tags: [ Foo, Bar ]
category: Front-end
draft: false
# lang: jp
---
```

## 🧞 指令

| Command                           | Action                            |
|:----------------------------------|:----------------------------------|
| `pnpm install` 并 `pnpm add sharp` | 安装依赖                              |
| `pnpm dev`                        | 在 `localhost:4321` 启动本地开发服务器      |
| `pnpm build`                      | 构建网站至 `./dist/`                   |
| `pnpm preview`                    | 本地预览已构建的网站                        |
| `pnpm new-post <filename>`        | 创建新文章                             |
| `pnpm astro ...`                  | 执行 `astro add`, `astro check` 等指令 |
| `pnpm astro --help`               | 显示 Astro CLI 帮助                   |
