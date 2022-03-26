# Kotlin

## 一、Kotlin简介

Kotlin 是一种在 Java 虚拟机上运行的静态类型编程语言，被称之为 Android 世界的Swift，由 JetBrains 设计开发并开源。

Kotlin 可以编译成Java字节码，也可以编译成 JavaScript，方便在没有 JVM 的设备上运行。

在Google I/O 2017中，Google 宣布 Kotlin 成为 Android 官方开发语言。



### 1.1Kotlin的优势

- 全面支持Lamda表达式
- 数据类
- 函数字面量和内联函数
- 函数扩展
- 空安全
- 智能转换
- 字符串模板
- 主构造函数
- 类委托
- 类型推断
- 单例
- 声明点变量
- 区间表达式



### 1.2第一个Kotlin程序

创建一个文件HelloWorld.kt，Kotlin文件以.kt为后缀。

```kotlin
fun main(args:Array<String>){
    println("hello world")
}
```

1. 函数声明使用fun
2. main方法是程序的入口
3. 接收参数名是args，数据类型字符串数组
4. 向控制台打出hello world字符串



### 1.3变量

Kotlin的基本数值类型包括Byte、Short、Int、Long、Float、Double等。不同于 Java 的是，字符不属于数值类型，是一个独立的数据类型。

**定义变量的方式：**

1. var 关键字：用来定义可变变量

   ```kotlin
   var <标识符> : <类型> = <初始化值>
   ```

2. val 关键字：用来定义不可变变量（类似于java中final修饰的变量）

   ```kotlin
   val <标识符> : <类型> = <初始化值>
   ```

3. 系统可以自动进行类型判断

   ```kotlin
   val a : Int = 1
   
   val b = 1
   
   val c : Int
   c = 1
   
   // 这三种，系统都可以自动判断出声明的类型
   ```


**声明变量的方式：**

1. 隐式类型声明：声明时不指定类型，由编译器自动判断

   ```kotlin
   var i = 18 // int
   var j = 9999999999 // long
   var k = "name" // string
   var l = 'c' // char
   var m = 3.14 // float
   ```

   **隐式声明时必须给定初值！**

2. 显式类型声明：声明时指定类型

   ```kotlin
   var i : Int = 18 // int
   var j : Long= 9999999999 // long
   var k : String = "name" // string
   var l : Char = 'c' // char
   var m : Float = 3.14 // float
   ```



### 1.4函数

函数定义使用关键字 fun，参数格式为：参数名 : 类型

```kotlin
fun sum(a: Int, b: Int): Int {   // Int 参数，返回值 Int
    return a + b
}
```

表达式作为函数体，返回类型自动推断：

```kotlin
fun sum(a: Int, b: Int) = a + b

public fun sum(a: Int, b: Int): Int = a + b   // public 方法则必须明确写出返回类型
```

无返回值的函数(类似Java中的void)：

```kotlin
fun printSum(a: Int, b: Int): Unit { 
    print(a + b)
}

// 如果是返回 Unit类型，则可以省略(对于public方法也是这样)：
public fun printSum(a: Int, b: Int) { 
    print(a + b)
}
```

可变长参数函数：

```kotlin
fun vars(vararg v:Int){
    for(vt in v){
        print(vt)
    }
}

// 测试，类似于java中的(int v...)
fun main(args: Array<String>) {
    vars(1,2,3,4,5)  // 输出12345
}
```

lambda(匿名函数)

```kotlin
// 测试
fun main(args: Array<String>) {
    val sumLambda: (Int, Int) -> Int = {x,y -> x+y}
    println(sumLambda(1,2))  // 输出 3
}
```

