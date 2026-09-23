# CLAUDE.md

本目录是 Obsidian 个人知识库（vault），不是软件项目，没有构建系统、CI/CD 或测试套件。

## 目录结构

| 目录 | 用途 |
| --- | --- |
| `index/` | 首页、规范、导航入口（首页/笔记总览/配置指南） |
| `clippings/` | 收集的片段（文章、教程、笔记转录） |
| `kanban/` | 个人任务看板 |
| `work/daily/` | 每日便签（按年月组织） |
| `work/weekly/` | 工作周记（按年组织） |
| `study/` | 技术学习笔记（Java 等） |
| `notes/` | 活跃工作笔记（仅笔记类文档，扁平） |
| `archive/guides/` | 可复用指南 / SOP（见 `指南索引.md`） |
| `archive/<topic>/` | 大型需求/专题归档（含归档说明） |
| `scripts/` | 开发辅助脚本（非 Obsidian 笔记） |
| `resource/templates/` | 笔记模板（Templater） |
| `resource/base/` | 数据库视图 |
| `resource/canvas/` | 白板画布 |
| `resource/excalidraw/` | Excalidraw 图表 |
| `resource/attachments/` | 附件（按笔记名分目录，如 `attachments/<笔记名>/`） |

## 导航入口

| 入口      | 位置                        | 用途                       |
| ------- | ------------------------- | ------------------------ |
| 首页（仪表盘） | `index/🔖-首页.md`          | 默认打开页：统计概览/待办/最近更新/项目概览  |
| 笔记总览    | `index/笔记总览.md`           | 全库笔记卡片浏览 + 附件体检          |
| 任务看板    | `kanban/个人任务看板.md`        | 任务唯一来源（首页待办只查看板）         |
| 配置指南    | `index/界面改造与配置指南.md`      | 界面配置/Style Settings/回滚方法 |
| 笔记表格视图  | `resource/base/笔记总览.base` | Bases 表格筛选视图             |

## 工作规范

- 笔记为 Markdown 文件，包含 YAML frontmatter（`---` 分隔）
- 看板使用 frontmatter `kanban-plugin: board` 和复选框语法（`- [ ]`）
- 模板使用 Templater 语法（如 `<% tp.file.title %>`）
- **新增笔记时，优先参考 `resource/templates/` 中的模板**
- 新建笔记默认放 `notes/`；导航/规范类放 `index/`
- Tag 规则见 `index/📋-Tag规范.md`（`type/index`、`project/*` 受控词表）
- 附件规则：`resource/attachments/<笔记名>/`；目录名一致性由 `obsidian-vault-lint` 的 ATT001 自动检查
- 指南/SOP **结项后**才迁入 `archive/guides/`；未结项留 `notes/`；大型专题用 `archive/<topic>/`，小主题（≤3 篇）进 `archive/misc/`（见 `obsidian-archive` skill）
- 与飞书互传见 `obsidian-lark-bridge`；仓库规范检查见 `obsidian-vault-lint`

## 项目 Skill（`.agents/skills/`）

| Skill                  | 用途                                                |
| ---------------------- | ------------------------------------------------- |
| `obsidian-lark-bridge` | Obsidian ↔ 飞书 Docx 上传/下载（含图片表格；画板可跳过）             |
| `obsidian-vault-lint`  | 以 `notes/` 为主的增量 lint（含 ATT001 附件目录一致性）；先报告，确认后再改 |
| `obsidian-archive`     | 按 `archive/guides` 与专题目录约定归档                      |

## Obsidian CLI 使用规范

涉及本 vault 的读取、创建、搜索、标签、任务、属性等操作，**优先**读取并遵循 `obsidian-cli` skill，通过 `obsidian` 命令行调用；不要绕过 CLI 直接读写文件系统，除非 CLI 无法完成或用户明确要求改文件。

1. **默认加 `silent`**：除非用户特别说明要在前台打开笔记或界面，否则所有可能打开文件的命令默认加上 `silent`（如 `read`、`create`、`append`、`search`）；仅当用户要求打开/跳转时才用 `obsidian open` 等不带 `silent` 的命令。
2. **标签搜索用 `obsidian tag`**：按标签筛选笔记时优先 `obsidian tag name="project/gnss" silent verbose`，比 `obsidian search` 全文搜索更精确；标签统计用 `obsidian tags counts sort=count`。嵌套 tag 写完整路径（如 `project/gnss`），无需 `#` 前缀。
