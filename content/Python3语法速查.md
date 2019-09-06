Title: Python3语法速查
Date: 2019-09-06
Category: Python
Tags: Python

> ### 一. 变量

*变量就像一个盒子，你可以把具体的内容装进去。变量需要一个名字，例如：x，然后需要给她装点东西，装东西的方法很简单，用=符号，如果我们想把1装进x里面，像这样：x=1。*

1. 我想创建整数变量

```python
x = 1 # 现在x里面装的是整数1
y = 2 # 现在y里面装的是整数2
```

2. 我想创建字符串变量

```python
h = '你好' # 现在h里面装的是字符串'你好'
name = '王小明' # 现在name里面装的是字符串'王小明'
```

3. 我想创建一个新变量，用另外一个变量初始化他
```python
x = 13
y = x
```

> ### 二. 类型

*python支持自己定义类型，不过python也有预先定义好的类型，最基础的是：整数（int），小数或者浮点数（float），字符串（str），布尔（bool），空（NoneType），数组（list），字典（dict）。这些都是经常会用到的类型。*

*那么类型到底是什么呢，为什么要区分类型呢。首先是存放的方式不同，python对不同的内容需要采用不同的保存方式，就像水用桶装装盖个盖子就好了，酒需要密封，冰就需要隔热。所以python首先需要区分出类型然后根据类型设计存放的方式。然后是使用的方式不同，水可以用来洗完洗衣粉，煮饭。酒一般只是用来饮用。冰用来冷敷伤口。整数和小数可以进行加减乘除运算，字符串就不行。*

*这里重点说一下布尔型，不同于整数，字符串有无数的值，布尔型只要两个值，真（True）和假（False）。当我们需要进行判断的时候我们就需要布尔型了。*

1. 我怎么知道一个变量是什么类型，可以使用函数type。
```python
x = 1
print(type(x)) # 输出<class 'int'>，表示是整数
x = 1.0
print(type(x)) # 输出<class 'float'>，表示是小数
x = 'hello'
print(type(x)) # 输出<class 'str'>，表示是浮点数
x = True
print(type(x)) # 输出<class 'bool'>，表示是布尔型
x = None
print(type(x)) # 输出<class 'NoneType'>，表示是空
x = [1,2,3,4]
print(type(x)) # 输出<class 'list'>，表示是数组
x = {
    "name":"小明",
    "age":"13",
}
print(type(x)) # 输出<class 'dict'>，表示是字典
```

2. 怎么把小数转变成整数，使用函数int。
```python
x = 1.0
print(type(x)) # 输出<class 'float'>
y = int(x)
print(type(y)) # 输出<class 'int'>
```
3. 怎么把字符串变成整数，用函数int。
```python
x = '2019'
print(type(x)) # 输出<class 'str'>
y = int(x)
print(type(y)) # 输出<class 'int'>
```
4. 怎么把其他类型变成字符串，用函数str。
```python
x = 1
y = str(1)
print(type(y)) # 输出<class 'str'>
```
5. 怎么把其他类型变成布尔型，用函数bool。
```python
x = 1
y = bool(1)
print(type(y)) # 输出<class 'bool'>
```
