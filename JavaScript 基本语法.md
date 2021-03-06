# JavaScript 基本语法
```javascript
//每行代码结尾必须加 分号 “；”
console.log()；    //打印括号内的内容

//这是单行注释
/*
这是
多行
注释
*/


```

## 数据类型
一共7种：
- 数字，包含整数、浮点数字
- 字符串，通常用单引号‘’或双引号“”标示
- 布尔，只有两个值：True或False
- Null，标示缺少值
- undefined,标示缺少值，但与Null不同
- 符号（symbol）
- 对象（object），是相关数据的集合

```javascript
console.log('Teaching the code'.length);
//length() 表示计算前边字符串的字符个数（长度）

console.log('hello'.toUpperCase());
//toUpperCase() 表示所有字母都大写

console.log('Hey'.startsWith('H'));
//startsWith 表示判断前面字符串的开头是以“H”开头

console.log('   Remove whitespace   '.trim());
//trim() 表示删除前面字符串的首尾空格

```

## 内建对象

```javascript
console.log(Math.random());
//调用Math里的random()随机函数输出0～1之间的随机数字

console.log(Math.random() * 50);
//输出1～50之间的随机数

console.log(Math.floor(Math.random() * 50));
//floor() 表示取一个十进制数字，并四舍五入为一个整数。

console.log(Math.ceil(43.8));
//ceil() 表示输出大于参数值的最小整数。此处为44

console.log(Number.isInteger(46.78));
//isInteger() 表示判断参数是否为整数，此处为False。


```

## if else语句

```javascript
let sale = true;

sale = false;

if(sale) {
  console.log('Time to buy!');
} else {
  console.log('Time to wait for a sale.');
}
```

## 比较运算符

符合|含义
:--:|:--:
`<`|小于
`>`|大于
`<=`|小于等于
`>=`|大于等于
`===`|判断等于
`!==`|不等于

## 逻辑运算符

|符号|含义|
|:--:|:--:|
|`&&` | 和 |
| `｜｜`  | 或 |
|`!` | 采用true而返回false|


- 尽管变量值不是显性的，但是在布尔或条件上下文中使用的时候已为它分配了一个**非伪造的**值True，那么if语句中的代码块依然会运行。  

哪些是**非伪造的值**呢？
- `0`
- 空白的字符串例如`“”`或`‘’`
- `null`
- `undefined`
- `NaN`,或者“Not a Number”

```javascript
let bumberOf Apples = 0;

if (numberOfApples){
    console.log('Let us eate apples!');
    } else {
    console.log('No apples left!');
    }
    
//输出 “No apples left!”
```

## 短路评估(Short Circuit Evaluation)
使用短小的代码表达选择逻辑。

```javascript {.line-numbers}
let defaultName;
if (username) {
  defaultName = username;
} else {
  defaultName = 'Stranger';
}
```

等价于

```javascript {.line-numbers}
let defaultName = username || 'Stranger';
```

## 三元运算符(Ternary Operator)

```javascript
let isNightTime = true;
if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```

等价于

```javascript
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```

另一个例子

```javascript
let favoritePhrase = 'Love That!';
if (favoritePhrase === 'Love That!') {
  console.log('I love that!');
} else {
  console.log('I don't love that!');
}
```

等价于

```javascript
let favoritePhrase = 'Love That!';

favoritePhrase === 'Love That!' ? console.log('I love that!') : console.log('I don't love that!');
```

