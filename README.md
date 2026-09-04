# Crispig.github.io

这是为 `Crispig` 从零创建的全新个人主页与博客。它不会读取、覆盖或依赖旧的 `Backup_Crispig.github.io`。

网站采用 GitHub Pages 原生支持的 Jekyll。主页排版参照 Ruiqi Zhong 的个人网站：800px 居中内容区、Lato 字体、顶部简介/照片双栏、蓝色链接和紧凑的研究条目；文章仍使用 Markdown 编写。

## 最先修改的内容

1. 编辑 `_config.yml`：站点标题、简介、头像和 GitHub 用户名。
2. 编辑 `index.html`：个人介绍、研究方向、论文和精选项目。
3. 将示例文章 `_posts/2026-07-19-welcome.md` 改写为自己的内容，或直接删除。

当前头像保存在 `assets/images/profile.png`。如需更换，请把新照片放到 `assets/images/profile.jpg`，再将 `_config.yml` 中的 `avatar` 改成：

```yaml
avatar: "/assets/images/profile.jpg"
```

## 写一篇新文章

在 `_posts` 中新建 `YYYY-MM-DD-title.md`：

```markdown
---
layout: post
title: "文章标题"
date: 2026-07-19 12:00:00 +0800
categories: [AI, Notes]
description: "显示在首页和文章列表中的一句简介。"
---

这里开始使用 Markdown 写正文。
```

提交后，文章会自动出现在首页的 Recent Writing 和 `/blog/` 归档页。

## 发布到 GitHub Pages

先在 GitHub 创建一个全新的公开仓库，名称必须为 `Crispig.github.io`。不要重命名或修改旧备份仓库。

然后在本目录执行：

```bash
git add .
git commit -m "Create new personal website"
git remote add origin https://github.com/Crispig/Crispig.github.io.git
git push -u origin main
```

进入新仓库的 `Settings → Pages`，选择：

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

发布地址将是 <https://crispig.github.io/>。

## 可选：本地预览

安装 Ruby 和 Bundler 后运行：

```bash
bundle install
bundle exec jekyll serve
```

然后打开 <http://127.0.0.1:4000/>。

## 访客世界地图与访问统计

已接入本站专属的 MapMyVisitors **Map Widget**，在主页、博客列表和文章底部显示同一张访客地图，让直接进入文章的访问也能计入。配置已启用，发布后开始记录；普通本地预览不发送统计请求。地图采用白色背景与自动宽度，禁用 JavaScript 时使用服务提供的图片地图。

本站公开统计页：<https://mapmyvisitors.com/web/1c815>。

### 配置与更换

1. 打开 <https://mapmyvisitors.com/add>，输入 `https://crispig.github.io/`，按页面提示生成本站的 **Map Widget**。选择自动宽度（如果服务提供此选项）；建议白色背景、浅灰陆地和蓝色访客点。
2. 如需更换地图，将服务生成的完整嵌入代码替换到 `_includes/visitor-map-embed.html`。保留原始 script ID 和网站专属 ID，资源地址使用 `https://`；图片备用代码放在 `<noscript>` 中，避免同一次访问同时加载两种统计方式。不要使用其他网站或演示地图的代码，也不要填写账号密码或私密 API 密钥。
3. 在 `_config.yml` 中将 `visitor_map.enabled` 改为 `true`。将服务提供的本站公开统计页地址填入 `visitor_map.stats_url`，即可显示 “View visitor statistics” 链接；留空则隐藏该链接。
4. 将修改发布到 GitHub Pages。地图脚本只在 Jekyll 的 `production` 环境中加载，普通本地预览不计数。GitHub Pages 使用 production；如果自行构建，需使用 `JEKYLL_ENV=production bundle exec jekyll build`。

### 数据与验证

- 服务按 IP 估算大致地区，无法据此得知访问者的姓名或精确住址；VPN 和代理可能影响位置。
- 数据从启用并发布后开始积累，不能恢复接入前的访问记录。访问趋势和国家／城市统计由第三方服务保存，具体展示以服务当前功能为准。
- 上线后实际打开主页或文章，确认地图显示，再打开本站统计页确认新增访问。服务更新可能有延迟；广告拦截器或网络不可达会使记录缺失，因此统计不等于全部访问。
- 地图加载会向 MapMyVisitors 发送请求，服务可获得 IP 等请求信息；页面底部附有简短说明与服务链接。
- 若地图加载失败，正文仍可阅读；已配置的统计页链接仍可使用。将 `visitor_map.enabled` 改回 `false` 可移除地图及其统计请求。
