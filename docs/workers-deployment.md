# Cloudflare Workers 静态部署

## 当前部署拓扑

- 现有正式 Worker：`hikaru-im`，绑定 `hikaru.im`；Worker 的 GitHub 构建监听 `main`。
- 本配置 `wrangler.jsonc` 的名称必须与现有 Worker **完全一致**，避免创建第二个 Worker。
- Astro 采用静态站点生成，不使用 Cloudflare SSR 适配器，Wrangler 上传 `dist` 静态资源。
- Workers Builds 的生产与预览根目录均为 `/`，构建命令 `pnpm run build`；生产部署为 `npx wrangler deploy`，预览为 `npx wrangler preview`。

## 流程

1. PR #38 完成新版主题校验，PR #39（本 PR）以 #38 分支为目标，仅准备配置。
2. 先合并 PR #39 至 `staging/akari-fuwari-sync`，在主 PR 中统一构建验证；该操作不会改变 `main` 或生产 Worker。
3. 通过源码与预览构建检查后，将 PR #38 合入 `main` 才会触发正式 Worker 自动部署；这一步影响线上网站，需在合并前完成回归确认。
4. 生产部署之后核对首页、全部 7 篇文章、旧分类/标签 URL、关于页面、Giscus、Pagefind、RSS、Sitemap、404 页面和移动端。

## 命令

```bash
corepack enable
pnpm install --frozen-lockfile
pnpm run build
npx wrangler deploy
```

### 注意

- 不需要新的 Pages 项目，也不应重建 Worker。
- `wrangler.jsonc` 配置 `404-page`，未知 URL 应返回 404，而非首页。
- PR #39 的 CI 通过不等于 Workers 预览地址可访问；需单独确认 Workers Builds 预览部署结果。
- 任何无法完成的交互测试不得标记为通过。
