# Crispig.github.io

这是为 `Crispig` 从零创建的全新个人主页与博客。它不会读取、覆盖或依赖旧的 `Backup_Crispig.github.io`。

网站采用 GitHub Pages 原生支持的 Jekyll。主页排版参照 Ruiqi Zhong 的个人网站：800px 居中内容区、Lato 字体、顶部简介/照片双栏、蓝色链接和紧凑的研究条目；文章仍使用 Markdown 编写。

## 最先修改的内容

1. 编辑 `_config.yml`：站点标题、简介、头像和 GitHub 用户名。
2. 编辑 `index.html`：个人介绍、研究方向、精选项目和 Miscellaneous。
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
