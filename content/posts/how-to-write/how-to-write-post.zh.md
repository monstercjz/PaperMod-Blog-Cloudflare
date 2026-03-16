---
title: "如何规范化撰写基于 PaperMod 博客的文章"
date: 2026-03-16
tags: ["教程", "Hugo"]
categories: ["博客"]
draft: false
---

本文介绍在 PaperMod 博客中撰写文章的注意事项。

## 文章页面字段-必填项

每篇文章开头的 front matter 必须包含以下字段：

```yaml
---
title: "文章标题"    # 必填：文章标题
date: 2026-03-16    # 必填：发布日期
---
```

## 文章页面字段-常用可选项

```yaml
---
# ===== 基础信息 =====
title: "文章标题"                        # 必填：文章标题
date: 2026-03-16                         # 必填：发布日期（YYYY-MM-DD）
lastmod: 2026-03-17                      # 最后修改日期
description: "文章简介"                   # 文章描述，用于 SEO 和社交媒体分享
author: "作者名"                         # 作者名，覆盖默认设置
keywords: ["关键词1", "关键词2"]          # SEO 关键词

# ===== 分类与标签 =====
tags: ["标签1", "标签2"]                 # 标签，细粒度分类，可多个
categories: ["分类名"]                   # 分类，粗粒度分类，通常一个
series: ["系列名"]                       # 系列文章，用于关联多篇相关文章

# ===== 发布状态 =====
draft: false                             # false = 发布，true = 草稿（不显示）
publishDate: 2026-03-16                  # 发布日期（可用于定时发布）
expiryDate: 2026-12-31                   # 过期日期，过期后文章不显示

# ===== 排序与置顶 =====
weight: 1                                # 排序权重，数字越小越靠前（用于置顶）
pinned: true                             # PaperMod 特有：置顶文章

# ===== 封面图片 =====
cover:
  image: "images/cover.jpg"              # 封面图片路径（相对 static 目录）
  alt: "图片描述"                         # 图片 alt 文本（无障碍访问）
  caption: "图片说明"                     # 图片下方说明文字
  relative: false                        # true = 相对于文章目录，false = 相对于 static

# ===== 功能开关（覆盖全局设置）=====
ShowToc: true                            # 是否显示目录
TocOpen: true                            # 目录是否默认展开
ShowReadingTime: true                    # 是否显示阅读时间
ShowShareButtons: true                   # 是否显示分享按钮
ShowBreadCrumbs: true                    # 是否显示面包屑导航
ShowPostNavLinks: true                   # 是否显示上一篇/下一篇导航
ShowCodeCopyButtons: true                # 是否显示代码复制按钮
ShowWordCount: true                      # 是否显示字数
comments: false                          # 是否启用评论

# ===== 其他设置 =====
slug: "custom-url"                       # 自定义 URL 别名（默认用文件名）
url: "custom-path/"                      # 自定义完整 URL 路径
type: "posts"                            # 内容类型（默认根据目录自动判断）
layout: "custom-layout"                  # 自定义布局模板
---
```

## 标签与分类

**标签（tags）和分类（categories）的区别：**

| 类型 | 特点 | 示例 |
|------|------|------|
| **标签** | 细粒度，一篇文章可有多个标签 | `["Hugo", "前端", "教程"]` |
| **分类** | 粗粒度，文章通常属于一个分类 | `["技术"]` |

**无需预先定义**：标签和分类的值在写文章时直接写即可，Hugo 会自动收集并生成对应页面。

```yaml
---
tags: ["Hugo", "教程"]      # 直接写，自动生成标签页
categories: ["博客"]        # 直接写，自动生成分类页
---
```

## 文章级功能开关

可以在单篇文章中覆盖全局设置：

```yaml
---
ShowToc: false              # 关闭目录
ShowReadingTime: false      # 关闭阅读时间
ShowShareButtons: false     # 关闭分享按钮
ShowBreadCrumbs: false      # 关闭面包屑导航
comments: false             # 关闭评论
---
```

## 注意事项

1. **文件命名**：使用小写字母和连字符，如 `my-first-post.zh.md`
2. **双语文章**：中文用 `.zh.md`，英文用 `.en.md`
3. **日期格式**：推荐 `YYYY-MM-DD` 格式
4. **草稿预览**：`draft: true` 的文章本地可见，部署后不显示
5. **内容格式**：支持 Markdown 语法

## 示例文章模板

```yaml
---
title: "我的第一篇文章"
date: 2026-03-16
tags: ["随笔", "生活"]
categories: ["日常"]
description: "这是我的第一篇博客文章"
---

这里写正文内容...

## 二级标题

正文内容...

### 三级标题

更多内容...
```

## 文章组织方式

`posts` 目录下可以创建子文件夹组织文章：

```
content/posts/
├── how-to-write-post.zh.md
├── tech/                      # 技术类文章
│   ├── hugo-tips.zh.md
│   └── react-guide.zh.md
├── life/                      # 生活类文章
│   └── travel.zh.md
└── 2026/                      # 按年份组织
    └── summary.zh.md
```

**注意**：
- 子文件夹名会成为 URL 的一部分
- 文章分类用 `categories` 字段，与文件夹无关
- 文件夹只是物理组织，不影响 Hugo 的分类系统

## 首页显示与文章排序

### 首页显示内容

由 `config.yml` 中的 `mainsections` 控制：

```yaml
mainsections: ["posts"]  # 首页显示 posts 目录的文章
```

### 文章排序规则

| 优先级 | 参数 | 说明 |
|--------|------|------|
| 1 | `weight` | 权重越小越靠前 |
| 2 | `date` | 日期越新越靠前（默认） |

### 置顶文章

使用 `weight` 参数实现置顶：

```yaml
---
title: "重要公告"
date: 2026-03-16
weight: 1           # 权重越小越靠前，实现置顶
---
```

或者使用 PaperMod 特有的 `pinned` 参数：

```yaml
---
title: "置顶文章"
pinned: true        # PaperMod 特有置顶方式
---
```


