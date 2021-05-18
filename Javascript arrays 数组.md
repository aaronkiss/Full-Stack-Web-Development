# Javascript arrays 数组

Created: May 14, 2021 9:35 PM
Tags: Front-side, JavaScript, Web, html

### 要点回顾

### 随堂笔记

- 数组在JS中是全局对象，用于构造数组，类似于列表
- 具有执行遍历和变异操作的方法
- 其长度和元素类型均未固定
- 数组的长度可以随时更改，并且数据可以存储在数组中的非连续位置
- 可以使用类型化数组来代替
- 不能使用字符串作为元素索引，必须使用整数
- 数组的对象属性和数组元素列表是分开的，数组的遍历和变异操作不能应用与这些命名属性

```jsx
//创建数组
let fruits = [ 'Apple', 'Banana']
console.log(fruits.length)
//2

//使用索引位置访问数组项
let first = fruits[0]
//Apple
let last = fruits[fruits.length - 1]
//Banana

//遍历数组
fruits.forEach（function(item, index, array) {
		console.log(item, index)
})
//Apple 0
//Banana 1

//将项目添加到数组末尾
let newLength = fruits.push('Orange')
// ["Apple, "Banana", "Orange"]

//从数组末尾删除项目
let last = fruits.pop() //删除Orange
// ["Apple", "Banana"]

//从数组开头删除项目
let first = fruits.shift() //删除Apple
// ["Banana"]

//将项目添加到数组开头
let newLength = fruits.unshift('Strawberry')
// ["Strawberry", "Banana"]

//在数组中找到项目的索引
fruits.push('Mango')
let pos = fruits.indexOf('Banana')
// 1

//按索引位置删除项目
let removedItem = fruits.splice(pos, 1) //删除第2个项目
// ["Strawberry", "Mango"]

//从索引位置删除项目
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot']
console.log(vegetables)
// ["Cabbage", "Turnip", "Radish", "Carrot"]
let pos = 1
let n = 2
letremovedItems = vegetables.splice(pos, n)
console.log(vegetables)
// ["Cabbage", "Carrot"] 原始数组发生变化
console.log(removedItems)
// ["Tuenip", "Radish"]

//复制阵列
let shallowCopy = fruits.slice()
```

- Javascript的数组索引是0开头，所以最后一个索引是数组长度-1。

### 访问数组元素

使用无效的索引号将返回 `undefined` 。

```jsx
let arr = ['this is the first element', 'this is the second element', 'this is the last element']
console.log(arr[0])
console.log(arr[1])
console.log(arr.length - 1)
```

