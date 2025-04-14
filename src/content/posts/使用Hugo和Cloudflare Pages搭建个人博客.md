---
title: 使用Hugo和Cloudflare Pages搭建个人博客
published: 2024-08-07
description: ''
image: ''
tags: [ Hugo, 静态网站, Cloudflare Pages, Go ]
category: 技术分享
draft: false
---

## Hugo

[Hugo](https://gohugo.io/) 是一个用 Go 编写的快速静态网站生成器，构建速度极快（每个页面小于1毫秒），拥有大量现成主题，在开发过程中通过
live load 即时渲染更改，可以托管在任何平台，是一个理想的建站工具。

## 安装 Hugo

Windows

```powershell
winget install Hugo.Hugo.Extended
```

MacOS

```shell
brew install hugo
```

Linux

```shell
sudo apt-get install hugo
```

## 创建新项目

```shell
hugo new site my-hugo-site
```

```
cd my-hugo-site
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
```

## 创建 GitHub 仓库

访问 [repo.new](https://repo.new/)，创建新的 GitHub 存储库，并将其推送到 GitHub。

```shell
git add .
git git commit -m "first commit"
git remote add origin https://github.com/<your-gh-username>/<repository-name>
git push -u origin main
```

## 使用 Cloudflare Pages 进行部署

在 Cloudflare dashboard](https://dash.cloudflare.com/) 创建 Pager 应用程序，连接到 Git 选择刚才创建的 GitHub 仓库。

| 配置选项   | 值      |
|:-------|:-------|
| 生产分支   | main   |
| 框架预设   | Hugo   |
| 构建命令   | hugo   |
| 构建输出目录 | public |

使用更新的 Hugo 版本，设置环境变量，例如：

| 变量名称         | 值       |
|:-------------|---------|
| HUGO_VERSION | 0.131.0 |

完成部署配置后，点击**保存并部署**。
