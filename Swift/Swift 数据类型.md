## Swift 数据类型

#### Int
一般来说，在Swift，如果没有特殊要求，我们不需要专门指定数据的长度。Swift中整数类型 Int 长度与当前平台一致。
> 在32位平台上,Int 和 Int32 长度相同
> 在64为平台上,Int 和 Int64 长度相同
> 

#### UInt
Swift 中同时创建一个特殊的无符号的 Int类型，尽量避免使用它。
> 在32位平台上,UInt 和 UInt32 长度相同
> 在64为平台上,UInt 和 UInt64 长度相同
>

#### 浮点数
浮点数表示范围比Int更大。能够存储比Int更大或者更小的值。Double，Float。默认为Double类型。
> Double表示64位浮点数，精确度很高，至少有15位数字
> Float表示32位浮点数，精确度稍低，只有6位
> 

#### 布尔值
Swift中有一个基本的布尔(Boolean)类型，叫做Bool。只能为真或假，有两个常量值 true 和 false

> 不同于Objective-C中，只要非真即假的那种判断了。


```objc
NSString *string = @"Hello";
if (string) {// 这段代码可执行，即为真，

} 
```
```swift
var string = "Hello"
if string { // 代码报错 'String' is not convertible to 'Bool'
    print("代码为真")
} else {
    print("代码不为真")
}
```

#### 字符串
字符串时字符序列的集合
```swift
let string = "Hello World"
print(type(of: string))  // String 
```

#### 字符
字符是指单个字母
```swift
let s : Character = "J"
print(type(of: s))  //  Character

```

```swift
// 报错 Cannot convert value of type 'String' to specified type 'Character'
let s : Character = "ddJ"
```

#### 可选类型
可选类型来处理值可能缺失的情况。可选类型表示此处可能有值，可能没有值。

#### 数值范围
| 类型 | 大小（字节）|区间值 |
|:---:|:---:|:---:|
| Int8|1字节|-127 到 127|
|UInt8|1字节|0 到 255|
|Int32|4字节|-2147483648 到 2147483647|
|UInt32|4字节|0 到 4294967295|
|Int64|8字节|-9223372036854775808 到 9223372036854775807|
|UInt64|8字节|0 到 18446744073709551615|
|Float|4字节|1.2E-38 到 3.4E+38 (~6 digits)|
|Double|8字节|2.3E-308 到 1.7E+308 (~15 digits)|

#### 类型别名
类型别名是对当前类型自定义一个类型。通过使用关键字 ```typealias``` 来定义。
```swift
typealias newname = type
```

```swift
import cocoa
typealias Feed = Int
let feed: Feed = 10
print(feed) // 10
```

#### 类型安全
Swift是一种类型安全的语言。
由于是类型安全的语言，所以会在编译的时候对代码进行检查（type checks）。并把不匹配的类型标记为错误。可以让你在开发中尽早的识别错误，并进行修改。
```swift
var typeString = "Hello world"
typeString  = 10 // 报错 Cannot assign value of type 'Int' to type 'String'
print(typeString)
```

#### 类型推断
当你要处理不同类型的时候，类型安全可以帮你检查避免错误。然而这并不是意味着你每次都需要显示指定数据常量或者变量的类型。如果你没有显示的指定类型，Swift会使用类型推断来选择合适的类型。
```swift
let typeA = 10
print(type(of: typeA))  // 会推断为 Int
```

```swift
let typeB = 10.0
print(type(of: typeB))  // 会被推断为 Double
```