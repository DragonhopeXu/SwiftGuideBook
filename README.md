# -Swift
# 从一开始学Swift

## 基础部分

### 常量和变量

#### 声明常量和变量

常量let 变量var

```
let max = 10
var min = 2
```

用let之后不能修改值，用var可以

#### 类型注解

```
var welcome: String
```

:后面加类型

#### 输出常量和变量

用print("")

```
print("hello world")
```

### 注释

用//来单行注释

用/*

   */

来多行注释

### 元组

元组是把多个值组合成一个复合值

```
let http404Error = (404, "Not Found")
```

该元组的类型即为（Int，String）类型

可以进行元组分解把http404Error分解为

```
let (statusCode, statusMessage) = http404Error
```

由此404赋值给了statusCode，“Not Found”赋值给了statusMessage

如果懒得给两个都赋值，可以将为赋值的用_代替如：

```
let (statusCode, _) = http404Error
```

或者用他们在元组中的位数表示他们所对应的值如：

```
print("is \(http404Error.0)")
```

### 可选型

用可选型来处理值可能缺失的情况

*像将字符串"hello"转为数值则会导致值缺失*

#### nil

用nil来表示可选变量没有值

```
var serverResponseCode: Int? = 404
serverResponseCode = nil
```

如果声明的可选变量没有赋值则会自动设置为nil

```
var surverAnswer: String?
```

*surverAnswer为nil*

#### if语句强制解析

用if语句可以比较安全的拆包避免报错

```
if convertedNumber != nil {
    print(“这个number有值，值为\(convertedNumber!)”)
}
```

*可选类型用！来获取值*

#### 可选绑定

用可选绑定判断可选类型是否包含值，如果有就赋值给变量

```
if let constantName = Int(possibleNumber) {
    print("\'\(possibleNumber)\'有一个整形值为\(actualNumber)")
} else {
    print("\'\(possibleNumber)\'不是转化为整形")
}
```

如果Int(possibleNumber)为一个Int值，则创建一个常量constantName来把值赋给他

*算法经常碰到*

#### 隐式解析可选型

把可选型后面的问好String?改为String!来声明一个隐式解析可选型

一个隐式解析可选型可以当非可选型使用，不需要每次解析获取可选值

```
let possibleString: String? = "一个可选型字符串"
let forcedString: String = possibleString

let assumedString: String! = "一个隐式解析可选型(不需要拆包)"
let implicitString: String = assumedString
```

*如上第二块代码则不需要用感叹号进行拆包，其前提是在第一个定义的时候加！*

### 错误处理

遇到错误用下列两种方法抛出异常

```
func canThorwAnErroe() throws {
    //这个函数有可能抛出错误
}
```

```
do {
    try canThrowAnErroe()
    //没有错误信息抛出
} catch {
    //有错误信息抛出
}
```

## 基本运算符

### 术语

#### 一元运算符 

-a    !b    c!

#### 二元运算符

2 + 3

#### 三元运算符

a ? b : c

### 赋值运算符

```
a = b

let (x, y) = (1, 2)
//x=1,y=2
```

### 算数运算符

加+ 减- 乘* 除/ 取余%

### 比较运算符

等于==  不等于!=  大于>  小于<  大于等于>=  小于等于<=

### 三元运算符

问题 ？ 答案一： 答案二

### 空合运算符

（a ?? b ）对可选型a进行非空判断，如果a有值就拆包，否则返回b

```
a != nil ? a! : b
```

*可选型a不为空则强制拆包返回a的值，否则返回b*

### 区间运算符

#### 闭区间运算符

(a...b)表示从a到b(包含a,b)的所有值的区间

#### 半开区间运算符

(a..<b)表示从a到b(不含b)的值的区间

#### 单侧区间

表示一侧无限延伸的区间

[2...]表示从2开始到结尾

[...2]表示从开头到2

[..<2]表示从开头到2的前一位

### 逻辑运算符

与&&  或||  非!

## 字符串和字符

#### 初始化空字符串

```
var emptyString = ""  //空字符串字面量
var anotherEmptyString = String() //初始化方法
```

### 字符串是值类型

#### 使用字符

通过for-in循环可以遍历字符串

```
for character in "Dog!"{
     print(character)
}
```

### 连接字符串和字符

用+连接

### 字符串插值

用“\”+(想插入的字符串名)

### 计算字符数量

字符串名.count

### 访问和修改字符串

#### 字符串索引

字符串名.Index，对应字符串每个字符的位置

startIndex为第一个字符的索引

endIndex为最后一个字符的索引

用index(字符名.startIndex或者endIndex，offsetBy: 数字)

*简写为index(_:offsetBy:)*

#### 插入和删除

insert(_:at:)在字符串的指定索引插入一个字符

```
var welcome = "hello"
welcome.insert("!", at: welcome.endIndex)
//结果为hello!
```

remove(at:)在字符串的指定索引删除一个字符

```
welcome.remove(at: welcome.index(before: welcome.endIndex))
//结果为hello
```



### 比较字符串

#### 字符串/字符相等

等于==     不等于!=

#### 前缀/后缀相等

hasPrefix("字符或字符串") 检查是否有特定前缀

hasSuffix("字符或字符串")检查是否有特定后缀


