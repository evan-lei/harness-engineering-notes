# harness-engineering-notes

VAS 团队 AI 辅助开发工程笔记，记录从 Lua AI 到 Native AI、从 Prompt Engineering 到 Harness Engineering 的实践探索。

| 地址 | 说明 |
|------|------|
| 🌐 [notes.evan-minho.com](https://notes.evan-minho.com) | 自定义域名，**优先用这个** |
| [evan-lei.github.io/harness-engineering-notes](https://evan-lei.github.io/harness-engineering-notes) | GitHub Pages 备用 |

---

## 笔记列表

| 笔记 | 目录 | 简介 |
|------|------|------|
| 客户端 Native AI使用探索-Harness Engineering | `harness/` | 从 Prompt → Context → Harness 的完整演进，含 SKILL+、CCD、Hooks 全套实践 |
| 客户端 Native AI使用探索-Context Engineering | `context-engineering/` | Rule → Code Graph → Agent Skill+Rules 协同方案，聚焦原生开发 AI 上下文传递 |
| 客户端 Lua AI 使用探索-RTCC | `rtcc/` | 模板+Rules+指令+CCD 四层体系（RTCC），以及 RTCC Pro 智能参考代码搜索与模板沉淀 |

---

## 目录结构

```
harness-engineering-notes/
├── index.html                                        # 首页（笔记列表入口）
├── CNAME                                             # 自定义域名 notes.evan-minho.com
├── README.md
├── harness/
│   └── index.html                                    # 客户端 Native AI使用探索-Harness Engineering
├── context-engineering/
│   └── index.html                                    # 客户端 Native AI使用探索-Context Engineering
├── rtcc/
│   └── index.html                                    # 客户端 Lua AI 使用探索-RTCC
└── 客户端Harness Engineering 使用探索.md             # 源文档（Markdown 存档）
```

---

## 新增笔记

1. 在根目录新建子目录：`mkdir -p <笔记名>`
2. 创建 `<笔记名>/index.html`（参考 `harness/index.html` 的模板）
3. 在根目录 `index.html` 的 `.cards` 里新增一个 `.card`
4. 更新本 `README.md`
5. 提交推送（GitHub Pages 自动部署）：
   ```bash
   git add .
   git commit -m "add <笔记名>"
   git push origin main
   ```

## 部署说明

- **托管**：GitHub Pages（`main` 分支根目录）
- **域名**：Cloudflare DNS → CNAME `notes` → `evan-lei.github.io`，DNS only（灰色云朵）
- **推送**：使用 Personal Access Token，详见 `evan-lei.github.io` 仓库的 `GITHUB-PAGES-SKILL.md`
