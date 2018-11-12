### Swift 变量

##### Swift变量
变量是一种类似于占位符，使用方便，能够方便的引用计算机的内存地址。
Swift每个变量都指定了类型，该类型决定了占用内存的大小，不同的数据类型也可决定存储值的范围。


##### 变量声明
变量声明是告诉编译器在内存中的哪个位置创造多大的内存空间。
声明变量使用关键字 ```var```

```swift
import cocoa

var varA = 10
print(varA)

var varB: Float
varB = 10.0
print(varB)
```

##### 变量命名

- 变量命名可以为字母、数字、下划线组成

```swift
var var_12: Float
var_12 = 10
print(var_12)
```

```swift
// 以下报错Consecutive statements on a line must be separated by ';'
var var_12#: Float 
var_12# = 10
print(var_12#)
```

- 变量名需要字母或者下划线开始

```swift
var _12: Float
_12 = 10
print(_12)
```

```swift
// 以下会报错 'w' is not a valid digit in integer literal
var 12w : Float 
12w = 12
print(12w)
```
- Swift是一个大小写敏感的语言。区分大小写。
- Swift支持Unicode，意味着你可以使用简单的Unicode来命名
```swift
var 变量: Int
变量 = 10
print(变量)
```

##### 变量输出
变量和常量可以使用 ```print()``` 输出
在字符串中可以使用括号与反斜杠来输出变量

```swift
var var_12: Float
var_12 = 10
print("\(var_12)是一个浮点型") // 10.0是一个浮点型
```

