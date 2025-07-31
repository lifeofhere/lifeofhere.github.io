# Jekyll Blog with Minimal Mistakes Theme

这是一个使用 Minimal Mistakes 主题的 Jekyll 博客，配置为自动部署到 GitHub Pages。

## 部署到 GitHub Pages

### 步骤 1: 创建 GitHub 仓库
1. 在 GitHub 上创建一个新的仓库
2. 仓库名可以是任意名称（如 `my-blog`）
3. 不要初始化 README、.gitignore 或 license

### 步骤 2: 更新配置
1. 编辑 `_config.yml` 文件
2. 更新以下字段：
   ```yaml
   title: "你的博客标题"
   email: "your-email@example.com"
   description: "你的博客描述"
   baseurl: "" # 如果仓库名不是 username.github.io，则设置为 "/repository-name"
   url: "https://username.github.io" # 替换为你的 GitHub Pages URL
   repository: "username/repository-name" # 替换为你的 GitHub 用户名和仓库名
   github_username: "your-github-username"
   ```

### 步骤 3: 推送到 GitHub
```bash
git remote add origin https://github.com/username/repository-name.git
git branch -M main
git push -u origin main
```

### 步骤 4: 启用 GitHub Pages
1. 进入 GitHub 仓库的 Settings 页面
2. 滚动到 "Pages" 部分
3. 在 "Source" 下选择 "GitHub Actions"
4. GitHub Actions 工作流将自动构建和部署你的站点

### 步骤 5: 访问你的网站
几分钟后，你的网站将在以下地址可用：
- `https://username.github.io/repository-name`（如果仓库名不是 username.github.io）
- `https://username.github.io`（如果仓库名是 username.github.io）

## 本地开发

```bash
# 安装依赖
bundle install

# 启动本地服务器
bundle exec jekyll serve
```

---

*最后更新时间: 2025-01-31 触发工作流测试*

然后访问 http://localhost:4000

## 添加新文章

在 `_posts` 目录下创建新的 Markdown 文件，文件名格式为：
```
YYYY-MM-DD-title.markdown
```

文件开头需要包含 Front Matter：
```yaml
---
layout: post
title: "文章标题"
date: 2025-01-31 12:00:00 +0800
categories: jekyll update
---
```

## 主题文档

更多关于 Minimal Mistakes 主题的配置选项，请参考：
https://mmistakes.github.io/minimal-mistakes/