# Jekyll 博客双仓库部署指南

## 架构说明

本项目采用双仓库架构：
- **blog-source**（私有仓库）：存放源代码、配置文件和文章
- **lifeofhere.github.io**（公开仓库）：存放构建后的静态网站文件

## 部署流程

### 1. 创建 Personal Access Token

1. 访问 GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. 点击 "Generate new token (classic)"
3. 设置以下权限：
   - `repo`（完整仓库访问权限）
   - `workflow`（工作流权限）
4. 复制生成的 token

### 2. 配置仓库 Secrets

在 **blog-source** 私有仓库中：
1. 进入 Settings → Secrets and variables → Actions
2. 添加新的 Repository secret：
   - Name: `PERSONAL_ACCESS_TOKEN`
   - Value: 刚才创建的 Personal Access Token

### 3. 确保目标仓库存在

确保 `lifeofhere/lifeofhere.github.io` 仓库已创建并设为公开。

### 4. 启用 GitHub Pages

在 **lifeofhere.github.io** 仓库中：
1. 进入 Settings → Pages
2. Source 选择 "Deploy from a branch"
3. Branch 选择 "main"
4. Folder 选择 "/ (root)"

## 工作流说明

当向 `blog-source` 仓库的 `main` 分支推送代码时：

1. **构建阶段**：
   - 检出源代码
   - 设置 Ruby 3.2 环境
   - 安装依赖（bundle install）
   - 构建 Jekyll 站点

2. **部署阶段**：
   - 将构建好的 `_site` 目录推送到 `lifeofhere.github.io` 仓库
   - 触发 GitHub Pages 自动部署

## 本地开发

```bash
# 安装依赖
bundle install

# 本地预览
bundle exec jekyll serve

# 访问 http://127.0.0.1:4000
```

## 发布文章

1. 在 `_posts` 目录下创建新文章
2. 提交并推送到 `blog-source` 仓库
3. GitHub Actions 自动构建并部署到 `lifeofhere.github.io`
4. 几分钟后可在 `https://lifeofhere.github.io` 访问

## 故障排除

### 部署失败
- 检查 `PERSONAL_ACCESS_TOKEN` 是否正确设置
- 确认 token 有足够的权限
- 查看 Actions 日志获取详细错误信息

### 页面不更新
- 检查 `lifeofhere.github.io` 仓库是否收到了新的提交
- 确认 GitHub Pages 设置正确
- 等待几分钟让 GitHub Pages 完成部署

## 优势

✅ **源码私有**：博客源码保持私有，保护配置和草稿  
✅ **自动部署**：推送即部署，无需手动操作  
✅ **免费托管**：使用 GitHub Pages 免费托管  
✅ **版本控制**：完整的版本历史和回滚能力  
✅ **自定义域名**：支持绑定自定义域名