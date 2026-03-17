# Archetypes 使用说明

## 什么是 Archetypes？

Archetypes 是 Hugo 的内容模板系统，用于在创建新文章时自动生成 front matter 配置。

## 使用方法

### 方法1：在框架仓库创建文章（需要Hugo环境）

```bash
# 创建普通文章
hugo new my-article.md

# 创建博客文章（使用posts模板）
hugo new posts/my-first-post.md

# 创建在指定目录
hugo new posts/tech/hugo-tutorial.md
```

### 方法2：在内容仓库创建文章

由于内容仓库通过 Hugo Modules 挂载，推荐直接在内容仓库手动创建文件。

#### 文件命名规范

```
推荐格式：文章标题-语言.md
示例：
- my-first-post.zh.md (中文文章)
- my-first-post.en.md (英文文章)
- hugo-tutorial.zh.md (教程文章)
```

#### 手动创建文章模板

复制以下内容到新文章：

```yaml
---
title: "文章标题"
date: 2026-03-16
lastmod: 2026-03-16
draft: false
description: "文章描述"
tags: ["标签1", "标签2"]
categories: ["分类"]
keywords: ["关键词"]
cover:
  image: ""
  alt: ""
  caption: ""
ShowToc: true
---

<!-- 文章内容 -->
```

## 模板文件说明

### default.md

默认模板，适用于所有类型的内容。

### posts.md

博客文章专用模板，包含：
- 标签和分类
- 封面图配置
- 目录设置
- 文章结构模板

## 自定义模板

可以创建更多特定类型的模板：

```
archetypes/
├── default.md       # 默认模板
├── posts.md         # 博客文章
├── tutorials.md     # 教程文章（可自定义）
└── notes.md         # 笔记文章（可自定义）
```

使用：`hugo new tutorials/hugo-guide.md`

## Front Matter 字段说明

### 基础字段

| 字段 | 说明 | 示例 |
|------|------|------|
| title | 文章标题 | `"我的第一篇文章"` |
| date | 发布日期 | `2026-03-16` |
| lastmod | 最后修改时间 | `2026-03-16` |
| draft | 是否草稿 | `true` / `false` |
| description | 文章描述（SEO） | `"文章简介"` |

### 分类字段

| 字段 | 说明 | 示例 |
|------|------|------|
| tags | 标签 | `["Hugo", "博客"]` |
| categories | 分类 | `["技术"]` |
| series | 系列 | `"Hugo教程"` |
| keywords | SEO关键词 | `["Hugo", "教程"]` |

### 显示控制

| 字段 | 说明 | 示例 |
|------|------|------|
| ShowToc | 显示目录 | `true` |
| TocOpen | 默认展开目录 | `true` |
| ShowBreadCrumbs | 显示面包屑 | `true` |
| ShowReadingTime | 显示阅读时间 | `true` |

### 封面图

| 字段 | 说明 | 示例 |
|------|------|------|
| cover.image | 封面图路径 | `"/images/cover.jpg"` |
| cover.alt | 图片描述 | `"封面图"` |
| cover.caption | 图片说明 | `"图片来源：xxx"` |

## 注意事项

1. **日期格式**：推荐使用 `YYYY-MM-DD` 或 `YYYY-MM-DDTHH:MM:SS`
2. **布尔值**：使用 `true` / `false`，不要加引号
3. **数组**：使用 YAML 数组格式 `["item1", "item2"]`
4. **多语言文章**：使用语言后缀 `.zh.md` / `.en.md`