数组元素是对象属性，其使用方式与属性相同 `toString` (具体而言， `toString` 是一种方法）。但一下方式访问数组的元素是错误的❌

```jsx
console.log(arr.0)    // ❌错误的访问方式
```

以数字开头的Javascript属性不能以点表示法引用，必须用方括号访问。

```jsx
let years = [1950, 1960, 1970, 1980, 1990, 2000, 2010]
console.log(years.0)    // ❌错误访问
console.log(years[0])    // ✅正确访问

renderer.3d.setTexture(model, 'character.png')    // 错误❌引用
renderer['3d'].setTexture(model, 'character.png')    // ✅正确引用
```

在上面例子中， `'3d'` 必须加引号，因为它以数字开头。但是也可以使用数组索引。

Javascript引擎通过隐式转换将 `years[2]` 里的 `2` 强制 `toString` 为字符串 。其结果是， `'2'` 与 `'02'` 将引用两个不同的 years 对象。一下代码可以成立：

```jsx
console.log(years['2'] != years['02']
```

完整的访问数组元素实例：

```jsx
<html>
<body>

<p id="demo"></p>  //这里将由Javascript代码的输出结果填充

<script>
		var cars = ["Audi", "BMW", "Porsche"];  //声明数组
		document.getElementById("demo").innerHTML = cars[0];  //输出第1个元素到demo
</script>

</body>
</html>
```

### Javascript 显示方案：

- 使用 `window.alert()` 写入警告框
- 使用 `document.write()` 写入HTML输出
- 使用 `innerHTML` 写入HTML元素
- 使用 `console.log()` 写入浏览器控制台

如果需要访问HTML元素，可使用 `document.getElementById(id)` 方法。 `id` 属性定义HTML元素， `innerHTML` 属性定义HTML内容。

### Javascript数值方法

原始值（比如3.14或2016）无法拥有属性和方法，因为它们不是对象。

但通过Javascript，方法和属性也可用于原始值，因为Javascript在执行的时候可以将原始值视作对象。

**toString()** 

以字符串返回数值。

```jsx
var x = 123;
x.toString();    //从变量x返回123
(123).toString;    //从文本123返回123
(100 + 23).toString();    //从表达式返回123
```

**toExponential()**

返回字符串，它包含已被四舍五入并使用指数计数法的数字。参数定义小数点后的位数。

```jsx
var x = 9.656;
x.toExponential(2);    //返回9.66e+0
x.toExponential(4);    //返回9.6560e+0
x.toExponential(6);    //返回9.656000e+0
```

**toFixed()**

返回字符串，参数定义了小数点后的位数。 `toFixed(2)` 适合处理金钱数字。

**toPrecision()**

返回字符串，参数指定数字的长度。

**valueOf()**

以数值返回数值。

### 全局方法

[Untitled](https://www.notion.so/5f7141623c704979bb4765683bc95893)

### 数值属性

[Untitled](https://www.notion.so/862ff6bd7bc94e909685d561573bcbec)

### 长度与数值特性之间的关系

`length` 属性返回数组长度。

遍历数组元素：

```jsx
<p id="demo"></p>

var fruits, text, fLen, i;
fruits = ["Banana", "Orange", "Apple", "Mango"];
fLen = fruits.length;
text = "<ul>";
for (i = 0; i < fLen; i++) {
		text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>"
document.getElementById("demo").innerHTML = text;
```

另一种方法 forEach()函数：

```jsx
var fruits, text;
fruits = ["Banana", "Orange", "Apple", "Mango"];

text = "<ul>";
fruits.forEach(myFunction);
text += "</ul>";

function myFunction(value) {
		text += "<li" + value + "</li>";
}
```

*具有命名索引的数组被称为关联数组或散列。但是Javascript并不支持关联数组。Javascript只支持以数字索引的数组。*

- **在Javascript中，数组使用数字索引，对象使用命名索引。**
- **避免使用 new Array()，因为会产生不可预期的结果。**

```jsx
var points = new Array(40,100);  //创建包含两个元素的数组

var points = new Array(40);  //创建包含40个为定义元素的数组！！！要疯了！！！
```

### 如何识别数组

- 通过 `typeof` 检查数组，若返回 `object` 则为数组。
- 使用 `Array.isArray()` 检查数组，若返回 `true` 则为数组。

```jsx
<p id="demo"></p>

<script>
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = Array.isArray(fruits);
</script>
```

- 若对象由给定的构造器创建，则 `instanceof` 会返回 true。

```jsx
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits instanceof Array;    //返回true
```

### 数组方法

`toString()` 把数组转换为数组值以逗号分隔的字符串。

```jsx
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();
//返回 Banana,Orange,Apple,Mango
```

`join()` 可将所有数组元素结合为一个字符串。

```jsx
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join("*");
//返回 Banana*Orange*Apple*Mango
```

`pop()` 意思是从数组中弹出元素，即删除最后一个元素。

```jsx
<p id="demo1"></p>
<p id="demo2"></p>
<p id="demo3"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = fruits;
document.getElementById("demo2").innerHTML = fruits.pop();
document.getElementById("demo3").innerHTML = fruits;
```

`push()` 意思是向数组中推入元素，即在数组末尾添加一个元素。

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo1"></p>
<p id="demo2"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];

function myFunction() {
		document.getElementById("demo2").innerHTML = fruits.push("Lemon");
		document.getElementById("demo1").innerHTML = fruits;
}
```

`shift()` 会删除首个元素，而不是最后一个，剩余元素位移到更底的索引。

```jsx
<p id="demo1"></p>
<p id="demo2"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = fruits.shift();
document.getElementById("demo2").innerHTML = fruits;
```

`unshift()` 是 `shift()` 的逆向操作。

由于数组是对象，因此可以使用 `delete` 删除数组中的元素，但是会留下空洞（即没有元素的空白索引）。

`splice()` 可用于向数组添加新元素。

```jsx
<button onclick="myFunction()">Try me</button>

<p id="demo1"></p>
<p id="demo2"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo1").innerHTML = "原数组: <br>" + fruits;

function myFunction() {
		fruits.splice(2,0, "Lemon", "Kiwi");
		document.getElementById("demo2").innerHTML = "新数组: <br>" + fruits;
}
```

`splice(添加元素的索引位置, 删除元素的数量, 要添加的元素……)` 

用 `splice()` 巧妙的删除元素：

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];

function myFunction() {
		fruits.splice(0, 1);  //删除第一个元素，并且不添加任何新元素
		document.getElementById("demo").innerHTML = fruits;
}
```

`concat()` 通过合并现有数组来创建一个新数组。

```jsx
<p id="demo"></p>

var myGirls = ["Emma", "Isabella"];
var myBoys = ["Jacob", "Michael", "Ethan"];
var myChildren = myGirls.concat(myBoys);

document.getElementById("demo").innerHTML = myChildren;
```

`concat()` 不会更改现有数组，它总是返回一个新数组，并且可以使用任意数量的数组参数。

```jsx
<p id="demo"></p>

var arr1 = ["Cecilie", "Lone"];
var arr2 = ["Emil", "Tobias", "Linus"];
var arr3 = ["Robin", "Morgan"];

document.getElementById("demo").innerHTML = arr1.concat(arr2, arr3);
```

`concat()` 可以将值合并到数组。

```jsx
<p id="demo"></p>

var arr1 = ["Emma", "Isabella"];
var myChildren = arr1.concat(["Jacob", "Michael", "Ethan"]);
document.getElementById("demo").innerHTML = myChildren;
```

`slice()` 用数组的某个片段切出新数组。

```jsx
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1);  //从原数组的第二个元素开始切出新数组，原数组不变
document.getElementById("demo").innerHTML = fruits + "<br><br>" + citrus;
```

`slice()` 创建新数组，它不会从原数组中删除任何元素。

`slice()` 可以接受两个参数。**第1个参数是开始的索引，第2个参数是结束的索引（不包括）。**

```jsx
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1, 3);  //切出原数组的第2个、第3个元素
document.getElementById("demo").innerHTML = fruits + "<br><br>" + citrus;
```

Javascript支持自动 `toString()` 。所有Javascript对象都支持自动 `toString()` 。

```jsx
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;
```

### 数组排序

`sort()` 是最强大的数组方法之一。其以字母顺序对数组进行排序。**对数字排序无效。**

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;

function myFunction() {
		fruits.sort();
		document.getElementById("demo").innerHTML = fruits;
}
```

`reverse()` 可以**降序**排列数组。

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits;

function myFunction() {
		fruits.sort();
		fruits.reverse();
		document.getElementById("demo").innerHTML = fruits;
}
```

用 `sort()` 对数字进行排序需要用**比较函数**来修正此问题。

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;

function myFunction() {
		points.sort(function(a, b){return a - b});
		document.getElementById("demo").innerHTML = points;
}
```

同样也可以进行降序数字排序。

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;

function myFunction() {
		points.sort(function(a, b) {return b - a});
		document.getElementById("demo").innerHTML = points;
}
```

### 当 `sort()` 函数比较两个值时，会将值发送给比较函数，并根据所返回的值（正、负、零）对这些值进行排序。

```jsx
<button onclick="myFunction1()">按字母排序</button>
<button onclick="myFunction2()">按数字排序</button>
<p id="demo"></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;

function myFunction1() {
		points.sort();
		document.getElementById("demo").innerHTML = points;
}
function myFunction2() {
		points.sort(function(a, b){return a - b});
		document.getElementById("demo").innerHTML = points;
}
```

### 随机排序：

```jsx
<button onclick="myFunction()">Try me</button>
<p id="demo"></p>

function myFunction() {
		points.sort(function(a, b){return 0.5 - Math.random()});
		document.getElementById("demo").innerHTML = points;
}
```

### 查找最大值、最小值

Javascript不提供查找数组中最大值最小值的内建函数。

**对数组元素排序后可以使用索引来获得最大值、最小值。**

```jsx
<p>最低值是： <span id="demo1"></span></p>
<p>最大值是： <span id="demo2"></span></p>

var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});  //升序排列
document.getElementById("demo1").innerHTML = points[0];

points.sort(function(a, b){return b - a});  //降序排列
document.getElementById("demo2").innerHTML = points[0];

```

### 对数组使用 `Math.max()`

可以使用 `Math.max.apply` 查找数组中的最高值。

```jsx
<p>最高值是： <span id="demo"></span></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = myArrayMax(points);

function myArrayMax(arr) {
		return Math.max.apply(null, arr);
}
```

`Math.max.apply([1, 2, 3])` 等效于 `Math.max(1, 2, 3)` 。

### 对数组使用 `Math.min()`

可以使用 `Math.min()` 查找数组中的最低值。

```jsx
<p>最低值： <span id="demo"></span></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = myArrayMin(points);

function myArrayMin(arr) {
		return Math.min.apply(null, arr);
}
```

`Math.min.apply([1, 2, 3])` 等效于 `Math.min(1, 2, 3)` 。

### 自定义的Max / Min 方法

此函数遍历数组，用找到的最高值与每个值进行比较。

```jsx
<p>最高值是： <span id="demo"></span></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = myArrayMax(points);

function myArrayMax(arr) {
		var len = arr.length;
		var max = -Infinity;
		while (len--) {
				if (arr[len] > max) {
						max = arr[len];
				}
		}
		return max;
}
```

```jsx
<p>最低值是： <span id="demo"></span></p>

var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = myArrayMin(arr);

function myArrayMin(arr) {
		var len = arr.length;
		var min = Infinity;
		while (len--) {
				if (arr[len] < min) {
						min = arr[len];
				}
		}
		return min;
}
```

### 排序对象数组

Javascript数组经常会包含对象。

即使对象拥有不同数据类型的属性， `sort()` 仍可用于对数组排序，方法就是用**比较函数**。

```jsx
<p>点击按钮按年份对汽车进行排序： </p>
<button onclick="myFuncton()">排序</button>
<p id="demo"></p>

var cars = [
						{type:"BMW", year:2017},
						{type:"Audi", year:2019},
						{type:"porsche", year:2018}
						];

displayCars();

function myFunction() {
		cars.sort(function(a, b){return a.year - b.year});
		displayCars();
}

function displayCars() {
		document.getElementById("demo").innerHTML = 
																				cars[0].type + " " + cars[0].year + "<br>" + 
																				cars[1].type + " " + cars[1].year + "<br>" +
																				cars[2].type + " " + cars[2].year;
}
```

**比较字符串**会稍麻烦：

```jsx
<p>点击按钮按车型对汽车排序</p>
<button onclick="myFunction()">排序</button>
<p id="demo"></p>

var cars = [
						{type:"BMW", year:2017},
						{type:"Audi", year:2019},
						{type:"porsche", year:2018}
						];

displayCars();

function myFunction() {
		cars.sort(function(a, b) {
				var x = a.type.toLowerCase();
				var y = b.type.toLowerCase();
				if (x < y) { return -1;}
				if (x > y) { retuen 1;}
				return 0;
		});
		displayCars();
}

function displayCars() {
		document.getElementById("demo").innerHTML = 
							cars[0].type + " " + cars[0].year + "<br>" +
							cars[1].type + " " + cars[1].year + "<br>" +
							cars[2].type + " " + cars[2].year;
}
```

### 数组迭代

数组迭代对数组内的每个元素进行操作。

`forEach()` 为每个数组元素调用一次函数。其接受三个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);
document.getElementById("demo").innerHTML = txt;

function myFunction(value, index, array) {
		txt = txt + value + "<br>";
}
```

可重写为：

```jsx
<p id="demo"></p>

var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);
document.getElementById("demo").innerHTML = txt;

