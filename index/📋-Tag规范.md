---
title: Tag 使用规范
date: 2026-07-01
updated: 2026-07-30
tags:
  - type/index
aliases:
  - tag规范
---

# Tag 使用规范

轻量约定：**目录管大类，搜索管定位，tag 只做可选补充。**

## 目录分工

| 目录 | 用途 |
|------|------|
| `index/` | 首页、规范（导航与元信息） |
| `notes/` | 活跃方案、迁移总结、进行中材料（仅工作笔记，扁平） |
| `archive/guides/` | **指南 / SOP / 可复用手册**（不按项目拆子目录） |
| `archive/<topic>/` | 大型专题归档（≥4 篇，含归档说明） |
| `archive/misc/` | 小主题散档（≤3 篇，不建子目录） |
| `archive/county-resident/` | 正式需求：常驻区 County Resident（目前唯一项目归档） |
| `clippings/` | 外部摘录、工具介绍 |
| `study/` | 技术学习 |
| `work/daily/` · `work/weekly/` | 时间类便签 |
| `scripts/` | 开发/测试脚本（不进归档） |

## 放哪里（快速判断）

| 文档性质 | 放哪 |
|----------|------|
| 首页、规范、导航入口 | `index/` |
| 可复用指南、接入手册、操作 SOP | `archive/guides/` |
| 某次迁移/方案总结、还在改 | `notes/` |
| 正式需求已沉淀（当前仅常驻区） | `archive/county-resident/` |
| 基本是摘录、很少改 | `clippings/` |

## 归档约定

1. 指南统一进 `archive/guides/`，不要为 NLP / SystemServer 等各建目录
2. 正式需求结项后进 `archive/<project>/`；当前仅 `county-resident`
3. 小主题（≤3 篇）归档到 `archive/misc/`，不建子目录；≥4 篇才建专题目录
4. 尽量不改文件名，保留 wikilink
5. 入口：[[指南索引]] · [[常驻区County归档说明]]

## Tag 规则

- **默认不打 tag**，靠文件名和搜索即可
- 需要按项目筛选时，可加 `project/xxx`（可选，0～1 个）

### `project/` 受控词表

| Tag | 含义 |
|-----|------|
| `project/gnss` | GNSS / 定位 / NLP |
| `project/residence` | 常驻地识别（HOME/WORK） |
| `project/tran-system` | TranSystemServer / Harness |

### 时间类笔记（模板自动）

| Tag | 用途 |
|-----|------|
| `type/daily` | 每日便签 |
| `type/weekly` | 工作周记 |
| `type/index` | 首页、规范 |
| `type/kanban` | 看板 |

## 已废弃（不再使用）

- `area/*`、`type/guide`、`type/plan`、`tool/*`、`topic/*`
- Property：`doc-type`、`project`、`platform`、`status`（与 tag 重复）

## Dataview 示例

```dataview
LIST
FROM "archive/guides"
SORT file.name ASC
```

```dataview
LIST
FROM "archive/county-resident"
SORT file.name ASC
```
