# Where can you go? 关于网站导航

Created: May 1, 2021 6:06 PM
Tags: CSS, Front-side, JavaScript, Web, html

### 要点回顾

Accordion（手风琴）效果

`<ul>` 表示无需列表

`<div>` 用来包装页面内容元素

`<nav>` 用来标记导航栏

### 参考网站

[https://getbootstrap.com/docs/5.0/components/accordion/](https://getbootstrap.com/docs/5.0/components/accordion/)

[https://code.z01.com/v4/components/collapse.html](https://code.z01.com/v4/components/collapse.html)

### 随堂笔记

### Accordion（手风琴）效果

### Navbar（导航栏）

导航栏标签以 `<nav>`表示， 其中的class 可以在Bootstrap.css中找到。

`class="active"` 表示该项目保持高亮以区分其他项目。

相关代码：

```html
<nav class="navbar navbar-default">   <!-- 使导航栏与页面其他部分的背景区分开来 -->
      <div class="container-fluid">    <!-- 使用div来包装导航栏,容器设为流体容器 -->
        <ul class="nav navbar-nav">   <!-- 使导航链接变为导航按钮 -->
          <li class="active"><a href="#">Home</a></li>    <!-- active类让该标签保持高亮 -->
          <li><a href="#">My phtots</a></li>
        </ul>
      </div>
</nav>
```

### 可在小屏幕上折叠的导航栏（Collapse Navbar）

```html
<nav class="navbar navbar-default"><!-- 使导航栏与页面其他部分的背景区分开来 -->
      <div class="container-fluid"><!-- 将容器设为流体容器，可随浏览器大小动态布局 -->

        <!-- 折叠导航栏按钮 开始 -->
        <div class="navbar-header">
          <button 
              type="button" 
              class="navbar-toggle collapsed" 
              data-toggle="collapse"
              data-target="#main_navbar" 
              aria-expanded="false">Menu</button>
        </div>  <!-- 折叠导航栏按钮 结束 -->

        <!-- 未折叠的导航栏 开始 -->
        <div class="collapse navbar-collapse"
              id="main_navbar"><!-- 设置导航栏可折叠的类和被调用的id -->
          <ul class="nav navbar-nav">   <!-- 使导航链接变为导航按钮 -->
            <li class="active"><a href="#">Home</a></li>    <!-- active类让该标签保持高亮 -->
            <li><a href="#">My phtots</a></li>
          </ul>
        </div>  <!-- 未折叠的导航栏 结束 -->
      </div>  <!-- /container -->
    </nav>
```

`class="navbar-toggle collapsed"` 表示导航栏折叠时显示的内容。

`data-toggle="collapse"` 表示切换的数据是折叠的状态。

`data-target="#main_navbar"` 表示切换的目标是 `id=“main_navbar”` 的对象。

`aria-expanded="false"` 表示可折叠导航栏默认是折叠状态。

总结**:**