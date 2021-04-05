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
|`||` | 或 |
|`!` | 采用true而返回false|
