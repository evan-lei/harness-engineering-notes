# harness-engineering-notes

静态单页：**客户端 Harness Engineering 使用探索**（长文排版 + Mermaid 流程图）。

| 项目 | 说明 |
|------|------|
| 页面入口 | 仓库根目录 `index.html` |
| 源稿 | `客户端Harness Engineering 使用探索.md`（改版后可再用 Pandoc 生成正文后套模板） |
| 部署 | `git push` 到 `main` 后，**GitHub Pages**（根目录）自动发布 |

## 本地预览

直接用浏览器打开 `index.html`，或使用任意静态服务器。

## GitHub 仓库创建（首次）

1. GitHub → **New repository** → 名称建议 `harness-engineering-notes`，Public，**不要**勾选添加 README（本地已有）。
2. 本地（若尚未 `git init`）：

   ```bash
   cd /Users/user/Documents/harness-engineering-notes
   git init
   git add .
   git commit -m "Initial: Harness Engineering 使用探索"
   git branch -M main
   git remote add origin https://github.com/evan-lei/harness-engineering-notes.git
   git push -u origin main
   ```

3. 仓库 **Settings → Pages**：**Deploy from branch** → **main** → **/(root)**。

访问示例：`https://evan-lei.github.io/harness-engineering-notes/`（具体路径以仓库名为准）。

## 自定义子域名（可选）

在 DNS 提供商处为子域名添加 **CNAME** 指向 GitHub Pages（如 `evan-lei.github.io`），并在本仓库 **Settings → Pages → Custom domain** 中填写该子域名（与 [jiufu-fishing](https://github.com/evan-lei/jiufu-fishing) 配置方式一致）。

## 技术说明

- 正文由 **Pandoc (GFM)** 转换后嵌入模板；表格带横向滚动容器；代码块分区样式。
- 图表依赖 CDN：`mermaid@10`（需联网）。
