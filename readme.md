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

## 集合类型

### 数组(Ayyay)

#### 创建一个空数组

```
var someInts: [Int] = []
```

```
someInts.append(3)
//someInts现在包含了一个Int值
someInts = []
//someInts现在为空数组，但还是Int类型
```

#### 创建一个带有默认值的数组

repeating表示初始值，count表示初始值重复的次数

```
var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles 是一种[Double]数组，等价于[0.0, 0.0, 0.0]
```

#### 通过两个数组相加创建一个数组

用+连接

#### 用数组字面量构造数组

```
var shoppingList: [String] = ["Eggs", "Milk"]
```

如上构造了一个有两个初始值的shoppingList

#### 访问和修改数组

数组名.count

判断是否为空用 数组名.isEmpty

数组后面添加新数据项 数组名.appent("添加的东西")

用下标语法可以直接访问数组中的数据 数组名[位数]

在某个特定索引值之前添加数据 数组名.insert("数据", at: 位数)

在某个特定索引值中删除数据的某一项 数组名.remove(at: 位数)

### 集合(Sets)

#### 创建和构造一个空的集合

Set<Element> 其中Element表示集合允许存储的类型

```
var letters = Set<Character>
```

其他大致和数组一样

#### 集合操作

intersection(_:) 取交集

symmetricDifference(_:)取不想交的集合

union(_:)取并集

subtracting(_:)取a不包含b的集合

使用举例

```
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]

oddDigits.union(evenDigits).sorted()
//[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 字典(Dictionary)

#### 创建一个空字典

字典使用Dictonary<Key, Value>定义 其中key是可以在字典中被用作键的类型，Value是字典中对应于这些键所存储的数据类型

```
var namesOfIntegers: [Int: String] = [:]
//namesOfIntegers 是一个空的[Int: String]字典
```

#### 用字典字面量创建字典

下列airports字典被声明为[String: String]类型，包含两个键值对

```
var airports: [String: String] = ["YYZ": "Toronto", "DUB": "Dublin"]
```

## 控制流

### For-In循环

用for-in遍历数组的所有元素

```
let names = ["Anna", "Alex"]
for name in names {
    print("Hello, \(name)!")
}
```

*如果不需要用到name，那么name可以用_代替*

### While循环

```
while condition {
        statements
}
```

### 条件语句

#### If

#### Switch

### 控制转移语句

#### continue

#### break

## 函数

### 函数的定义与调用

定义一个函数时需要定义多个有名字和类型的值称为参数

定义某种类型的值作为函数执行结束时的输出，称为返回类型

*函数实参必须和函数参数表里的参数的顺序一致*

```
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
```

以上函数函数名为greet(person:)，需要定义一个输入参数，叫做person的String值，和一个String的返回值

```
print(greet(person: "Mike"))
//打印"Hello, Mike!"
```

在调用这个函数时，需要在圆括号中传给它一个String类型的实参

### 函数参数与返回值

#### 无参数函数

```
func sayHelloWorld() -> String {
    return "hello world"
}
print(sayHelloWorld())
```

以上函数没有参数，被调用时返回固定的String消息

#### 多参数函数

```
func greet(person: String, alreadyGreeted: Bool) -> String {
    if alreadyGreeted {
        return greetAgain(person: person)
    } else {
        rerurn greet(person: person)
    }
}
print(greet(person: "Tim", alreadyGreeted: true))
//打印"Hello again,Tim!"
```

以上函数有两个参数，需要两个参数正常使用

#### 无返回值函数

```
func greet(person: String) {
    print("Hello, \(person)!")
}
greet(person: "Dave")
//打印"Hello, Dave!"
```

以上函数不需要返回值，所以没有->

#### 多重返回值函数

```
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```

以上函数定义了一个minMax(array:)函数，在数组中找出最大最小值

函数返回两个Int值的元组，被标记为min和max

#### 可选元组返回类型

如果函数返回的元组类型有可能整个元组都没有值，可以用可选的元组返回类型来声明元组可以说nil，可以通过在元组类型的右括号放置一个问号来定义一个可选元组例如(Int, Int)?

```
func minMax(array: [Int]) -> (min: Int, max: Int) {
    if array.isEmpty{ return nil }
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```

以上函数添加了个if语句来处理空数组问题

#### 隐式返回的函数

```
func greeting(for person: String) -> String {
    "Hello, " + person + "!"
}
print(greeting(for: "Dave"))
//打印 "Hello, Dave!"
```

以上函数省略了return

### 函数参数提示符和参数名称

每个函数参数都有一个参数提示符和一个参数名称

调用的时候参数提示符在参数名称前面

```
func someFunction(argumentLabel parameterName: Int) {
    //parameterName代表参数值
}
```

可以用_来省略参数提示符

