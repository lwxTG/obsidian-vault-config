# Obsidian Vault 配置仓库

本仓库只包含 Obsidian vault 的**配置与模板**，不含任何笔记内容。

## 内容

| 路径 | 说明 |
| --- | --- |
| `.obsidian/` | 全部 Obsidian 配置：核心/社区插件清单、插件设置、外观、CSS snippets、主题（已排除 `workspace*.json`、`cache/` 等运行时文件） |
| `resource/templates/` | Templater 笔记模板（daily / weekly / note / study / kanban） |
| `AGENTS.md` / `CLAUDE.md` | vault 目录结构与工作规范说明 |
| `.gitignore` | 忽略规则 |

## 恢复方法

1. 新建或已有 vault 中，将 `.obsidian/`、`resource/templates/`、`AGENTS.md` 覆盖到对应位置
2. 打开 Obsidian → 设置 → 第三方插件 → 关闭安全模式，插件会按 `community-plugins.json` 清单加载
3. 按需调整插件设置中的本地路径
