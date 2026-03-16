# 冇记

## 技术栈

本博客使用以下开源项目搭建：

| 项目 | 说明 | 地址 |
|------|------|------|
| [Hugo](https://gohugo.io/) | 静态网站生成器 | [github.com/gohugoio/hugo](https://github.com/gohugoio/hugo) |
| [PaperMod](https://github.com/adityatelange/hugo-PaperMod) | Hugo 主题 | [github.com/adityatelange/hugo-PaperMod](https://github.com/adityatelange/hugo-PaperMod) |

感谢以上开源项目的作者 🙏

## 博客地址

[https://paper.nuaa.dpdns.org/](https://paper.nuaa.dpdns.org/)

## 功能特性

- 🌐 中英双语支持
- 📱 响应式设计
- 🌙 深色/浅色主题自动切换
- 🔍 全站搜索
- 🏷️ 标签与分类
- 📰 RSS 订阅

## 本地运行

```bash
# 安装 Hugo (Windows)
winget install Hugo.Hugo.Extended

# 克隆项目
git clone --recursive https://github.com/monstercjz/PaperMod-blog-cf.git
cd PaperMod-blog-cf

# 本地预览
hugo server -D

# 浏览器访问 http://localhost:1313/
```

## 写作指南

详见文章：[如何撰写博客文章](https://paper.nuaa.dpdns.org/blog-paper/how-to-write-post/)

## 目录结构

```
├── config.yml          # 配置文件
├── content/            # 文章内容
│   └── blog-paper/          # 博客文章
├── assets/             # 静态资源
│   ├── css/            # 自定义样式
│   └── images/         # 图片资源
└── themes/             # 主题目录（子模块）
```

## 部署

部署在 [Cloudflare Pages](https://pages.cloudflare.com/)，推送代码后自动构建发布。

## License

- 本博客内容版权归作者所有
- PaperMod 主题遵循 [MIT License](https://github.com/adityatelange/hugo-PaperMod/blob/master/LICENSE)
