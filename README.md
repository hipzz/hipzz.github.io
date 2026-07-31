# 读书笔记网站

纯静态、Markdown 驱动的读书笔记展示站。每篇笔记是一个 `.md` 文件，网页自动读取并渲染（支持标题、列表、引用、代码、**图片**等标准 Markdown）。

## 目录结构
- `index.html` —— 网站页面（列表 + 详情，纯前端渲染）
- `marked.min.js` —— 本地 Markdown 解析器（无需联网）
- `notes.json` —— 索引文件，**只列出每篇笔记的 `.md` 路径**
- `notes/` —— 读书笔记 Markdown 文件目录
- `assets/` —— 图片等静态资源（可选）
- `README.md` —— 本说明

## 如何新增一篇读书笔记

> 核心：写好一个 `.md` 文件，并在 `notes.json` 里登记它的路径即可。

1. 在 `notes/` 目录下新建一个 `.md` 文件，例如 `notes/my-book.md`。
   文件开头用 frontmatter 写元信息，下面是正文（标准 Markdown）：

   ````markdown
   ---
   title: 《书名》读书笔记
   author: 作者
   date: 2026-08-01
   tags: [标签1, 标签2]
   summary: 一句话摘要，显示在列表卡片上
   cover: assets/cover.png
   ---

   ## 核心观点
   正文支持 **加粗**、*斜体*、列表、引用等。

   > 金句引用。

   ![示意图](assets/my-book.png)
   ````

   frontmatter 字段说明：
   - `title` / `author` / `date`：展示用。
   - `tags`：数组，用于列表筛选（写成 `[a, b]` 或 `a, b` 均可）。
   - `summary`：列表卡片摘要。
   - `cover`：（可选）卡片封面图路径，如 `assets/cover.png`。

2. 打开 `notes.json`，在 `notes` 数组里加一行文件路径：
   ```json
   {
     "notes": [
       "notes/effective-executive.md",
       "notes/my-book.md"
     ]
   }
   ```

3. 提交（Commit）。GitHub Pages 几分钟后自动更新。

### 放图片
- 把图片放进仓库 `assets/` 目录。
- 在 `.md` 里用 `![说明](assets/xxx.png)` 或绝对路径 `![说明](/assets/xxx.png)` 引用。
- 也可直接引用外链图片 URL（如图床链接）。

### 在 GitHub 网页上直接操作（最省事）
进入仓库 → 在 `notes/` 下「Add file」上传 `.md`（或新建）→ 编辑 `notes.json` 登记 → 提交。无需本地环境。

### 本地预览
```bash
cd portfolio-site
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```
注意：必须经由 http 访问（不能直接双击用 file:// 打开），否则 `.md` / `notes.json` 会被浏览器拦截。

## 部署
已部署为 GitHub Pages 用户主页站（`https://<用户名>.github.io`），由 `main` 分支根目录发布。
