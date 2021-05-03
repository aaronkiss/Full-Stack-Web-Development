# Basic Bootstrap Setup

Created: May 1, 2021 9:58 AM
Tags: CSS, Design, Front-side, JavaScript, UX, Web, html

### 要点回顾

### 参考网站

[http://getbootstrap.com/getting-started/](http://getbootstrap.com/getting-started/)

### 随堂笔记

- 使用Bootstrap库开始编码。
- 基本的Bootstrap文件系统包括：CSS、fonts、images、JS以及index文件

**CSS**文件夹包含最重要的内容，即引导CSS，并且是实时引导。

**fonts slide**文件夹包含了一组字体，这些字体提供了Bootstrap附带的一些图标。

**images**文件夹中有一整套图像。

**index.html**是一个简单的html文件，显示了如何使用基本的Bootstrap。

**JS**文件夹包含一堆JavaScript库，并允许Bootstrap调用。其中包含jQuery、bootstrap.min、bootstrap。

基本思想：当有人访问网站时，不需要在显示相关内容之前下载太多数据，否则网站的运行会缓慢。

### 在调试网站的时候可以使用普通版本的文件，在启动网站的使用后应该使用“压缩版本”以获得最佳性能。

### 关于index.html

```html
<!DOCTYPE html>    <!-- 表示此html文件是什么类型的文件，可以是更严格的xhtml -->
<html lang="en">    <!-- 带有语言属性的html标记，表示页面使用英语编写 -->
  <head>
   <title></title>

    <link href="css/bootstrap.css" rel="stylesheet"> <!-- 从css文件夹调用bootstrap -->
    
    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->    <!-- 以上是关于向旧浏览器兼容的注释 -->

  </head>
  
  <body>
    <!-- 导入两个JavaScript库文件 -->
    <script src="js/jquery.min.js"></script> <!-- jquery libraries -->
    <script src="js/bootstrap.min.js"></script> <!-- bootsrap libraries -->

  </body>
</html>
```

### 关于“优雅降级”：如果某人使用的浏览器略有缺陷，而该浏览器没有完整的功能，则它可以确保网站不会完全失败。

**总结:HTML5是目前html最新的版本。填充程序使人们可以在不支持html5的旧浏览器上查看网站。    Bootstrap是一个CSS库，但也具有JavaScript的部分，这些JavaScript部分提供了纯CSS无法提供的交互功能。**
