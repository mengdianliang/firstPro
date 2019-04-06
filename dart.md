### 1. dart语言概述
``` python
 一门开源编程语言
 目标成为下一代web语言
 可用于全平台开发
 面向对象
```
### 2. 应用场景
``` python
 web开发
 跨平台移动应用开发(Flutter)
 脚本或服务器开发
```
### 3. 环境搭建
``` python
 SDK安装
    Install using a setup wizard
    wins：
    http://www.gekorm.com/dart-windows/
 插件安装
    安装code runner插件 (vscode)
```
### 4. 变量和常量
``` python
    (1) 变量
        1) 使用var声明变量，可赋予不同类型的值；
        2) 未初始化时，默认值为null；
        3) 使用final声明一个只能赋值一次的变量；
    (2) 常量
        使用const声明的必须是编译期常量
```
### 5. 数据类型
``` python
数值型 Number  
        整型   Int
        浮点型 double
    
    数值型操作
        运算符：+，-，*，/，~/(取整向下)，%
        常用属性：isNaN,isEven, isOdd等
        常用方法：abs(),round(),floor(),ceil(),toInt(),toDouble()
        
字符型 String
        (1) 使用单引号，双引号创建字符串；
        (2) 使用三个引号或双引号创建多行字符串；
        (3) 使用r创建原始raw字符串；
        
    运算符： +，*，==，[]    
    插值表达式 ${expression}
    常用属性：length, isEmpty, isNotEmpty
    常用方法：contains(), substring(), startsWith(), endsWith(), indexOf(), lastIndexOf(), toLowerCase(), toUpperCase(), trim(), trimLeft(), trimRight(), split(), replaceXXX()
    
布尔型 Boolean
        (1) 使用bool表示布尔类型
        (2) 布尔值只有true和false
    
列表 List
        创建List：var list = [1, 2, 3];
        创建不可变的List：var list = const [1, 2, 3];
        构造创建：var list = new List();
    
    常用操作：
        [], lengh
        add(), insert()
        remove(), clear()
        indexOf(), lastIndexOf()
        sort(), sublist()
        shuffle(), asMap(), forEach()
键值对 Map
        创建Map: var language = {'first': 'Dart', 'second': 'Java'};
        创建不可变Map: var language = const {'first': 'Dart', 'second': 'Java'};
        构造创建: var language = new Map();
        
        常用操作：
            [], length
            isEmpty(), isNotEmpty()
            keys,values
            containsKey(), containsValue()
            remove(),
            forEach()
        
Runes/Symbols        
```
### 6. 运算符
``` python
 6-1 算数运算符
    加减乘除：+，-，*，/~/，%
    递增递减：++var, var++, --var, var--
 6-2 关系运算符
    ==, !=, >, <, >=, <=
    判断内容是否相同用==
 6-3 逻辑运算符
    !, &&, ||
    针对布尔型运算
 6-4 赋值运算符
    基础运算符：=, ??=(赋默认值)
    复合运算符：+=, -=, *=, /=, %=, ~/=
 6-5 条件表达式
    三目运算符：condition ? expr1 : expr2
    ??运算符：expr1 ?? expr2 (如果前边的值为空，选后边的值；否则，选前边的值)
```
### 7. 控制流
``` python
 4-1 if语句
    if语句
    if...else if语句
    if...else if...else语句
 4-2 for语句
     for
     for...in
 4-3 while语句
     while
     do..while
 4-4 break和continue
 4-5 switch...case语句
    比较类型：number,String, 编译器常量, 对象，枚举
    非空case必须有一个break
    default处理默认情况
    continue跳转标签
```
### 8. 方法
``` python
 8-1 方法定义
    返回类型 方法名(参数1, 参数2, ...) {
        方法体...
        return 返回值
    }
    
    方法特性： 
    (1) 方法也是对象，并且有具体类型Function;
    (2) 返回值类型，参数类型都可省略
    (3) 箭头语法： =>expr是{return expr;}缩写。只适用于一个表达式。
    (4)方法都有返回值。如果没有指定，默认return null最后一句执行。
 8-2 可选参数
    (1) 可选命名参数: {param1, param2, ...}
    (2) 可选位置参数: [param1, param2, ...]
 8-3 默认参数值
    (1) 使用=在可选参数指定默认值
    (2) 默认值只能是编译时常量
 8-4 方法对象
    (1) 方法可以作为对象赋值给其他变量
    (2) 方法可以作为参数传递给其他方法
 8-5 匿名方法
    (参数1, 参数2, ...) {
        方法体...
        return 返回值
    }
    
    特性：
        (1) 可赋值给变量，通过变量进行调用
        (2) 可在其他方法中直接调用或传递给其他方法
 8-6 闭包
    (1) 闭包是一个方法(对象)
    (2) 闭包定义在其他方法内部
    (3) 闭包能够访问外部方法内的局部变量，并持有其状态
```
### 9. 面向对象
``` python
 9-1 类与对象
 9-2 计算属性
 9-3 构造方法
 9-4 常量构造方法
 9-5 工厂构造方法
 9-6 初始化列表
 9-7 静态成员
 9-8 对象操作符
 9-9 对象call方法
 9-10 本章小结
```
### 10. 深层面向对象
``` python
 10-1 继承
 10-2 继承中的构造方法
 10-3 抽象类
 10-4 接口
 10-5 Mixins
 10-6 操作符覆写
```
### 11. 枚举&类型
``` python
 11-1 枚举
 11-2 泛型
```