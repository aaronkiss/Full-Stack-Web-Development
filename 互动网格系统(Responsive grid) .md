# 互动网格系统(Responsive grid)

Created: May 4, 2021 1:50 PM
Tags: Bootstrap, CSS, Front-side, JavaScript, UX, Web, html

### 要点回顾

为了渲染正确及触摸缩放正确，需要将 `<meta>` 添加入 `<head>`  中。

### 随堂笔记

### 移动设备优先

为了兼容移动设备，需要在 `<head>` 中添加 `<meta>` 标签

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

另外：

```html
<meta user-scaleble=no >    <!-- 表示禁止移动设备的缩放 -->
```

这意味着用户在移动设备上观看页面只能滚动，并使页面看起来更像个本地应用程序。因此需要谨慎使用。

### 版式和链接

Bootstrap设置基本的全局显示、版式、链接样式：

- 在 `body` 中设置 `background-color: #fff`
- 使用 `@font-family-base` , `@font-size-base` , `@line-height-base` 作为基本文字样式
- 通过使用全局链接颜色 `@link-color` 并仅在以下位置应用链接的下划线 `:hover`

以上样式都可以在 `scaffolding.less` 中找到。

### Nornalize.css

为了改善跨浏览器的呈现，应该使用 [Normalize.css](https://necolas.github.io/normalize.css/)

### Containers

Bootstrap需要一个容器来包装站点内容并使用网格系统。有两种容器可供使用：

```html
<div class="container">    <!-- 这是一个响应固定宽度的容器 -->
    ...
</div>
```

```html
<div class="container-fluid">    <!-- 这是一个全宽度容器，跨越视图的整个宽度 -->
    ...
</div>
```

### 网格系统(Grid system)

总宽度为12列。

- 行必须放在 `.container` （固定宽度）或 `.container-fluid` （全宽度）内
- 使用行创建水平的列组
- 内容必须放在列中，只有列可以是行的直接子容器
- 预定义的栅格类 `.row` 和 `.col-xs-4` 可用于快速创建布局。 `mixin` 可用于更多的语义布局
- 列可以通过 `padding` 创建列内容之间的间隙。
- 如果在一行里放置超过12列，则超过的列会被放到第二行

### 媒体查询

### 网格选项

[Untitled](https://www.notion.so/335f616c15f841e88015c6b572141b0f)

### 偏移列

使用 `.col-md-offset-*` 将列向右偏移。 * =4 表示向右偏移4列。

```html
<div class="row">
    <div class="col-md-4 col-md-offset-4">...</div>
</div>
```

### 嵌套列

要将内容与默认网格嵌套，需在现有列中添加新行 `.row` 和一组列 `.col-sm-* .col-sm-*`  。嵌套行应包括一组总计不超过12列的宽度。

1级： .col-sm-9

2级： .col-xs-8 .col-sm-6                        2级： .col-xs-4 .col-sm-6

```html
<div class="row">
  <div class="col-sm-9">
    Level 1: .col-sm-9<div class="row">
      <div class="col-xs-8 col-sm-6">
        Level 2: .col-xs-8 .col-sm-6</div>
      <div class="col-xs-4 col-sm-6">
        Level 2: .col-xs-4 .col-sm-6</div>
    </div>
  </div>
</div>
```

给上边的代码添加背景色就可以看出来区别了

```css
<style>
    .col-sm-9{
        background-color: #20c997;
        padding: 25px;
        border-color: red;
        margin: 5px;
    }

    .col-xs-8{
        background-color: yellow;
        padding: 10px;
        margin: 5px;
    }

    .col-xs-4{
        background-color: blue;
        color:white;
        padding: 10px;
    }
</style>
```

### 列顺序

使用 `.col-md-push-*` 和 `.col-md-pull-*` 更改内置网格列的顺序。

.col-md-3 .col-md-pull-9        .col-md-9 .col-md-push-3

```html
<div class="row"
		<div class="col-md-9 col-md-push-3">.col-md-9 .col-md-push-3</div>
		<div calss="col-md-3 col-md-pull-9">.col-md-3 .col-md-pull-9</div>
</div>
```

### Less mixins 和变量

可以用于快速生成简单的自定义布局。

**变量** 确定列数、间隙宽度等。

```css
@grid-columns:12;
@grid-gutter-width: 30px;
@grid-float-breadpoint: 768px;
```

**Less mixins**

与网格变量结合使用以生成单个网格列的自定义css

```css
.wrapper {
  .make-row();
}
.content-main {
  .make-lg-column(8);
}
.content-secondary {
  .make-lg-column(3);
  .make-lg-column-offset(1);
}
```

```html
<div class="wrapper">
  <div class="content-main">...</div>
  <div class="content-secondary">...</div>
</div>
```

### 标题

用 `<h1>` ～ `<h6>` 可以表示各级标题，也可以用 `.h1` ～ `.h6` 类实现。

```html
<div class="h1">这是h1标题</div>
```

用 <small> 或 .small 类可以创建较浅的辅助文本。

```html
<h1>这是h1标题<small>这是辅助文本</small></h1>
```

### 正文

Bootstrap的全局默认 `font-size` 为 14px， `line-height` 为1.428。这适用于 `<body>` 和所有段落。 而 `<p>` 的底边距为行高的一半，默认为10px。

### 铅体副本（Lead body copy）

通过添加 `.lead` 使段落突出。

```html
<p class="lead">...</p>
```

### Build with less

输出比例基于variable.less中的两个Less变量： `@font-size-base`  和 `@line-height-base` 。

第一个是全局的基本字体大小，第二个是基本行高。

总结**: 本篇内容可以在用到的时候再继续整理。[内容来自这里](https://getbootstrap.com/docs/3.4/css/#grid-offsetting)**