function myFunction(value) {
		txt = txt + value + "<br>";
}
```

`map()` 通过对每个数组元素执行函数来创建新数组，且不会对没有值的数组元素执行，也不会更改原始数组。

该函数有三个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers1 = [45, 4, 9, 16, 25];
var bumbers2 = numbers1.map(myFunction);

document.getElementBiId("demo").innerHTML = numbers2;

function myFunction(value, index, array) {
		return value * 2;
}
```

`filter()` 创建一个包含通过测试的数组元素的新数组，类似于“滤镜”。

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var over18 = numbers.filter(myFunction);

document.getElementById("demo").innerHTML = over18;

function myFunction(value, index, array) {
		return value > 18;
}
```

`reduce()` 在每个数组元素上运行函数，以生成（减少它）单个值，其运行顺序是**从左到右**，且不会减少原始数组。该函数接受4个参数：总数（初始值/先前返回值），项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduce(myFunction);

document.getElementById("demo").innerHTML = "总和是：" + sum;

function myFunction(total, value, index, array) {
		return total + value;
}
```

该函数接受一个初始值：

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduce(myFunction, 100);

document.getElementById("demo").innerHTML = "总和是：" + sum;

function myFunction(total, value) {
		return total + value;
}
```

`reduceRight()` 在每个数组元素上运行函数，以生成（减少它）单个值。其运行顺序是**从右往左**，并且不会减少原始数组。

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduceRight(myFunction);

document.getElementById("demo").innerHTML = "总和是：" + sum;

function myFunction(total, value, index, array) {
		return total + value;
}
```

