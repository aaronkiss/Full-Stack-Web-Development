# 建立站点Build out the Site

Created: May 3, 2021 12:29 PM
Tags: CSS, Front-side, JavaScript, UX, Web, html

### 要点回顾

建立多个页面

建立面包屑(breadcrumb)

nav bar 使用 `<ul>` 是因为元素不需要自动排序

breadcrumbs 使用 `<ol>` 是因为面包屑需要自动排序以体现层级

通过CSS解决多个不同长宽比图片裁切为正方形

CSS鼠标hover阴影动画

### 随堂笔记

通过复制页面的通用部分以快速建立新页面。

面包屑(breadcrumbs)

代码如下：

```html
<ol class="breadcrumb">
     <li><a href="index.html">Home</a></li>
     <li><a href="albums.html">Albums</a></li>
     <li><a href="photo1.html">Photo 1</a></li>
</ol>
```

通过设置class以调用bootstrap中预置的breadcrumbs设定。

不同长宽比图片的统一裁切

这是一个可以预见的未来难题，不如现在就来解决它

代码如下：

```html
<div class="sq">    <!-- 给每个图片包裹一个div容器 -->
     <a href="photos.html">
        <img class="album_cover" src="./images/img_1.jpg" alt="graffiti cover image"/>
     </a>    <!-- 调用图片的类来设置裁切的大小及裁切方式 -->
</div>

<div class="sq">
     <a href="">
        <img class="album_cover" src="./images/img_2.jpg" alt="full english image"/>
     </a>
</div>

<div class="sq">
     <a href="">
        <img class="album_cover" src="./images/img_3.jpg" alt="racks of cheese image"/>
     </a>
</div>
```

```css
.sq{
    /* 给每个图片都套一个div，相当于把图片装进容器 */
    display: inline-block;  /* inline-block表示行内块元素， block表示带换行符的块元素 */
}
.album_cover{
    width: 300px;   /* 设置了图片容器的大小 */
    height:300px;
    object-fit: cover;  /* 将超出容器的部分裁切掉 */
    border: 20px solid rgb(197, 197, 197);
    transition: all 0.3s ease-in-out;
}
```

最后效果见页头图片。

由于对视觉效果的偏执，实在受不了乏味的页面效果，因此查阅资料后添加了hover阴影效果：

```css
.album_cover:hover{
    box-shadow: 0px 5px 8px 0 rgba(129, 129, 129, 0.7);
    transition: all 0.3s ease-in-out;
}
```

偶然看到一个网站的按钮动画效果不错，经过研究其页面的代码，终于实现了其效果：

```css
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        

        <title>
            按钮动画
        </title>

        <style type="text/css">

            .su_button{
                display: inline-block;
                text-align: center;
                box-sizing: content-box;
                background-image: linear-gradient(135deg, #4000b9, #fc28b8, #fc28b8, #4000b9);
                box-shadow: 0 5px 8px 0 rgba(116, 79, 168, 0.7);
                color: white;
                text-decoration: none;
                padding: 8px 20px;
                position: relative;
                border: none;
                background-size: 300% 100%;
                transition: all 0.4s ease-in-out;  /* 这里的作用是鼠标移开时也呈现动画 */
                border-radius: 5px;
            }
            a{
                background-color: transparent;
            }
            .su_button:hover{
                background-position: 100% 0;
                transition:all 0.4s ease-in-out;
                -moz-transition: all 0.4s ease-in-out;
                -o-transition: all 0.4s ease-in-out;
                -webkit-transition: all 0.4s ease-in-out;
            }
            .su_button:active{
                box-shadow: 0 2px 4px 0 rgba(116, 79, 168,0.7);
            }
 
        </style>
    </head>

    <body>
        <div class="post-item-button">
            <a href="#" class="su_button" >绚丽的按钮</a>
        </div>
    </body>
</html>
```

总结**: CSS可玩性非常不错，比在 DaVinci 里做动画省资源多了！**