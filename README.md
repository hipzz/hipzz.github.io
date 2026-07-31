# 读书笔记网站

一个纯静态、数据驱动的读书笔记展示站。网页从 `notes.json` 读取笔记并自动渲染，无需构建工具。

## 目录结构
- `index.html` —— 网站页面（列表 + 详情，纯前端渲染）
- `notes.json` —— 读书笔记数据源（**新增内容只改这里**）
- `README.md` —— 本说明

## 如何新增一条读书笔记

> 这是本站点「后续新增内容」的唯一入口：不动 `index.html`，只往 `notes.json` 追加一条记录。

1. 打开仓库里的 `notes.json`。
2. 在数组 `[ ... ]` 里新增一个对象（参考已有条目），字段如下：

```json
{
  "id": "unique-id-here",
  "title": "《书名》读书笔记",
  "author": "作者",
  "date": "2026-08-01",
  "tags": ["标签1", "标签2"],
  "summary": "一句话摘要，显示在列表卡片上",
  "content": "正文第一段。\n\n正文第二段（用空行 + \\n\\n 分段）。"
}
```

字段说明：
- `id`：唯一标识，英文/数字/短横，不能和已有重复（用于详情页锚点）。
- `title` / `author` / `date`：展示用，自由填写。
- `tags`：字符串数组，用于列表筛选。
- `summary`：列表卡片摘要。
- `content`：正文。用 `\n\n` 分隔段落；支持纯文本即可。

3. 提交（Commit）改动。GitHub Pages 会在几分钟内自动更新。

### 在 GitHub 网页上直接改（最省事）
进入仓库 → 点开 `notes.json` → 右上角铅笔图标编辑 → 保存提交。无需本地环境。

### 本地预览
```bash
cd portfolio-site
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```
注意：必须经由 http 访问（不能直接双击用 file:// 打开），否则 `notes.json` 会被浏览器拦截。

## 部署
本目录已部署为 GitHub Pages 用户主页站（`https://<用户名>.github.io`），由 `main` 分支根目录发布。
