---
name: harness-engineering-notes
description: Manage the 工程笔记站 (notes.evan-minho.com). Use when the user wants to add a new note, update content, fix layout, upload images, or deploy changes to the harness-engineering-notes repo.
---

# 工程笔记站 管理指南

## 站点信息

| 项目 | 值 |
|------|-----|
| 公开地址 | `https://notes.evan-minho.com` |
| GitHub Pages 备用 | `https://evan-lei.github.io/harness-engineering-notes` |
| GitHub 仓库 | `https://github.com/evan-lei/harness-engineering-notes` |
| 本地工作目录 | `/Users/user/Documents/harness-engineering-notes` |
| GitHub 用户名 | `evan-lei` |

**部署方式**：`git push` 到 GitHub main 分支后，GitHub Pages 自动部署，约 30 秒生效。

> ⚠️ GitHub Token 和 COS 密钥统一存在 `~/.cursor/skills/evan-lei-github-pages/SKILL.md`，本文件不重复存储。

---

## 目录结构

```
harness-engineering-notes/
├── index.html                              # 首页（笔记卡片列表）
├── CNAME                                   # notes.evan-minho.com
├── README.md
├── SKILL.md                                # 本文件（已推送至 GitHub）
├── harness/
│   └── index.html                          # 客户端 Harness Engineering 使用探索
└── 客户端Harness Engineering 使用探索.md   # 源文档（Markdown 存档）
```

---

## 推送到 GitHub

Token 见 `~/.cursor/skills/evan-lei-github-pages/SKILL.md`。

```bash
cd /Users/user/Documents/harness-engineering-notes
git remote set-url origin https://evan-lei:<TOKEN>@github.com/evan-lei/harness-engineering-notes.git
git add .
git commit -m "描述改动"
git push origin main
git remote set-url origin https://github.com/evan-lei/harness-engineering-notes.git
```

---

## 腾讯云 COS（图片存储）

| 字段 | 值 |
|------|----|
| Bucket | `notes-1256297898` |
| 地域 | `ap-beijing` |
| SecretId / SecretKey | 见 `~/.cursor/skills/evan-lei-github-pages/SKILL.md` |
| 公开 Base URL | `https://notes-1256297898.cos.ap-beijing.myqcloud.com/` |

已上传素材：
- `img1.png` — 三个概念嵌套关系图（Harness Engineering 笔记）
- `img2.png` — 层次结构图（Harness Engineering 笔记）

上传新图片前先压缩，命令见 evan-lei-github-pages SKILL。

---

## 新增笔记流程

1. 新建子目录：`mkdir -p /Users/user/Documents/harness-engineering-notes/<笔记名>`
2. 参考 `harness/index.html` 创建笔记页（深色主题 + 左侧 TOC + Mermaid）
3. 如有外链图片：下载 → 压缩 → 上传 `notes-1256297898` COS → 替换 HTML 内的 `src`
4. 在根目录 `index.html` 的 `.cards` 里新增一张 `.card`
5. 更新 `README.md` 的笔记列表表格
6. 推送（见上方推送命令）

---

## 更新已有笔记流程

1. 编辑对应 `<笔记名>/index.html`
2. 如源文档有改动，先更新 `.md`，再用 Pandoc 转 HTML 后嵌入：
   ```bash
   pandoc "<笔记名>.md" --from markdown --to html5 --no-highlight -o /tmp/body.html
   ```
3. 推送

---

## DNS 配置（已完成，勿重复操作）

- 域名 `evan-minho.com` 由 **Cloudflare** 管理
- CNAME 记录：`notes` → `evan-lei.github.io`（DNS only，灰色云朵）
- 仓库根目录 `CNAME` 文件内容：`notes.evan-minho.com`

---

## 换电脑时恢复

1. Clone 仓库：
   ```bash
   git clone https://github.com/evan-lei/harness-engineering-notes.git
   ```
2. 复制 SKILL 到 Cursor（从仓库复制，再补入密钥）：
   ```bash
   mkdir -p ~/.cursor/skills/harness-engineering-notes
   cp /Users/user/Documents/harness-engineering-notes/SKILL.md \
      ~/.cursor/skills/harness-engineering-notes/SKILL.md
   ```
3. GitHub Token 和 COS 密钥从 `evan-lei-github-pages` 仓库的 `GITHUB-PAGES-SKILL.md` 获取（仅含占位符），真实密钥需重新生成：
   - GitHub Token：`https://github.com/settings/tokens/new`（勾选 `repo`）
   - COS 密钥：`https://console.cloud.tencent.com/cam/capi`
   - 更新后写入 `~/.cursor/skills/evan-lei-github-pages/SKILL.md`

---

## 注意事项

- 单文件严禁超过 25MB（GitHub Pages 限制），图片必须放 COS
- 不要把图片/视频提交进 git
- 笔记页设计规范：深色主题（`#0f1117` 背景）、左侧粘性 TOC、Mermaid.js 图表
- Mermaid 初始化：`mermaid.initialize({ startOnLoad: true, theme: 'dark' })`
- 外链图片必须先传到 COS，不依赖第三方外链（外链随时失效）