`every()` 检查**所有数组元素**是否全部通过测试。其接受3个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction);

document.getElementById("demo").innerHTML = "所有大于18的是：" + allOver18;

function myFunction(value, index, array) {
		return value > 18;
}
```

该函数返回值为true或false，表示是否全部通过测试。

`some()` 检查**某些数组**元素是否通过测试。其接受3个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers = [45, 4, 9, 16, 25];
var someOver18 = numbers.some(myFunction);

document.getElementById("demo").innerHTML = "某些值大于18: " + someOver18;

function myFunction(value, index, array) {
		return value > 18;
}
```

`indexOf()` 在数组中搜索元素值并返回其索引。两个参数：要检索的元素，开始搜索的位置（负值将从结尾开始的给定位置搜索到结尾）。若未找到项目，该函数会返回-1。

```jsx
<p id="demo"></p>

var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
document.getElementById("demo").innerHTML = "Apple 被找到的位置是：" + (a + 1);
```

`lastIndexOf()` 与 `indexOf()` 类似，只不过是从数组结尾开始搜索。

```jsx
<p id="demo"></p>

var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.lastIndexOf("Apple");
document.getElementById("demo").innerHTML = "Apple is found in position " + (a + 1);
```

`find()` 返回通过测试函数的第一个数组元素的值。该函数接受3个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

document.getElementById("demo").innerHTML = "大于 18 的第一个值是：" + first;

function myFunction(value, index, array) {
		return value > 18;
}
```

`findIndex()` 返回通过测试函数的第一个数组元素的索引。3个参数：项目值，项目索引，数组本身。

```jsx
<p id="demo"></p>

var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

document.getElementById("demo").innerHTML = "大于 18 的第一个值的索引是：" + first;

function myFunction(value, index, array) {
		reruen value > 18;
}
```

总结**:**