## Swift 数据类型

#### 1.Int
一般来说，在Swift，如果没有特殊要求，我们不需要专门指定数据的长度。Swift中整数类型 Int 长度与当前平台一致。
> 在32位平台上,Int 和 Int32 长度相同
> 在64为平台上,Int 和 Int64 长度相同
> 

#### 2.UInt
Swift 中同时创建一个特殊的无符号的 Int类型，尽量避免使用它。
> 在32位平台上,UInt 和 UInt32 长度相同
> 在64为平台上,UInt 和 UInt64 长度相同
>

#### 3.浮点数
浮点数表示范围比Int更大。能够存储比Int更大或者更小的值。Double，Float。默认为Double类型。
> Double表示64位浮点数，精确度很高，至少有15位数字
> Float表示32位浮点数，精确度稍低，只有6位
> 

#### 4.布尔值
Swift中有一个基本的布尔(Boolean)类型，叫做Bool。只能为真或假，有两个常量值 true 和 false

> 不同于Objective-C中，只要非真即假的那种判断了。


```objective-c
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