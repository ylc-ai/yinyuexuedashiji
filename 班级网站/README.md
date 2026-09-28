# 国音26级音乐学 · 班级大事记时间轴

> 一个纯静态的班级大事记时间轴网站：记录我们一起走过的每一刻。同学打开网址即可查看，无需登录；管理员通过 Pages CMS 可视化更新内容，推送后 GitHub Pages 自动部署。

## ✨ 功能特性

- 时间轴左右交替展示（手机端自动变为单列），事件卡片滚动入场动画
- 分类筛选（学习 / 考试 / 活动 / 通知 / 其他）+ 关键词实时搜索，可组合使用
- 重要事件金色高亮脉冲、紧急事件红色闪烁边框并带「紧急」角标
- 顶部统计栏：总事件数 / 本月事件数 / 重要事件数（数字滚动动画）
- 友好日期格式：单日显示 `2026年11月15日 周日`；时间段事件支持日期区间（`2026年9月16日—17日`）与自定义文案（`2026年11月第一周`）
- 回到顶部浮动按钮、空结果友好提示、完整响应式适配

## 📁 文件结构

```
/
├── index.html                         主页面（内嵌全部 CSS 和 JS）
├── events.json                        事件数据源（CMS 编辑此文件）
├── assets/
│   └── logo.jpg                       校徽水印底图
├── pages.config.json                  Pages CMS 可视化后台配置
├── .github/
│   └── workflows/
│       └── deploy.yml                 GitHub Pages 自动部署工作流
└── README.md                          本说明
```

## 🚀 部署步骤（首次）

1. 在 GitHub 上新建一个**公开仓库**（例如 `class-memory`）。
2. 把本项目所有文件 push 到仓库的 `main` 分支：

   ```bash
   git init
   git add .
   git commit -m "init: 班级大事记时间轴"
   git branch -M main
   git remote add origin https://github.com/<你的用户名>/<仓库名>.git
   git push -u origin main
   ```

3. 打开仓库页面 → **Settings → Pages** → **Build and deployment → Source** 选择 **GitHub Actions**（不要选 Deploy from a branch）。
4. 回到 **Actions** 标签页，等待 “Deploy to GitHub Pages” 工作流运行完成（约 1 分钟）。
5. 部署成功后，在 Settings → Pages 顶部即可看到网址，形如：

   ```
   https://<你的用户名>.github.io/<仓库名>/
   ```

   把网址发给同学即可。

## ✏️ 日常更新事件（Pages CMS，推荐）

1. 先修改 `pages.config.json` 中的仓库地址，把
   `"repository": "YOUR_GITHUB_USERNAME/YOUR_REPO_NAME"`
   改成你自己的 `用户名/仓库名`，提交到 GitHub。
2. 打开 [app.pagescms.org](https://app.pagescms.org)，用 GitHub 账号登录并授权。
3. 选择本项目仓库（首次登录会列出你有权限的仓库）。
4. 进入「**事件管理**」，即可可视化地添加 / 编辑 / 删除事件：
   - `ID`：在当前最大 ID 基础上加 1，保持唯一；
   - `日期`：`YYYY-MM-DD`；跨多天的事件填**开始日期**，并在标题里注明范围（如「艺术实践周（10月12日—25日）」）；
   - `分类`：学习 / 考试 / 活动 / 通知 / 其他；
   - `重要程度`：普通 `normal` / 重要 `important`（金色）/ 紧急 `urgent`（红色）。
5. 点击 **Save / Publish** → 内容会自动提交到 `main` 分支 → GitHub Actions 自动重新部署。
6. 等待十几秒，让同学刷新页面即可看到最新内容（如看到旧内容，按 `Ctrl + F5` 强制刷新缓存）。

> 也可以直接在 GitHub 网页上编辑 `events.json`，或在本地修改后 push，效果相同。注意保持 JSON 格式正确（字符串用英文双引号、不要留多余逗号）。

## 🔧 本地预览

页面使用 `fetch('./events.json')` 读取数据，**不能直接双击 `index.html` 打开**（`file://` 协议会被浏览器拦截），需要用本地 HTTP 服务器：

**方式一：Python（推荐，macOS / Linux 自带，Windows 需安装 Python）**

```bash
# 在项目根目录执行
python3 -m http.server 8000
# Windows 上如果 python3 不识别，改用：
python -m http.server 8000
```

然后浏览器访问 <http://localhost:8000>。

**方式二：VS Code**

安装 “Live Server” 扩展，右键 `index.html` → “Open with Live Server”。

## 📝 自定义

- 修改班级名称 / 标语：编辑 `index.html` 中 `<header class="hero">` 里的文字。
- 修改主题色：调整 `index.html` 顶部 `:root` 中的 CSS 变量。

## 📄 开源说明

仅供本班学习交流使用。
