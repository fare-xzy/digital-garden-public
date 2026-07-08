---
title: Tags
publish: true
tags: [meta/index]
---

# Tags

回到 [[Home]] · 看 [[Maps of Content (MOCs)]]

<!-- 由 publish.py 汇总；手动维护一个稳定标签表更可靠 -->

| Topic | Backing folder | Note template |
|-------|----------------|---------------|
| Long-form note (default) | — | `Templates/Note.md` |
| Daily note | `Notes/` | `Templates/Daily.md` |
| Raw dump | `Inbox/` | _(no template; sweep.py will catch orphans later)_ |
| Curated, public | `Published/` | inherit `Note.md`, set `publish: true` |
| Image / attachment | `assets/` | — |
| Index / MOC pages | `Index/` | `Templates/Note.md`, `tags: [meta/index]` |
