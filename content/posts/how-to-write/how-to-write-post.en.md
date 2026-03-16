---
title: "How to Write Blog Posts"
date: 2026-03-16
tags: ["Tutorial", "Hugo"]
categories: ["Blog"]
draft: false
---

This article introduces the guidelines for writing posts in the PaperMod blog.

## Required Fields

Each post's front matter must include the following fields:

```yaml
---
title: "Post Title"    # Required: post title
date: 2026-03-16       # Required: publish date
---
```

## Common Optional Fields

```yaml
---
# ===== Basic Info =====
title: "Post Title"                      # Required: post title
date: 2026-03-16                         # Required: publish date (YYYY-MM-DD)
lastmod: 2026-03-17                      # Last modified date
description: "Post summary"              # Description for SEO and social sharing
author: "Author name"                    # Author name, overrides default
keywords: ["keyword1", "keyword2"]       # SEO keywords

# ===== Taxonomy =====
tags: ["tag1", "tag2"]                   # Tags, fine-grained, multiple allowed
categories: ["category"]                 # Categories, coarse-grained, usually one
series: ["series-name"]                  # Series name, for linking related posts

# ===== Publish Status =====
draft: false                             # false = published, true = draft (hidden)
publishDate: 2026-03-16                  # Publish date (for scheduled publishing)
expiryDate: 2026-12-31                   # Expiry date, post hidden after this date

# ===== Sorting & Pinning =====
weight: 1                                # Sort weight, lower = earlier (for pinning)
pinned: true                             # PaperMod-specific: pin post to top

# ===== Cover Image =====
cover:
  image: "images/cover.jpg"              # Cover image path (relative to static)
  alt: "Image description"               # Image alt text (accessibility)
  caption: "Image caption"               # Caption text below image
  relative: false                        # true = relative to post, false = relative to static

# ===== Feature Toggles (override global settings) =====
ShowToc: true                            # Show table of contents
TocOpen: true                            # TOC expanded by default
ShowReadingTime: true                    # Show reading time
ShowShareButtons: true                   # Show share buttons
ShowBreadCrumbs: true                    # Show breadcrumbs navigation
ShowPostNavLinks: true                   # Show prev/next post navigation
ShowCodeCopyButtons: true                # Show code copy buttons
ShowWordCount: true                      # Show word count
comments: false                          # Enable comments

# ===== Other Settings =====
slug: "custom-url"                       # Custom URL slug (default: filename)
url: "custom-path/"                      # Custom full URL path
type: "posts"                            # Content type (auto-detected from folder)
layout: "custom-layout"                  # Custom layout template
---
```

## Tags vs Categories

**Difference between tags and categories:**

| Type | Characteristics | Example |
|------|-----------------|---------|
| **Tags** | Fine-grained, multiple tags per post | `["Hugo", "Frontend", "Tutorial"]` |
| **Categories** | Coarse-grained, usually one category per post | `["Tech"]` |

**No pre-definition needed**: Just write tags and categories directly in your posts. Hugo will automatically collect them and generate corresponding pages.

```yaml
---
tags: ["Hugo", "Tutorial"]   # Just write, pages auto-generated
categories: ["Blog"]         # Just write, pages auto-generated
---
```

## Post Organization

You can create subdirectories under `posts` to organize your articles:

```
content/posts/
├── how-to-write-post.en.md
├── tech/                      # Tech articles
│   ├── hugo-tips.en.md
│   └── react-guide.en.md
├── life/                      # Life articles
│   └── travel.en.md
└── 2026/                      # By year
    └── summary.en.md
```

**Notes**:
- Subdirectory names become part of the URL
- Post categories use the `categories` field, unrelated to folders
- Folders are for physical organization only, not Hugo's taxonomy system

## Homepage Display & Post Ordering

### Homepage Content

Controlled by `mainsections` in `config.yml`:

```yaml
mainsections: ["posts"]  # Homepage shows posts from the posts directory
```

### Post Ordering Rules

| Priority | Parameter | Description |
|----------|-----------|-------------|
| 1 | `weight` | Lower weight appears first |
| 2 | `date` | Newer date appears first (default) |

### Pinning Posts

Use `weight` parameter to pin posts:

```yaml
---
title: "Important Announcement"
date: 2026-03-16
weight: 1           # Lower weight = pinned to top
---
```

Or use PaperMod's `pinned` parameter:

```yaml
---
title: "Pinned Post"
pinned: true        # PaperMod-specific pinning method
---
```

## Post-level Feature Toggles

You can override global settings in individual posts:

```yaml
---
ShowToc: false              # Disable table of contents
ShowReadingTime: false      # Disable reading time
ShowShareButtons: false     # Disable share buttons
ShowBreadCrumbs: false      # Disable breadcrumbs
comments: false             # Disable comments
---
```

## Important Notes

1. **File Naming**: Use lowercase letters and hyphens, e.g., `my-first-post.en.md`
2. **Bilingual Posts**: Use `.zh.md` for Chinese, `.en.md` for English
3. **Date Format**: Recommended format is `YYYY-MM-DD`
4. **Draft Preview**: Posts with `draft: true` are visible locally but hidden in production
5. **Content Format**: Markdown syntax is supported

## Post Template

```yaml
---
title: "My First Post"
date: 2026-03-16
tags: ["Random", "Life"]
categories: ["Daily"]
description: "This is my first blog post"
---

Write your content here...

## Heading 2

Content...

### Heading 3

More content...
```

Happy writing!
