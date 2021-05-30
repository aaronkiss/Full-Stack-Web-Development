# 完整的图像库数据结构 Data structure

Created: May 24, 2021 1:39 PM
Tags: Bootstrap, Design, Front-side, Handlebars, JavaScript, Web, html

### 要点回顾

`<meta>` 标签

Handlebars 助手代码

### 参考网站

[https://www.runoob.com/tags/tag-meta.html](https://www.runoob.com/tags/tag-meta.html)

### 随堂笔记

完整的index代码：

```html
<!DOCTYPE html>
<!-- 这是图片库的完整实例的复刻 -->

<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>图片库</title>

        <script src="js/jquery.min.js"></script>
        <script src="js/bootstrap.min.js"></script>
        <script src="js/handlebars-v3.0.3.js"></script>

        <!-- 
            这里是我们的 JavaScript 文件。
            Albums.js 包含了 data 数据。
            gallery.js 是代码 
        -->
        <script src="js/Albums.js"></script>
        <script src="js/gallery.js"></script>

        <link href="css/bootstrap.css" rel="stylesheet">
        <link href="css/gallery.css" rel="stylesheet">

        <!-- IE8 对于 HTML5 和 Respond.js 的支持-->
        <!-- WARNING: Respond.js dost't work if you view the page via file:// -->
        <!-- [if lt IE9]>
            <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
            <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
        <![endif]-->
        
    </head>

    <body>

        <div class="container">

            <!-- 页面标题 -->
            <div class="page-header">
                <h1>我的相册</h1>
            </div>

            <!-- 导航菜单可以选择不同的视图 -->
            <ul class="nav nav-tabs">
                <li role="" class="active"><a href="#" id="albums-tab">Albums</a></li>
                <li role=""><a href="#" id="photos-tab">Photos</a></li>
                <li role=""><a href="#" id="slideshow-tab">Slideshow</a></li>
            </ul>
            <br/><br/>

            <!-- 这里是空白的 content，使用模版和JavaScript生成的内容填充 -->
            <div id="content" class="container-fluid" role="main">
            </div>
        </div><!-- /.container -->

        <!-- 这里是模版 -->

        <!-- 这里是相册视图的模版 -->
        <!--
            使用 bootstrap 网格显示相册，通过模版的 {{#each}} 助手代码实现。
            每个相册都用缩略图显示，包含名字和照片数量，通过模版的 {{photos.length}} 表达式实现。
        -->
        <script id="albums-template" type="text/x-handlebars-template">
            <div class="row">

                {{#each albums}}

                <div class="col-xs-12 col-md-3">
                    <div class="album-thumbnail" data-id="{{@index}}">
                        <img class="crop-img" src="{{thumbnail}}" alt=""/>

                        <div class="caption">
                            <h4> {{name}} </h4>
                            <p>{{photos.length}} photos</p>
                        </div>
                    </div>
                </div><!-- / col -->

                {{/each}}
            </div><!-- / row -->
        </script>

        <!-- 这里是单个相册中照片的视图模版 -->
        <!--
            如同相册视图那样，使用 bootstrap 网格显示相册中的每个照片、名字、说明
        -->
        <script id="photos-template" type="text/x-handlebars-template">
            <div class="row">
                <!-- xs-12: 小屏幕设备显示一个相册，使用12个格子 -->
                <!-- md-3: 中等尺寸及以上的设备每个相册占用3个格子显示 -->

                {{#each photos}}
                <div class="col-xs-12 col-md-3">
                    <div class="photo-thumbnail" data-id="{{@index}}">
                        <img class="crop-img" src="{{src}}" alt=""/>

                        <div class="caption">
                            <h3>{{title}}</h3>
                            <p>{{description}}</p>
                        </div>
                    </div>
                </div><!-- / col -->
                {{/each}}
            </div><!-- / row -->
        </script>

        <!-- 这里是单个照片视图的模版 -->
        <!-- 此模版显示的是大图、标题、说明 -->
        <script id="photo-template" type="text/x-handlebars-template">
            <div class="row">
                <div class="col-xs-12 col-md-12">
                    <img class="large-img" src="{{src}}" alt=""/>

                    <div class="caption">
                        <h3>{{title}}</h3>
                        <p>{{description}}</p>
                    </div>
                </div><!-- / col -->
            </div><!-- / row -->
        </script>

        <!-- 这里是滑动显示图片的模版 -->
        <!--
            使用轮播（carousel）视图，是一种复杂的模版
        -->
        <script id="slideshow-template" type="text/x-handlebars-template">
            <div class="row">
                <div class="col-md-6">

                    <div id="carousel-example-generic" class="carousel slide" data-ride="carousel">

                        <ol class="carousel-indicators">
                            <li data-target="#carousel-example-generic" data-slide-to="0" class="active"></li>
                            <li data-target="#carousel-example-generic" data-slide-to="1"></li>
                            <li data-target="#carousel-example-generic" data-slide-to="2"></li>
                        </ol>

                        <!-- 打包滑动相册 -->
                        <div class="carousel-inner" role="listbox">

                            {{#each photos}}
                            <div class="item {{#if @first}}active{{/if}}">
                                <img class="carousel-img" src="{{src}}" alt=""/>
                                <div class="carousel-caption">
                                    Image caption
                                </div>
                            </div><!-- / carousel item -->
                            {{/each}}
                        </div>

                        <!-- 这里是控制方法 -->
                        <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
                            <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
                            <span class="sr-only">Previous</span>
                        </a>
                        <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
                            <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
                            <span class="sr-only">Next</span>
                        </a>
                    </div>

                </div> <!-- / carousel -->
            </div> <!-- / col -->
        </script> <!-- /row -->
    </body>
</html>
```

- `<meta>` 提供了HTML文档的元数据，通常用于指定网页的描述、关键词、文件的最后修改时间、作者等信息。其内的信息可以被浏览器、搜索引擎或其他Web服务调用。

```html
<!-- 用于搜索关键词 -->
<meta name="keyworks" content="HTML, CSS, XML, XHTML, Javascript">

<!-- 定义Web页面描述 -->
<meta name="description" content="Free Web tutorials on HTML and CSS">

<!-- 定义页面作者 -->
<meta name="author" content="Hege Refsnes">

<!-- 每30秒刷新页面 -->
<meta http-equiv="refresh" content="30">
```

- `<meta>` 新属性：

[Untitled](https://www.notion.so/f47a8062755f47eca31a93fea13d9519)

[用于移动端显示优化的 viewport 属性](https://www.notion.so/a6c441166080408981f6ae5de0a72274)

### 关于 {{#if }} {{/if}} 的用法

（参考的 ember.js）

在模版中，可以使用 `if` 有条件的呈现内容。有两种样式的 `if` ：块（block）和内联（inline）。

```jsx
//块（block）样式
{{#if this.thingIsTrue}}
	Content for the block form of "if"
{{/if}}

//内联（inline）样式
<div class={{if this.thingIsTrue "value-if-true" "value-if-false"}}
	This div used the inline "if" to calculate the class to use.
</div>
```

### 🧠思考

以下有两个关于用户名的组件：

```jsx
<!-- 组件1 -->
<h4 class="username">
	Tomster
	<span class="local-time">their local time is 4:56pm</span>
</h4>

<!-- 组件2 -->
<h4 class="username">
	Zoey
</h4>
```

第一个组件显示了有关用户本地时间的额外信息。

如果 `Username` 标签没有指定  `@localTime` 参数，那么 `their local time is` 在屏幕上将是一个不完整的文本。

显示本地时间的方法（如果 `@localTime` 被指定的话），可以使用 `if` 。

```jsx
<h4 class="username">
	{{@name}}
	{{#if @localTime}}
		<span class="local-time">their local time is {{@localTime}}</span>
	{{/if}}
</h4>
```

Albums.js 文件代码:

```jsx
//这个文件包含了data数据。 “gallery” 包含了一个数组，数组中有每个相册的图片、名称、缩略图等内容

var gallery = {
	albums : [
		{
			name: "Travels",
			thumbnail: "images/img_1.jpg",
			photos: [
				{
					src: "images.img_1.jpg",
					title: "grafitti",
					description: "some derelict appartments with grafitti"
				},
				{
					src: "images/img_6.jpg",
					title: "fountain",
					description: "a huge dragon fountain"
				},
				{
					src: "images/img_7.jpg",
					title: "images/img_8.jpg",
					description: "an interesting interior"
				}
			]  //photos数组结束
		},  //albums数组中元素结束
		{
			name: "Equipment",
			thumbnail: "images/img_4.jpg",
			photos: [
				{
					src: "images/img_4.jpg",
					title: "syths",
					description: "all workshops should aspire to being this tidy"
				},
				{
					src: "images/img_9.jpg",
					title: "helmet",
					description: "a sci-fi helmet"
				},
				{
					src: "images/img_12.jpg",
					title: "drums",
					description: "a rather nice drum kit"
				}
			]
		},
		{
			name: "English Winter",
			title: "images/img_17.jpg",
			photos: [
				{
					src: "images/img_16.jpg",
					title: "dog in the snow",
					description: "looks like he needs that jacket"
				},
				{
					src: "images/img_17.jpg",
					title: "winter",
					descripthon: "a  snowy scene in a park"
				},
				{
					src: "images/img_18.jpg",
					title: "frosty pond",
					description: "some ducks feeling cold"
				}
			]
		}
	]  //albums数组结束
};  //gallery变量结束
```

gallery.js 代码：

```jsx
/* 这个文件包含了 JavaScript 代码 */

//所有模版的变量在页面载入的时候进行一次性解析，并可以在随后随时使用很多次
var albums_template, photos_template, photo_template, slideshow_template;

//存储当前显示的相册和照片的变量
var current_album = gallery.albums[0];
var current_photo = current_album.photos[0];

//实例化模板并在内容 div 中显示结果的辅助函数
function showTemplate(template, data) {
	var html = template(data);
	$('#content').html(html);
}

//document read 在整个文档加载时被调用，所以我们把大部分需要运行的代码放在这里
$(document).ready(function() {

	//解析所有的模版并准备使用
	var source = $("#albums-template").html();
	albums_template = Handlebars.compile(source);

	source = $("#photos-template").html();
	photos_template = Handlebars.compile(source);

	source = $("#photo-template").html();
	photo_template = Handlebars.compile(source);

	source = $("#slideshow-template").html();
	slideshow_template = Handlebars.compile(source);

	//点击缩略图tab时显示所有的缩略图
	$("#albums-tab"),click(function () {
		
		//显示albums 模版
		showTemplate(albums_template, gallery);

		//使 albums tab 成为 active 激活状态
		//首先将当前活动的标签设为不活动
		$(".nav-tabs .active").removeClass("active");
		//然后将 albums tab 设为active
		$("#albums-tab").addClass("active");

		//向每个相册缩略图添加一个点击回调，以显示该相册中的照片模板
		//（为了清楚起见，我已经为此函数编写了代码，但实际上它与photos选项卡功能几乎相同，
		//因此我们实际上可以只调用$(".photo-thumbnail").click()）
		$(".album-thumbnail").click(function () {
			
			//获得被点击的相册在数组中的索引
			// “this” 是被点击的元素，data("id")获得 data-id 属性，即之前设置的相册在数组中的索引
			var index = $(this).data("id");

			//将当前相册设置为此相册
			current_album = gallery.albums[index];

			//显示照片们的模版
			showTemplate(photos_template, current_album);

			////在所有照片缩略图上添加一个单击按钮，以缩略图形式在弹出窗口中显示该照片
			$(".photo-thumbnail").click(function () {

				//获得被点击的照片的索引
				// “this” 是被点击的元素，data("id")获得 data-id 属性，即之前设置的相册在数组中的索引
				var index = $(this).data("id");

				//将当前相册设置为此相册
				current_photo = current_album.photo[index];

				//显示单独图片的模版
				showTemplate(photo_template, current_photo);
			});
		});
	});

	//点击 photos tab 后，显示当前相册的所有照片
	$("#photos-tab").click( function () {

		//显示照片们的模版
		showTemplate(photos_template, current_albums);

		//将 photos tab 设为当前活动状态
		//首先要移除非当前项的 active
		$(".nav-tabs .active").removeClass("active");

		//然后将 photos tab 设为 active
		$("#photos-tab").addClass("active");

		//向每个相册缩略图添加一个点击回调，以显示照片的弹出式模态框
		$(".photo-thumbnail").click(function () {
			
			//获得被点击照片的索引
			//“this” 是被点击的元素，data("id")获得 data-id 属性，即之前设置的相册在数组中的索引
			var index = $(this).data("id");

			//将当前照片设为此照片
			current_photo = current_album.photos[index];

			//显示单独照片的模版
			showTemplate(photo_template, current_album);
		});
	});

	//以滑动展示为显示方式显示被点击的相册
	$("#slideshow-tab").click(function() {
	
		//显示当前相册的滑动展示模版
		showTemplate(slideshow_template, current_album);

		//使 slideshow tab 成为 active 状态
		//首先移除其他项的 active 状态
		$(".nav-tabs .active").removeClass("active");

		//将 slideshow tab设为 active 状态
		$("#slideshow-tab").addClass("active");
	});

	//通过显示相册视图来开始页面，我们可以通过虚拟地单击相册选项卡来完成此操作
	$("albums-tab").click();

});
```

### 嵌套的数据结构：

```jsx
albums: [
		{
				name: "Travels",
				photos: [
						{
						src: "images/img_1.jpg",
						title: "grafitti"
						},  //photos数组中元素结束
						...
				]  //photos数组结束
		}  //albums数组元素结束
		...
]  //albums数组结束
```

### 可以通过将数组放在其他数组内部的对象中来构建复杂的嵌套的数据

### 本例中的albums也有“元数据“，比如标题、作者。所以最好让它成为一个包含数组的对象

**虽然本例确实为相册和照片使用了单独的模版，但是可以在另一个 {{#each}} 中包含一个 {{#each}} 来将它们组合成一个模版，以在单个模版中显示两者。**

**虽然照片是一个数组，它可以像对象一样拥有成员变量，但所有数组都有成员变量“length” （实际上，在幕后数组是一种特殊类型的对象）。**

**#if 有点像if语句，所以它可以在不同情况下打开和关闭渲染。**

总结**:**