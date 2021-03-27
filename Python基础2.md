# range()函数
可以产生一组**有规律**的数列。  
格式：range（start,end,step），三个参数至少要具备一个。step默认为1，start默认为0。
返回的是range对象，可以迭代。  

# 循环
- **while语句**
```python
sumA = 0    #赋初值
j = 1     #赋初值
while j < 10:   #循环次数，当j => 10的时候就跳出循环 
    sumA += j
    j += 1
    
sumA
# 返回45
j
# 返回10
```

- **for语句**
for语句运行时获取的是**可迭代对象(iterable_object)**  
可以明确循环的次数，遍历一个数据集内的成员，在列表解析中使用，生成器表达式中使用。
可迭代对象：String,List,Tuple,Dictionary,File
```python
for i in range(3,11,2)
    print(i,end = '')   #执行并不成功

```

### break 终止整个循环

### continue 当条件满足的时候就跳过continue之后的语句，只终止当前的这个循环

# 自定义函数

格式：
```python
def 函数名(x)：   # 如果没参数的化小括号也不能省略
    '函数的注释'   # 通过 “print 函数名.__doc__” 来查看注释
    return（x+x）
```

代码：
```python
from math import sqrt
def isprime(x):
    if x == 1:
        return False
    k = int(sqrt(x))
    for j in range(2,k+1):
        if x % j == 0:
            return False
    return True
for i in range(2,101):
    if isprime(i):
        print(i, end=' ')
```
