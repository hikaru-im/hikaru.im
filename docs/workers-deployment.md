# Cloudflare Workers（静态博客）

本分支基于 `staging/akari-fuwari-sync`，不修改当前 Cloudflare Pages 项目、域名或生产构建。

## 原理

Astro 在构建时生成静态页面和 Pagefind 索引，Workers Static Assets 直接托管 `dist`。**不添加 Astro SSR 适配器，也不创建 Worker JavaScript 入口。**

`wrangler.jsonc` 中 `name` 为独立测试 Worker `hikaru-blog-preview`。`assets.html_handling` 使用 `auto-trailing-slash` 以兼容 `trailingSlash: "always"` 的站点 URL；`not_found_handling` 使用 `404-page`，避免未知 URL 错误地返回首页。

## 本地或 CI 发布

```bash
corepack enable
pnpm install --frozen-lockfile
pnpm build
pnpm dlx wrangler deploy
```

Workers Builds Git 集成的配置：GitHub 仓库 `hikaru-im/hikaru.im`，分支 `deploy/workers-static-assets`，构建命令 `pnpm build`，部署命令 `pnpm dlx wrangler deploy`，根目录 `/`。建议在 Cloudflare 控制台绑定 GitHub 后启用自动构建，且先保持 `workers.dev` 测试域名，**不要绑定 `hikaru.im`**。

## 回归清单

- 首页、关于页面以及全部 7 篇文章的原有 URL
- 分类和标签旧地址（`/archive/category/`、`/archive/tag/`）
- 页面 CSS/图片加载、移动端、暗色主题、Swup 页面切换
- Giscus 评论（绑定 `hikaru-im/hikaru.im`，不应指向模板）
- `/rss.xml`、`/sitemap-index.xml`、`/pagefind/pagefind.js` 和搜索
- 未知页面应返回 404（如配置自定义 404 页面则展示该页面）

正式切换前：在 Worker 的测试域名完成浏览器回归、再规划 `hikaru.im` 域名映射；旧 Pages 项目暂时保留用于快速回滚。
