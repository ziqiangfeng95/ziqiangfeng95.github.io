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


## 使用课程专属 class
先把课程页中的：
<div class="site-shell paper simple-page" markdown="1">
改为：
<div class="site-shell paper simple-page course-page" markdown="1">
然后在 assets/css/main.css 末尾添加仅以 .course-page 开头的样式：
/* Only affects Advanced Mathematics A (Part I) */
.course-page {
  font-family: "Times New Roman", "Songti SC", "Noto Serif SC", serif;
  font-size: 17px;
  line-height: 1.75;
}

.course-page > h2 {
  margin-bottom: 1.5rem;
  font-family: "Times New Roman", "Songti SC", serif;
  font-size: 1.8rem;
  line-height: 1.35;
  text-align: center;
}

.course-page h3 {
  margin-top: 1.6rem;
  margin-bottom: 0.6rem;
  font-size: 1.2rem;
}

.course-page a {
  color: #246b58;
  text-underline-offset: 0.18em;
}

.course-page a:hover {
  color: #174b3e;
}
因为所有选择器都以 .course-page 开头，而主页没有这个 class，所以 Hero、About、Publications、Teaching 和主页字体都不会改变。
常用调整：
.course-page {
  font-size: 16px; /* 正文大小 */
}

.course-page > h2 {
  font-size: 28px; /* 页面标题 */
}

.course-page h3 {
  font-size: 20px; /* Instructor、Course Information 等小标题 */
}
添加 PDF
建议在仓库中新建：
assets/pdfs/00132511/
例如上传：
assets/pdfs/00132511/syllabus.pdf
assets/pdfs/00132511/lecture-01.pdf
assets/pdfs/00132511/homework-01.pdf
然后直接在课程 Markdown 中写：
### Course Materials

- [Course Syllabus (PDF)]({{ '/assets/pdfs/00132511/syllabus.pdf' | relative_url }})
- [Lecture 1 Notes (PDF)]({{ '/assets/pdfs/00132511/lecture-01.pdf' | relative_url }})
- [Homework 1 (PDF)]({{ '/assets/pdfs/00132511/homework-01.pdf' | relative_url }})
如果希望点击后在新标签页打开，使用 HTML：
<a href="{{ '/assets/pdfs/00132511/lecture-01.pdf' | relative_url }}"
   target="_blank"
   rel="noopener noreferrer">
  Lecture 1 Notes (PDF)
</a>
文件名建议只使用小写英文、数字和连字符，避免空格，例如：
lecture-01.pdf
midterm-review.pdf
homework-02.pdf
最快捷的 GitHub 网页操作流程
1. 在仓库打开 assets，创建并上传 pdfs/00132511/*.pdf。
2. 编辑 teaching/example-course/index.md，加入 PDF 链接及 course-page class。
3. 编辑 assets/css/main.css，追加 .course-page 样式。
4. Commit 到 main。
5. 等待 GitHub Pages 自动部署约一分钟。



### 最推荐使用 Jekyll/Liquid 的注释：
{% comment %}
Temporarily hidden section
This paragraph will not appear on the rendered page.

- Item one
- Item two

$$
\int_0^1 x^2\,dx=\frac13
$$

{% endcomment %}
提交后，这一整段不会进入最终生成的网页。普通 Markdown、列表、HTML、数学公式和链接都可以放在里面。

如果注释的是 front matter，需要逐行使用 YAML 的 #：
```---
title: "00132511"
permalink: /00132511/
# hide_site_header: true
---'''
不要注释 ---，也不要轻易注释 permalink，否则课程网址可能改变。
