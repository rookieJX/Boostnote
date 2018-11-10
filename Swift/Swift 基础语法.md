## Swift 基础语法

##### 1.Swift引入

  在Swift中，使用 import 来引用框架到我们的程序中。
  ``` 
  import Cocoa 
  ```
##### 2.Swift注释
```swift
// 这是一行注释
```
```swift
/*这也是一行注释*/
```
```swift
/*
    这同样是一行注释
    /*
    但是我们可添加多层嵌套
    */
    这就是注释的结尾
*/
```
#### 3.分号
Swift中是不需要分号来标识一句话的结尾，但是如果一行有多句话，就需要分号来标识

```swift
import Cocoa

var myString = "Hello World";print(myString)

```

#### 4.标识符
标识符就是给变量、常量、方法、函数等指定的名字。

- 区分大小写
- 标识符首字母为 字母或者下划线，不可以用数字和其他字符
- 标识符其他字符可以为 字母，数字，下划线

> 如果一定要使用关键字做标识符，可以在关键字前后加上重音标识符 `
> 

#### 5.关键字
关键字是一种特殊的标识符，对于编译器来说有特殊的作用。常用的关键字有四种

1. 与声明有关的关键字

| 与声明有关的关键字 ||||
| :-------: | :----: | :---: | :---: |
| class     | deinit | enum   |extension|
| func | import |  init    | internal |
| let    | operator   |  private   | protocl |
| public     | static    |  struct  | subscript |
| typealias     | var    |    |  |

2. 与语句有关的关键字
| 与语句有关的关键字 ||||
| :-------: | :----: | :---: | :---: |
| break | case |  continue    | default |
| do    | else   |  fallthrough   | for |
| if     | in    |  return  | switch |
| where     | while    |    |  |

3. 与表达式和类型有关的关键字
| 与表达式和类型有关的关键字 ||||
| :-------: | :----: | :---: | :---: |
| as | dynamicType |  false    | is |
| nil    | self   |  Self   | super |
| true     | _COLUMN_    |  _FILE_  | _FUNCTION_ |
| _LINE_     |     |    |  |


4. 在特定上下文中使用的关键字
| 在特定上下文中使用的关键字字 ||||
| :-------: | :----: | :---: | :---: |
| associativity | convenience |  dynamic    | didSet |
| final    | get   |  infix   | inout |
| lazy     | left    |  mutating  | none |
| nonmutating     | optional    | override   | postfix |
| precedence    | prefix   |  Protocol   | required |
| right     | set    |  Type  | unowned |
| weak     | willSet    |    |  |


#### 6.Swift空格
在Swift中，对空格还是会有一定的要求的。简单来说就是表达式左右最好保持一致。
例如

```swift
let a=1+2 // 表达式正常
```

```swift
let a= 1+2 // 表达式报错'=' must have consistent whitespace on both sides
```

```swift
let c = 1+3 // 表达式正常
```

```swift
let d = 1+ 4 // 表达式报错'+' is not a postfix unary operator
```
			
			
			
			
			
			
		