# 🚀 AI Team 落地页 - GitHub Pages 部署指南

**项目**: AI Team Landing Page  
**目标**: 部署到 `https://keepcodinglife.github.io`

---

## ✅ 部署步骤

### 第一步：创建 GitHub 仓库

1. 登录 GitHub (keepcodinglife@outlook.com)
2. 访问 https://github.com/new
3. 填写信息：
   - **Repository name**: `keepcodinglife.github.io` ⚠️ 必须用这个名称才能作为主页
   - **Description**: `AI Team - 你的智能协作小队`
   - **Public**: ✅ 选中
   - **Add a README file**: ❌ 不选（我们已有代码）
4. 点击 **Create repository**

### 第二步：推送代码到 GitHub

在终端执行以下命令（在项目目录 `~/.openclaw/workspace/ai-team/`）：

```bash
# 进入项目目录
cd ~/.openclaw/workspace/ai-team

# 初始化 git（如果还没有）
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit: AI Team landing page"

# 添加远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/keepcodinglife/keepcodinglife.github.io.git

# 推送到 main 分支
git branch -M main
git push -u origin main
```

### 第三步：启用 GitHub Pages

1. 进入仓库 **Settings** → **Pages**
2. **Build and deployment**:
   - Source: **GitHub Actions** (推荐，已配置自动部署)
3. 等待部署完成（约 1-2 分钟）

### 第四步：验证部署

访问：https://keepcodinglife.github.io

---

## 🔄 后续更新

每次修改代码后：

```bash
git add .
git commit -m "更新说明"
git push
```

GitHub Actions 会自动重新部署！

---

## 📁 项目文件说明

```
ai-team/
├── landing-page.html      # 主落地页
├── vercel.json            # Vercel 配置（可保留）
├── .github/
│   └── workflows/
│       └── deploy.yml     # GitHub Actions 部署配置
├── README.md              # 团队介绍
└── ...                    # 其他团队成员目录
```

---

## 🎯 访问地址

- **主页**: https://keepcodinglife.github.io
- **仓库**: https://github.com/keepcodinglife/keepcodinglife.github.io

---

## ⚠️ 常见问题

### 1. 页面显示 404
- 等待 2-3 分钟，GitHub Pages 需要时间构建
- 确认推送到了 `main` 分支

### 2. 样式错乱
- 检查 HTML 中的 CSS/JS 路径是否正确
- 确保所有资源文件都已提交

### 3. 自定义域名
如需绑定自己的域名，在 **Settings → Pages → Custom domain** 中设置

---

*部署由 GitHub Actions 自动完成，无需手动操作*
