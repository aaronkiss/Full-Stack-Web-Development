# Handlebars 相关

Created: May 30, 2021 2:47 PM
Tags: Design, Front-side, Handlebars, JavaScript, Web

### 要点回顾

### 参考网站

[https://handlebarsjs.com/zh/api-reference/data-variables.html#first](https://handlebarsjs.com/zh/api-reference/data-variables.html#first)

### 随堂笔记

Handlebars 是一个js的语义模版库，通过view和data的分离来快速构建Web模版。

其采用“Logic-less template“（弱逻辑模版）的思路，并兼容Mustache，可以在Handlebars中导入Mustache模版。

“弱逻辑“代表这些逻辑性功能只能由某些只能标签来完成（例如：数组迭代、条件式渲染等）。

Handlebars是 ember.js / modejs Web框架 Clouda / Meteor 的默认模版引擎。

导入：

```jsx
<script type="text/javascript" src="js/jquery.js"></script>
<script type="text/javascript" src="js/handlebars/handlebars-v3.0.1.js"></script>
```

### 使用的基本逻辑：

1. 使用handlebars一般都是为了解决从后台拿数据，并实现后台数据前端渲染的问题。在未与后台对接时，可以自己用js模拟json数据进行渲染。

模拟的json对象:

```jsx
var data = [
		{"cd-timeline-content": "content_right",
		"cd-detail-date": "date-right",
		"cd-title": "七里香",
		"content_a_href": "#",
		"content_img_src": "../../src/images/jay/1.jpg",
		"cd-data": "2015-01-06",
		"cd-date-clock": "8:00",
		"cd-half-day": "am"}
];
```

2. js的json数据传入handlebars，并渲染需要的html部分，根据需要的div内容实现渲染效果。

handlebars渲染部分：

```jsx
<script id="table-template" type="text/x-handlebars-template">
		{{#each this}}
		<div class="cd-timeline-block">

				<div class="cd-timeline-img cd-picture">
						<img src="../../src/images/MyTrack/3.png" alt="Picture">
				</div>

				<div class="cd-timeline-content {{cd-timeline-content}}">
						<h2>{{cd-title}}</h2>
						<a href="{{content_a_href}}"><img src="{{content_img_src}}"></a>
				</div>

				<div class="cd-detail-date {{cd-detail-date}}">
						<p class="cd-date">{{cd-date}}</p>
						<p class="cd-date-clock">{{cd-date-clock}} &nbsp {{cd-half-day}}</p>
				</div>
		</div>
		{{/each}}
</script>
```

3. 再使用js实现html的替换和渲染

```jsx
var myTemplate = Handlebars.compile($("#table-template").html());
$('#dataList').html(myTemplate(data));
```

4. 逻辑如下

![https://upload-images.jianshu.io/upload_images/1958060-a967fee59581602e.png?imageMogr2/auto-orient/strip|imageView2/2/w/778/format/webp](https://upload-images.jianshu.io/upload_images/1958060-a967fee59581602e.png?imageMogr2/auto-orient/strip|imageView2/2/w/778/format/webp)

### Handlebars的三个使用前奏

1. 引用库
2. 页面数据渲染和实现

```jsx
<script id="tabel-template" type="text/x-handlebars-template">
{{data}}
</script>
```

3. 响应js获取json并渲染（一般使用ajax）

```jsx
<script src="handle.js"></script>

var data = {"data": "data"};
var myTemplate = Handlebars.compile($("#table-template").html());
$('body').html(myTemplate(data));
//这里利用jquery实现对handlebars的编译与页面的实现
var source = "<p>Hello, my name is {{name}}. I am from {{hometown}}. I have "
		 + 
		"{{kids.length}} kids:</p>"
		 + 
		"<ul>{{#kids}}<li>{{name}} is {{age}}</li>{{/kids}}</ul>";
var template = Handlebars.compile(source);
var data = { 
		"name": "Alan",
		"hometown": "Somewhere, TX",
		"kids": [
				{ "name": "Jimmy", "age": "12" },
				{ "name": "Sally", "age": "4" }
		]
};
var result = template(data);
```

### 注释

```jsx
{{! 这是Handlebars的注释 }}
{{!-- 也是注释 --}}
```

### Handlebars内置助手代码

很多时候，我们需要从后台获取数据，然后将数据放在对应页面中，那么就会存在循环、判断等情况，但是通过前面的直接进入数据是不行的，因此就有了Block表达式。

一般形式：

```jsx
{{# block代码}}
{{/block代码}}
```

- **each** block helper    即循环，遍历出列表内容，用this来引用遍历的元素

```jsx
<ul>
		{{#each name}}
		<li>{{this}}</li>
		{{/each}}
</ul>
```

对应的 json

```jsx
{ name: ["html", "css", "javascript"] };
```

- **if else** block helper    即 if/else 语句，使用 {{#if}}、{{#else}} {{/if}} 等进行渲染

```jsx
{{#if list}}
<ul id="list">
		{{#each list}}
		<li>{{this}}</li>
		{{/each}}
</ul>
{{else}}
		<p>{{error}}</p>
</if>

var data = {
		info: [ 'HTML5', 'CSS3', "WebGL"],
		"error": "数据错误:
}
```

- **unless** block helper    与 if 相反

```jsx
{{#unless data}}
<ul id="list">
		{{#each list}}
		<li>{{this}}</li>
		{{/each}}
</ul>
{{else}}
		<p>{{error}}</p>
{{/unless}}
```

- with block helper    会在编译的阶段进行context传递和赋值，用with可以很简单的进入一个数据集合里，查找对应的数据很方便

```jsx
<div class="entry">
		<h1>{{title}}</h1>
		{{#with author}}
		<h2>By {{firstName}} {{lastName}}</h2>
		{{/with}}
</div>

{
		title: "My first post!",
		author: {
				firstName: "Charles",
				lastName: "Jolley"
		}
}
```

### handlebars 自定义标签

其可以使用在Handlebars模版的任何地方，必须使用 `Handlebars.registerHelper` 注册helper。

```jsx
Handlebars.registerHelper('fullName', function(person) {
		return person.firstName + " " + person.lastName;
});
```

使用情景：

```jsx
<div class="post">
		<h1>By {{fullName author}}</h1>
		<div class="body">{{body}}</div>
		<h1>Comments</h1>

		{{#each comments}}
		<h2>By {{fullName author}}</h2>
		<div class="body">{{body}}</div>
		{{/each}}
</div>

//数据
var context = {
		author: {
				firstName: "Alan",
				lastName: "Johnson"
		},
		body: "I Love Handlebars",
		comments: [{
				author: {
						firstName: "Yehuda",
						lastName: "Katz"
				},
				body: "Me too!"
		}
]};

//结果输出
<div class="post">
		<h1>By Alan Johnson</h1>
		<div class="body">I Love Handlebars</div>
		<h1>Comments</h1>
		<h2>By Yehuda Katz</h2>
		<div class="body">Me too!</div>
</div>
```

### handlebars 访问路径（Path）

handlebars支持路径，可以使用嵌套的路径，能够查找嵌套低于当前上下文的属性。

```jsx
.    //访问属性
../  //访问父属性

{
		title: "My First Blog Post!",
		author: {
				id: 47,
				name: "Yehuda Katz"
		},
		body: "My first post. Wheeee!"
};

//访问情况
<h1>{{author.id}}</h1>
{{#with author}}
<h1>{{../title}}</h1>
{{/with}}
```

### @data 变量

由handlebars及其内建助手代码实现。

**@root**    初始化模版被执行时的上下文。Initial context with which the template was executed.

除非特意改变，对于页面渲染时的每一部分，本项的值恒定。

```jsx
{{#each array}} {{@root.foo}} {{/each}}
```

**@first**    会被 `each` 助手代码在迭代的第一步被设置为 `true` 。

```jsx
{{#each array}} {{#if @first}} First! {{/if}} {{/each}}
```

**@index**    从零开始的编号，表示当前的迭代次数。由 `each` 助手代码设置。

```jsx
{{#each array}} {{@index}} {{/each}}
```

**@key**    当前迭代次数的键。在遍历对象时被 `each` 助手代码设置。

```jsx
{{#each array}} {{@key}} {{/each}}
```

**@last**    在迭代的最后一步被 `each` 助手代码设置为 `true` 。

```jsx
{{#each array}} {{#if @last}} Last! {{/if}} {{/each}}
```

**@level**    设定log的输出级别。

可以为以下值： `Handlebars,logger.DEBUG` , `[Handlebars.logger.INFO](http://handlebars.logger.INFO)` , `Handlebars.logger.WARN` , `Handlebars.logger.ERROR` 。

当设定时，程序会按照设定的级别选择输出信息，默认值为 `Handlebars.logger.ERROR` 。

```jsx
template({}, { data: { level: Handlebars.logger.WARN } });
```

总结**:**