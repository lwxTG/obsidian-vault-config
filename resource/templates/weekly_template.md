---
uid: <% tp.date.now("YYYY") %>-W<% tp.date.now("WW") %>-weekly
title: <% tp.file.title %>
tags:
  - type/weekly
create_time: <% tp.file.creation_date() %>
date_range: <% tp.date.weekday("YYYY-MM-DD", 0) %> ~ <% tp.date.weekday("YYYY-MM-DD", 6) %>
---

# 📅 工作周记 -- 第<% tp.date.now("WW") %>周

## 🎯 本周待办事项

- [ ] 任务1

---

## 🐛 问题记录


---

## 📋 下周计划

- [ ] 任务1

