# Ziqiang Feng · 个人学术主页

这是一个为 GitHub Pages 设计的极简 Jekyll 学术主页。视觉上保留了参考站“绿色背景 + 中央白纸 + 内容优先”的气质，同时增加了响应式布局、清晰导航、可访问性和自动部署。

日常维护只需要改 Markdown 或 YAML，不需要碰 HTML/CSS。

## 先确认个人信息

站点已根据公开的学术资料预填姓名、单位、研究方向、论文与报告。正式发布前，请优先核对：

1. `_data/profile.yml` 中的单位、邮箱和个人链接；
2. `index.md` 中的个人简介；
3. `_publications/`、`_news/`、`_talks/` 中的条目；
4. 如有 CV，把 PDF 放入 `files/cv.pdf`，再在 `_data/profile.yml` 的 `links` 下新增链接。

当前头像位置使用姓名缩写 `ZF`。若要换成照片：把照片保存为 `assets/images/profile.jpg`，然后在 `_data/profile.yml` 中取消下面这行的注释即可：

```yaml
image: "/assets/images/profile.jpg"
```

## 日常更新

### 修改简介

直接编辑根目录的 `index.md`。正文支持标准 Markdown：

```md
My research is in **dynamical systems** and [ergodic theory](https://example.com/).
```

### 新增论文

复制 `_publications/` 里任意一个 `.md` 文件，修改文件名与顶部字段。例如：

```yaml
---
title: "Paper title"
date: 2026-08-21
year: 2026
type: "Preprint"
authors: "Ziqiang Feng and Coauthor"
venue: "arXiv:xxxx.xxxxx"
primary_url: "https://arxiv.org/abs/xxxx.xxxxx"
links:
  - label: "arXiv"
    url: "https://arxiv.org/abs/xxxx.xxxxx"
  - label: "PDF"
    url: "https://arxiv.org/pdf/xxxx.xxxxx"
---
```

页面会按 `date` 自动倒序排列。

### 新增动态或报告

- 动态：复制 `_news/` 中的 Markdown 文件；
- 报告：复制 `_talks/` 中的 Markdown 文件；
- 研究方向：编辑 `_data/research.yml`。

## 发布到 GitHub Pages

1. 把本目录全部文件推送到目标仓库的 `main` 分支；
2. 打开 GitHub 仓库的 `Settings → Pages`；
3. 在 `Build and deployment` 中选择 `GitHub Actions`；
4. 推送后，仓库中的 `Deploy academic website to GitHub Pages` 会自动构建与发布。

### 仓库名与网址

GitHub 账号是 `Feng104` 时：

- 仓库名为 `feng104.github.io`，默认网址是 `https://feng104.github.io/`；
- 仓库名为 `ziqiangfeng.github.io`，默认网址是 `https://feng104.github.io/ziqiangfeng.github.io/`。

本项目当前按你给出的仓库名 `ziqiangfeng.github.io` 配置。如果改成 `feng104.github.io`，请把 `_config.yml` 中的 `baseurl` 改为空字符串：

```yaml
baseurl: ""
```

## 本地预览（可选）

电脑已安装 Ruby 后：

```bash
bundle install
bundle exec jekyll serve
```

然后访问终端显示的本地地址。只在 GitHub 网页上编辑 Markdown 也完全可以，不需要本地环境。

## 目录说明

```text
index.md                 个人简介
_data/profile.yml        姓名、单位、邮箱、导航与外链
_data/research.yml       研究方向
_publications/*.md       论文
_news/*.md               动态
_talks/*.md              学术报告
assets/css/main.css      视觉样式（通常无需修改）
_layouts/                页面结构（通常无需修改）
.github/workflows/       自动发布（通常无需修改）
```
