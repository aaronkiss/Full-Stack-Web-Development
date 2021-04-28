# 相册图片自动翻页

Created: Apr 26, 2021 1:30 PM
Tags: CSS, Front-side, JavaScript, Web, html

### 要点回顾

## 变量(Variable)

由于JavaScript不是强类型语言，所以不用特别指定变量类型

网页中的“实质内容”通常都是通过JavaScript添加的，而不是在html中直接添加

### setInterval()函数

### 布尔型变量

### Javascript中的this 在不同的情况下可能是不同的东西。

`$(".something")`表示调取所有的something类（class）。

`$("#times")`表示调取所有id为times的元素。

### 随堂笔记

下方代码是最简单的变量声明和调用：

```jsx
var counter = 0;

$("#number").text(counter);
```

下方代码是html网页内对点击鼠标计数的功能调用：

```html
<body>
<h1 id = "number" onclick = "count();">
</h1>
</body>
```

下方代码是点击鼠标显示计数的逻辑实现：

```jsx
<script type = "text/javascript">
		var counter = 0;
		$("#number").html(counter);
		function count(){
				counter = counter + 1;
				$("#number").html(counter);
		};
</script>
```

经过测试：

```jsx
counter = counter + 1;
```

不能简单的写成

```jsx
counter =+ 1;
```

两者得到的结果并不一样。

在“点击显示大图”的代码中：

```jsx
<script>
		$(".crop-img").click(function(){
				$("#bigImage").attr('src', $(this).attr('src'));
});
</script>
```

`(this)`表示鼠标点击时的缩略图，缩略图就会显示在“this”中，即“this“其实是一个变量。

## 在实现图片滑动的效果时，缩略图标签需要添加id:

```jsx
<div class="row">
		<img id="image1" 
		class="crop-img" src="images/1.jpg" alt="图片的文字说明" />
</div>
```

## setInterval()函数

```jsx
setInterval(function(){
		$("#forward").click();
}, 1000);
```

### 这个函数只是定义每次调用另一个函数的间隔时间

初始定义布尔型变量：

```jsx
paused = false；
```

那么：

```jsx
!paused = true;    // “!” 表示“not”
paused = ！paused    //此时paused的值为“true”
```

本例中：

```jsx
paused = false;

$("#bigImage").click(function(){
		paused = !paused;
    //paused初始为“假”，大图被点击时调用函数设定paused为“真”，大图停止滑动
})；

setInterval(function(){
		if(!paused){
				$("#forward").click();  //如果不暂停，就执行“点击‘下一张’”指令
		};
}, 3000);    //调用函数的间隔为3秒
```

在上段代码中，paused初始值为“假”，所以是“不暂停”。那么!paused就为“真”，在鼠标点击大图的时候暂停就为“真”。把!paused赋给paused后，paused为“真”，那么!paused就为“假”。

总结**:**
