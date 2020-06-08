---
title: Hugo Book Theme 使用说明
date: 2019-10-17 21:19:32
tags:
- theme
---

# Hugo Book Theme

## 特点

- 干净简洁
- 轻便，对移动端支持友好
- 可自定义
- 布局之间互不干扰
- 无需初始配置
- 简单方便的代码块

## 配置要求
- Hugo 0.55 或更高版本
- Hugo 拓展版，[点击这里](https://gohugo.io/news/0.48-relnotes/)查看更多信息。

**Hugo 拓展版本下载**

由于此主题需要使用 Hugo 拓展版

去 [Hugo-releases](https://github.com/gohugoio/hugo/releases) 页面下载 `hugo_extended_x.xx.x_Windows-64bit.zip` 版本

## 安装
### 原有的博客项目下修改
进入 hugo 项目根目录并运行以下命令：
```bash
git submodule add https://github.com/alex-shpak/hugo-book themes/book
```
然后运行 hugo 测试(或在配置文件中设置 `theme = "book"` / `theme: book`)
```bash
hugo server --minify --theme book
```
### 重新创建一个博客网站

以下是如何重新创建一个新网站的示例
```bash
hugo new site mydocs; cd mydocs
git init
git submodule add https://github.com/alex-shpak/hugo-book themes/book
cp -R themes/book/exampleSite/content .
```
然后
```bash
hugo server --minify --theme book
```

## 分类菜单

### 文件树菜单

 默认情况下，主题将以`content/docs`树状结构的形式呈现部分中的页面。
您可以在页面的前部设置`title`和`weight`调整菜单中的顺序和标题。 

### 叶束菜单

您还可以使用叶包及其内容`index.md`作为菜单。
鉴于您具有此文件结构

```
├── content
│   ├── docs
│   │   ├── page-one.md
│   │   └── page-two.md
│   └── posts
│       ├── post-one.md
│       └── post-two.md
```

 创建`content/docs/menu/index.md` ，在 `index.md ` 中加入以下内容 

```
+++
headless = true
+++

- [Book Example]({{< relref "/docs/" >}})
  - [Page One]({{< relref "/docs/page-one" >}})
  - [Page Two]({{< relref "/docs/page-two" >}})
- [Blog]({{< relref "/posts" >}})
```

并通过修改站点配置中的 `BookMenuBundle: /menu` 设置启用它

- [示例菜单](https://github.com/alex-shpak/hugo-book/blob/master/exampleSite/content/menu/index.md)
- [配置文件示例](https://github.com/alex-shpak/hugo-book/blob/master/exampleSite/config.yaml)
- [叶束](https://gohugo.io/content-management/page-bundles/)

## 关于搭建博客

此主题支持部分的简单博客`posts`。
博客不是主要的用例，因此本书主题只有很少的功能 

## 配置

### 网站配置

如下 `config.toml` 案例

```
#（可选）设置Google Analytics（分析）（如果您使用它来跟踪您的网站）。
# 始终将其放在配置文件的顶部，否则将不起作用
googleAnalytics = "UA-XXXXXXXXX-X"

# （可选）如果在文件名中使用大写字母，则将其设置为true 
disablePathToLower = true

# （可选）将此属性设置为true可在“doc”类型页面上启用“最后修改者”日期和git author ＃信息。
#  information on 'doc' type pages.
enableGitInfo = true

#（可选）主题仅供文档使用，因此不呈现分类法。
# 您可以使用下面的配置删除相关文件
disableKinds = ['taxonomy', 'taxonomyTerm']

# 代码块样式使用 highlight 
# 代码块主题配置
# pygmentsStyle = 'monokailight'
pygmentsCodeFences = true
  
[params]
  #（可选，默认为6）设置要在页面上显示多少个目录级别。
  # 使用false隐藏ToC，请注意0将默认为6（https://gohugo.io/functions/default/）
  # 您还可以在每页前面指定此参数
  BookToC = 3
  
  # （可选，默认为无）设置书籍徽标的路径。如果徽标是
  # /static/logo.png，那么路径将是'logo.png'
  BookLogo = 'logo.png'
  
  # (可选，默认设置为无)将叶子包设置为侧面菜单
  # 未指定文件结构和权重时使用
  BookMenuBundle = '/menu'
  
  #（可选，默认文档）指定内容的一部分为渲染为菜单
  # 您还可以将值设置为“ *”以将所有部分渲染到菜单
  BookSection = 'docs'
  
  # 设置源存储库位置。
  # 用于“最后修改”和“编辑此页面”链接。
  BookRepo = 'https://github.com/alex-shpak/hugo-book'
  
  # 启用“文档”页面类型的“编辑此页面”链接。
  # 默认禁用。取消注释即可启用。需要“ BookRepo”参数。
  # 路径必须指向仓库的“内容”目录。
  BookEditPath = 'edit/master/exampleSite/content'
  
  # （可选，默认为2006年1月2日）配置页面上使用的日期格式
  # - 在git信息中
  # - 在博客文章
  BookDateFormat = 'Jan 2, 2006'
  
  # （可选，默认为true）启用lunr.js的搜索功能，
  # 索引是动态建立的，因此可能会降低您的网站速度。
  BookSearch = true
```

### 页面配置

您可以在首页上为每页指定其他参数

```
# 如果要在配置的部分之外渲染页面，或者如果要渲染'docs'以外的部分，则将类型设置为'docs'
type = 'docs'

# 设置页面权重以重新排列文件树菜单中的项目（如果BookMenuBundle不set）
# 就是页面菜单的每个项目的前后顺序，类似有序列表
weight = 10

# （可选）设置为在文件树菜单中将页面标记为平面部分（如果未设置BookMenuBundle）
bookFlatSection = true

# （可选，实验性）设置为隐藏该级别的嵌套部分或页面。仅适用于文件树菜单模式
# 只在点击当前目录时显示目录下文件
bookCollapseSection = true

# （可选）设置为true可从侧面菜单隐藏页面或部分（如果未设置BookMenuBundle）
# 隐藏当前目录下的所有文件，不在主页菜单
bookHidden = true

# （可选）设置要显示的ToC级别。使用'false'完全隐藏ToC 
bookToC = 3
```

### 修改部分布局

你可以在以下目录覆盖空的局部 `layouts/partials/`

| 局部布局                                        | 在页面中的位置         |
| ----------------------------------------------- | ---------------------- |
| `layouts/partials/docs/inject/head.html`        | 加在 `<head>` 标签之前 |
| `layouts/partials/docs/inject/body.html`        | 加在 `<body>` 标签之前 |
| `layouts/partials/docs/inject/footer.html`      | 页面内容最后           |
| `layouts/partials/docs/inject/menu-before.html` | 在`<nav>` 菜单块的开头 |
| `layouts/partials/docs/inject/menu-after.html`  | 在`<nav>` 菜单块的末尾 |

### 添加额外的定制样式

| 文件                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| `static/favicon.png`     | 覆盖默认图标                                                 |
| `assets/_custom.scss`    | 自定义或覆盖scss样式                                         |
| `assets/_variables.scss` | 覆盖默认的SCSS变量                                           |
| `assets/_fonts.scss`     | 将默认字体替换为自定义字体（例如本地文件或远程字体，例如Google字体） |

## 文章拓展组件

### 提示框

可作用于 提示/警示/通知 块。有三种颜色：`info`，`warning`，`danger`

```html
{{< hint [info|warning|danger] >}}
**Markdown content**  
Lorem markdownum insigne. Olympo signis Delphis! Retexi Nereius nova develat
stringit, frustra Saturnius uteroque inter! Oculis non ritibus Telethusa
{{< /hint >}}
```

### 按钮链接

 可以添加外部链接的按钮

```html
{{< button relref="/" >}}Get Home{{< /button >}}
{{< button href="https://github.com/alex-shpak/hugo-book" >}}Contribute{{< /button >}}
```

### 多 tab 切换

可以实现多列表切换

```html
{{< tabs "uniqueid" >}}
{{< tab "MacOS" >}} # MacOS Content {{< /tab >}}
{{< tab "Linux" >}} # Linux Content {{< /tab >}}
{{< tab "Windows" >}} # Windows Content {{< /tab >}}
{{< /tabs >}}
```

### 多栏布局

在两列或更多列中组织文本以有效利用空间。

```html
{{< columns >}}
<!-- begin columns block -->

# Left Content Lorem markdownum insigne... <--->
<!-- magic sparator, between columns -->

# Mid Content Lorem markdownum insigne... <--->
<!-- magic sparator, between columns -->

# Right Content Lorem markdownum insigne... {{< /columns >}}
```

### 拓展面板

提供可点击的面板，显示额外的隐藏内容。

```html
{{< expand >}}
## Markdown content
{{< /expand >}}
```

### 图标渲染

 使用[mermaidjs](https://mermaidjs.github.io/)渲染各种图表 

```html
{{< mermaid >}}
sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
        Bob->>Alice: Not so good :(
    else is well
        Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
        Bob->>Alice: Thanks for asking
    end
{{< /mermaid >}}
```

### KaTeX语法

使用[KaTeX](https://katex.org/)渲染数学公式

```html
{{< katex >}}
x = \begin{cases}
   a &\text{if } b \\
   c &\text{if } d
\end{cases}
{{< /katex >}}
```



> 注：本文只是翻译中文版 
> 附原文档地址：[Hugo-book](https://github.com/alex-shpak/hugo-book)