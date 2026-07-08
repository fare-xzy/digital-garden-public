---
title: README
publish: true
tags: [meta/index, meta/about]
---

# Digital Garden

> 个人双链知识库。原子化笔记，双向链接，长期迭代，没有"完成"。

**打开方式**：当作 [Obsidian](https://obsidian.md/) vault。

## 这是什么

- 一个本地优先的 markdown vault，`publish:` 标记控制每篇笔记是否对外发布
- 一对最小 Python 工具：**发布**（`publish.py` / `make publish`）和**整理孤立簇**（`sweep.py` / `make sweep`）
- 一套完全 stdlib 的代码，零外部依赖，零 npm / 零 docker

## 快速上手

```bash
make install   # 第一次：起 venv + 装 pytest
make test      # 跑单测 (应 11 全过)
make publish   # 编译 publish:true 的笔记到 dist/
make sweep     # 列出"同 tag 但没外链"的孤立笔记
make lint      # 检查每篇笔记是否有 frontmatter
```

## 目录约定

| 路径 | 用途 |
|------|------|
| `Index/` | vault 自身的索引页：`Home` / `Tags` / `Maps of Content` / 各主题 MOC |
| `Notes/` | 长文笔记（默认目的地） |
| `Notes/daily` | 日记（`Cmd+D` 自动建到这里） |
| `Inbox/` | 未整理的原材料，每周 `make sweep` |
| `Published/` | 已经决定要公开的内容 |
| `Templates/` | Obsidian 模板（`Note.md` / `Daily.md`） |
| `assets/` | 图片 / 附件 |
| `dist/` | `make publish` 产物（`dist/` 在 `.gitignore`，不入库） |
| `.scripts/` | publish / sweep / tests / lint 脚本 |
| `.obsidian/` | Obsidian 配置，与 vault 一起搬 |

完整对照表 + tag 字典见 [[Index/Tags]]。

## 如何写笔记

1. `Cmd+N` 新建一篇 → 默认套 `Templates/Note.md`
2. 改 frontmatter：`title:` / `date:` / `tags:` / `publish: true|false` / `status:`
3. 主体用 markdown；双向链接用 `[[另一篇笔记]]` 或 `[[Note|显示文字]]`
4. 写完跑 `make publish`（公开稿）或 `make sweep`（找孤立）

更详细的"为什么要这样"见 [[Notes/getting-started|Getting Started]]。

## 公开发布

```bash
make publish           # 编译到 dist/
```

`dist/` 是能直接丢给任何静态站服务（Netlify / Cloudflare Pages / GitHub Pages）
的产物。把 `dist/` 推到一个 `username.github.io` 子 repo 就能上线。

## 整体视图

```
Digital Garden/
├── .obsidian/                # Obsidian 自己的配置
├── .scripts/                 # publish/sweep/lint
├── .venv/                    # 本地虚拟环境（不入库）
├── assets/                   # 图片 / 附件
├── dist/                     # 编译产物（不入库）
├── Index/                    # 索引与 MOC
├── Inbox/                    # 原材料
├── Notes/                    # 主要笔记
│   └── daily/                # 日记（Cmd+D）
├── Published/                # 公开内容
├── Templates/                # Obsidian 模板
├── tests/                    # 单测
├── IDEA.md                   # 立项说明
├── Makefile                  # 入口：`make help`
├── README.md                 # 你正在读的这一篇
├── publish.py                # 编译脚本
└── sweep.py                  # 孤立簇扫描
```

## License

笔记内容以实际发布页的声明为准。
代码部分（`publish.py` / `sweep.py` / tests）以 MIT 发布。
