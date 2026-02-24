# 个人博客网站

> 一个功能丰富、易于使用的个人博客系统

该项目是一个基于 Next.js 构建的现代化个人博客网站，支持博客发布、图片管理、项目展示、代码片段分享等多种功能。

## 1. 项目特点

- 🎨 现代化设计，响应式布局
- ✏️ 内置 Markdown 编辑器，支持图片上传
- 📁 分类管理博客内容
- 🖼️ 图片库功能，支持拖拽上传
- 📱 移动端适配
- 🌙 深色模式支持
- 🚀 快速部署流程

## 2. 安装

### 2.1 本地开发

```bash
# 安装依赖
pnpm i

# 启动开发服务器
pnpm dev
```

### 2.2 环境变量

项目使用以下环境变量进行配置：

```ts
export const GITHUB_CONFIG = {
	OWNER: process.env.NEXT_PUBLIC_GITHUB_OWNER || 'your-username',
	REPO: process.env.NEXT_PUBLIC_GITHUB_REPO || 'your-blog-repo',
	BRANCH: process.env.NEXT_PUBLIC_GITHUB_BRANCH || 'main',
	APP_ID: process.env.NEXT_PUBLIC_GITHUB_APP_ID || '-',
	ENCRYPT_KEY: process.env.NEXT_PUBLIC_GITHUB_ENCRYPT_KEY || 'your-encrypt-key',
	BLOGGERS_PASSWORD: process.env.NEXT_PUBLIC_GITHUB_BLOGGERS_PASSWORD || 'your-bloggers-password'
} as const

export const LOGIN_CONFIG = {
	USERNAME: process.env.NEXT_PUBLIC_LOGIN_USERNAME || 'your-login-username',
	PASSWORD: process.env.NEXT_PUBLIC_LOGIN_PASSWORD || 'your-login-password'
} as const
```

**说明**：
- `ENCRYPT_KEY`：用于加密敏感信息的密钥
- `BLOGGERS_PASSWORD`：博主访问密码
- `LOGIN_CONFIG`：网站后台登录账号密码

## 3. 部署

推荐使用 Vercel 进行部署，步骤如下：

1. 登录 Vercel 账号
2. 创建新项目，导入你的 GitHub 仓库
3. 无需特殊配置，直接点击部署
4. 等待部署完成（约 60 秒）

## 4. GitHub App 配置

为了使用前端编辑功能，需要配置 GitHub App：

### 4.1 创建 GitHub App

1. 进入 GitHub 个人设置 → Developer Settings
2. 点击 "New GitHub App"
3. 填写基本信息（名称和首页 URL 可随意填写）
4. 关闭 Webhook 功能
5. 授予仓库的 write 权限
6. 点击创建

### 4.2 生成私钥

1. 创建 App 后，生成并下载 **Private Key**
2. 复制页面上的 **App ID**

### 4.3 安装 App 到仓库

1. 进入 App 的安装页面
2. 选择授权当前博客仓库
3. 点击安装

### 4.4 配置环境变量

在 Vercel 项目设置中添加以下环境变量：

**GitHub 配置**：
- `NEXT_PUBLIC_GITHUB_OWNER`：你的 GitHub 用户名
- `NEXT_PUBLIC_GITHUB_REPO`：你的博客仓库名称
- `NEXT_PUBLIC_GITHUB_APP_ID`：之前复制的 App ID
- `NEXT_PUBLIC_GITHUB_ENCRYPT_KEY`：用于加密敏感信息的密钥
- `NEXT_PUBLIC_GITHUB_BLOGGERS_PASSWORD`：博主访问密码

**登录配置**：
- `NEXT_PUBLIC_LOGIN_USERNAME`：网站后台登录用户名
- `NEXT_PUBLIC_LOGIN_PASSWORD`：网站后台登录密码

添加后，手动触发一次重新部署使环境变量生效。

## 5. 使用指南

### 5.1 发布博客

1. 访问 `/write` 页面
2. 填写博客标题、内容和分类
3. 上传封面图片（可选）
4. 点击发布按钮
5. 等待部署完成后，刷新页面查看效果

### 5.2 管理图片

1. 访问 `/pictures` 页面
2. 点击上传按钮添加图片
3. 支持拖拽上传多张图片

### 5.3 配置网站

1. 访问首页，点击右上角的配置按钮
2. 可配置网站标题、描述、社交媒体链接等
3. 可自定义网站颜色主题

## 6. 项目结构

```
src/
├── app/             # 应用路由
│   ├── (home)/      # 首页相关组件
│   ├── blog/        # 博客页面
│   ├── write/       # 编辑器页面
│   ├── pictures/    # 图片库
│   └── share/       # 分享内容
├── components/      # 通用组件
├── lib/             # 工具函数
└── styles/          # 全局样式
```

## 7. 技术栈

- Next.js 14
- React 18
- TypeScript
- Tailwind CSS
- Markdown

## 8. 注意事项

- 网站前端编辑内容后，需要等待后台部署完成才能看到更新
- 图片上传建议先压缩，宽度不超过 1200px 以获得更好的加载性能
- 首次使用时，建议删除默认示例内容，添加自己的内容

## 9. 自定义开发

### 9.1 修改首页内容

首页内容位于 `src/app/(home)` 目录，可根据需要修改各个卡片组件。

### 9.2 添加新功能

可以在 `src/app` 目录下添加新的路由和页面，扩展网站功能。

---

## 项目来源

本项目基于 [YYsuni/2025-blog-public](https://github.com/YYsuni/2025-blog-public) 进行了大量修改和扩展，保留了原项目的基本结构和部分功能，同时添加了更多特性和改进。
