---
title： flutter学习

---

# 安装

http://gekorm.com/dart-windows/ 下载SDK安装包

windows命令行输入`dart --version`查看版本验证安装成功与否。

vscode安装dart、code runner这两个插件



# Dart语法

```dart
void main() {
    
}
```

类似C语言的main主函数。

## [变量与常量](https://dart.cn/guides/language/language-tour#variables)

**Dart 变量：**

 dart是一个强大的脚本类语言，可以不预先定义变量类型 ，自动会类型推倒

 dart中定义变量可以通过var关键字可以通过类型来申明变量

 如：

```dart
  var str='this is var';

  String str='this is var';

  int str=123;
```

 注意： var 后就不要写类型 ， 写了类型 不要var  两者都写  var a int = 5; 报错



**Dart 常量：  final 和 const修饰符** 

  const值不变 一开始就得赋值

  final 可以开始不赋值 只能赋一次 ; 而final不仅有const的编译时常量的特性，最重要的它是运行时常量，并且final是惰性初始化，即在运行时第一次使用前才初始化



## 数据类型

Dart中支持以下数据类型：

 常用数据类型：

   Numbers（数值）:

​     int

​     double

   Strings（字符串）

​     String

   Booleans(布尔)

​     bool

   List（数组）

​     在Dart中，数组是列表对象，所以大多数人只是称它们为列表

   Maps（字典）

​     通常来说，Map 是一个键值对相关的对象。 键和值可以是任何类型的对象。每个 键 只出现一次， 而一个值则可以出现多次

 项目中用不到的数据类型 （用不到）：

   Runes 

​    Rune是UTF-32编码的字符串。它可以通过文字转换成符号表情或者代表特定的文字。

```dart
main() {
  var clapping = '\u{1f44f}';
  print(clapping);
  print(clapping.codeUnits);
  print(clapping.runes.toList());
  Runes input =
      new Runes('\u2665 \u{1f605} \u{1f60e} \u{1f47b} \u{1f596} \u{1f44d}');
  print(new String.fromCharCodes(input));
}

```

![](https://gitee.com/dunteng/pic-go/raw/master/imgs/image-20210312130653428.png)

​    

   Symbols

​    Symbol对象表示在Dart程序中声明的运算符或标识符。您可能永远不需要使用符号，但它们对于按名称引用标识符的API非常有用，因为缩小会更改标识符名称而不会更改标识符符号。要获取标识符的符号，请使用符号文字，它只是＃后跟标识符：





​    在 Dart 中符号用 # 开头来表示，入门阶段不需要了解这东西，可能永远也用不上。

​    

​    http://dart.goodev.org/guides/libraries/library-tour#dartmirrors---reflection





### String字符串

```dart
/* 字符串定义的几种方式 */
var str1='this is str1';
String str1='this is str1';

// 使用三引号可以实现换行的效果，类似es6模板字符串
String str1 = '''this is str1
   this is str1

   this is str1
   ''';
```

#### $拼接变量字符串

```dart
/* 字符串拼接 */
 String str1='你好';
 String str2='Dart';
 print("$str1 $str2");
 print(str1 +" "+ str2); // 类似js
```



### Number数值类型

```dart
int a=123;
double b=23.5;
double dd = 24; // double  既可以是整型 也可是浮点型
print(0.1 + 0.2); // 0.30000000000000004 和js一样有精度问题
```



### Bool布尔类型

和 js 一样



### List集合/数组类型

```dart
var l1=['aaa','bbbb','cccc'];
print(l1);
print(l1.length);
print(l1[1]);
l1.add('ddd')； // 增加一个元素
```

由于SDK升级，以前可以用`new List()`来声明一个数组的，但是现在不允许了。

```dart
List里面常用的属性和方法：

    常用属性：
        length          长度
        reversed        翻转
        isEmpty         是否为空
        isNotEmpty      是否不为空
    常用方法：  
        add         增加
        addAll      拼接数组
        indexOf     查找  传入具体值
        remove      删除  传入具体值
        removeAt    删除  传入索引值
        fillRange   修改   
        insert(index,value);            指定位置插入    
        insertAll(index,list)           指定位置插入List
        toList()    其他类型转换成List  
        join()      List转换成字符串
        split()     字符串转化成List
        forEach   
        map
        where
        any
        every
```





### Map映射类型

Map的格式类似Json

```dart
  映射(Maps)是无序的键值对：

    常用属性：
        keys            获取所有的key值
        values          获取所有的value值
        isEmpty         是否为空
        isNotEmpty      是否不为空
    常用方法:
        remove(key)     删除指定key的数据
        addAll({...})   合并映射  给映射内增加属性
        containsValue   查看映射内的值  返回true/false
        forEach   
        map
        where
        any
        every
```



```dart
main() {
  var person = {
    "name": "张三",
    "age": 20,
    "work": ["程序员", "送外卖"]
  };

  print(person);
  print(person['name']); // 无法像js对象那样用.来获取
}
```

输出结果👇

![image-20210318161217711](d:\user\01397392\Application Data\Typora\typora-user-images\image-20210318161217711.png)

也可以用另一种定义map方式:

```dart
    var p=new Map();

    p["name"]="李四";
    p["age"]=22;
    p["work"]=["程序员","送外卖"];
    print(p);

    print(p["age"]);
```

#### Map的属性和方法

```dart
void main() {
  Map person = {"name": "张三", "age": 20, "sex": "男"};

  print(person.keys.toList());
  print(person.values.toList());
  print(person.isEmpty);
  print(person.isNotEmpty);
}

void main() {
  Map person = {"name": "张三", "age": 20, "sex": "男"};

  person.addAll({
    "work": ['敲代码', '送外卖'],
    "height": 160
  });

  print(person);

  person.remove("sex");
  print(person);

  print(person.containsValue('张三'));
}

```





### Set类型

```dart
//用它最主要的功能就是去除数组重复内容
//Set是没有顺序且不能重复的集合，所以不能通过索引去获取值
void main() {
  var s = new Set();
  s.add('香蕉');
  s.add('苹果');
  s.add('苹果');

  print(s); //{香蕉, 苹果}

  print(s.toList());
}

```

![](https://gitee.com/dunteng/pic-go/raw/master/imgs/image-20210318191540888.png)

```dart
// 利用Set进行数组去重

void main() {
  List myList = ['香蕉', '苹果', '西瓜', '香蕉', '苹果', '香蕉', '苹果'];

  var s = new Set();

  s.addAll(myList);

  print(s);

  print(s.toList());
}

```







## Dart判断数据类型  

dart用`is `关键词来判断类型

```dart
void main() {
  var str = 123;
  print(
    String is String,
  );
  if (str is String) {
    print('是string类型');
  } else if (str is int) {
    print('int');
  } else {
    print('其他类型');
  }
}
```



## 循环

基本上和JS是一样的,不赘述,补充一下continue,很少用到复习一下.

```dart
    //1、如果i等于4的话跳过

    for(var i=1;i<=10;i++){
      if(i==4){
        continue;  /*跳过当前循环体 然后循环还会继续执行*/
      }
      print(i);
    }
```

## 运算符

基本上和js一样，有几样多出来的运算符：

**`??=`运算符**： a??=2; 表示如果a为空的话把 2赋值给b

```dart
void main() {
  var a = null;
  a ??= 2;
  print(a);
  a ??= 3;
  print(a);
}

```

它其实类似js里`||=`的操作，但是在dart里`||`要求两端都是布尔值不像js那么灵活，所以有了`??=`这个运算符



**`~/`取整运算符**：

```dart
 print(a ~/ 2); // 1
```



## 类型转换

 Number类型转换成String类型 toString()

 String类型转成Number类型 int.parse()、double.parse()



## 函数

### 传参

```dart
/*
  内置方法/函数：

      print();

  自定义方法：
      自定义方法的基本格式：

      返回类型  方法名称（参数1，参数2,...）{
        方法体
        return 返回值;
      }
*/

/** 定义一个带参数的函数 */
void main() {
  int myPrint(int n) {
    return n;
  }
  print(myPrint(45));
}

/** 定义一个带可选参数的函数 */
void main() {
  int myPrint(int n, [int? k]) {
    if (k == null) {
      return n;
    }
    return k;
  }
  print(myPrint(45, 54));
}

/** 可选参数可以设置默认值 */
void main() {
  int myPrint(int n, [int? k = 90]) {
    if (k == null) {
      return n;
    }
    return k;
  }
  print(myPrint(45)); // 90
}

/** 命名参数 */
void main() {
  String printUserInfo(String username,{int? age,String sex='男'}){  

      if(age!=null){
        return "姓名:$username---性别:$sex--年龄:$age";
      }
      return "姓名:$username---性别:$sex--年龄保密";

  }
  print(printUserInfo('张三',age:20,sex:'未知'));
}
```



### 箭头函数

和es6的大致相同，但是只能写一行，比较鸡肋。

### 闭包

dart里也有闭包的概念：

```dart
想实现的功能：
1.常驻内存        
2.不污染全局   

产生了闭包,闭包可以解决这个问题
闭包: 函数嵌套函数, 内部函数会调用外部函数的变量或参数, 变量或参数不会被系统回收(不会释放内存)
闭包的写法： 函数嵌套函数，并return 里面的函数，这样就形成了闭包。
```



## 面向对象与类

```dart
面向对象编程(OOP)的三个基本特征是：封装、继承、多态      

      封装：封装是对象和类概念的主要特性。封装，把客观事物封装成抽象的类，并且把自己的部分属性和方法提供给其他对象调用, 而一部分属性和方法则隐藏。
                
      继承：面向对象编程 (OOP) 语言的一个主要功能就是“继承”。继承是指这样一种能力：它可以使用现有类的功能，并在无需重新编写原来的类的情况下对这些功能进行扩展。
            
      多态：允许将子类类型的指针赋值给父类类型的指针, 同一个函数调用会有不同的执行效果 。


Dart所有的东西都是对象，所有的对象都继承自Object类。

Dart是一门使用类和单继承的面向对象语言，所有的对象都是类的实例，并且所有的类都是Object的子类

一个类通常由属性和方法组成。
```

### 自定义类

```dart
class Person{
  String name="张三";
  int age=23;
  void getInfo(){
      // print("$name----$age");
      print("${this.name}----${this.age}");
  }
  void setInfo(int age){
    this.age=age;
  }

}
void main(){

  //实例化

  // var p1=new Person();
  // print(p1.name);
  // p1.getInfo();

  Person p1=new Person();
  // print(p1.name);

  p1.setInfo(28);
  p1.getInfo();
}
```

### 构造函数

```dart
class Person{
  String name;
  int age; 
  //默认构造函数的简写
  Person(this.name,this.age); // 记住！
  void printInfo(){   
    print("${this.name}----${this.age}");
  }
}


void main(){
  
  Person p1=new Person('张三',20);
  p1.printInfo();

  Person p2=new Person('李四',25);
  p2.printInfo();

}
```



```dart
/*
dart里面构造函数可以写多个
*/
class Person {
  late String name;
  late int age;
  //默认构造函数的简写
  Person(this.name, this.age);

  Person.now() {
    print('我是命名构造函数');
  }

  Person.setInfo(String name, int age) {
    this.name = name;
    this.age = age;
  }

  void printInfo() {
    print("${this.name}----${this.age}");
  }
}

void main() {
  // var d=new DateTime.now();   //实例化DateTime调用它的命名构造函数
  // print(d);

  //Person p1=new Person('张三', 20);   //默认实例化类的时候调用的是 默认构造函数

  //Person p1=new Person.now();   //命名构造函数

  Person p1 = new Person.setInfo('李四', 30);
  p1.printInfo();
}

```



### 私有属性和私有方法

Dart和其他面向对象语言不一样，Data中没有` public, private, protected`这些访问修饰符合

但是我们可以使用`_`把一个属性或者方法定义成私有。

【注意】：私有属性和私有方法必须单独抽离到一个文件中！

![](https://gitee.com/dunteng/pic-go/raw/master/imgs/image-20210322125820765.png)



### getter和setter

```dart
class Rect{
  num height;
  num width; 
  
  Rect(this.height,this.width);
  get area{
    return this.height*this.width;
  }
  set areaHeight(value){
    this.height=value;
  }
}

void main(){
  Rect r=new Rect(10,4);
  // print("面积:${r.area()}");   
  r.areaHeight=6;

  print(r.area);

}
```



### static静态成员

Dart中的静态成员:

 1、使用static 关键字来实现类级别的变量和函数

 2、静态方法不能访问非静态成员，非静态方法可以访问静态成员



### ..  级联操作 （连缀）

```dart
   Person p1=new Person('张三1', 20);

   p1.printInfo();

   p1..name="李四"
     ..age=30
     ..printInfo();
```





### 继承

```dart
面向对象的三大特性：封装 、继承、多态


Dart中的类的继承：  
    1、子类使用extends关键词来继承父类
    2、子类会继承父类里面可见的属性和方法 但是不会继承构造函数
    3、子类能复写父类的方法 getter和setter   @override  建议在覆写父类方法的时候加上 @override 可以写也可以不写  
```

```dart
class Person {
  String name='张三';
  num age=20; 
  void printInfo() {
    print("${this.name}---${this.age}");  
  } 
}
class Web extends Person{

}

main(){   

  Web w=new Web();
  print(w.name);
  w.printInfo();
 
}
```

```dart
class Person {
  String name;
  num age;
  Person(this.name, this.age);
  void printInfo() {
    print("${this.name}---${this.age}");
  }
}

class Web extends Person {
  Web(String name, num age) : super(name, age) {}
}

main() {
  // Person p=new Person('李四',20);
  // p.printInfo();

  // Person p1=new Person('张三',20);
  // p1.printInfo();

  Web w = new Web('张三', 12);

  w.printInfo();
}

```

```dart
class Person {
  String name;
  num age; 
  Person(this.name,this.age);
  void printInfo() {
    print("${this.name}---${this.age}");  
  }
  work(){
    print("${this.name}在工作...");
  }
}

class Web extends Person{
  Web(String name, num age) : super(name, age);

  run(){
    print('run');
    super.work();  //子类调用父类的方法
  }
  //覆写父类的方法
  @override       //可以写也可以不写  建议在覆写父类方法的时候加上 @override 
  void printInfo(){
     print("姓名：${this.name}---年龄：${this.age}"); 
  }
  

}


main(){ 

  Web w=new Web('李四',20);

  // w.printInfo();

  w.run();
 
}
```



### 抽象类和接口

Dart中抽象类: Dart抽象类主要用于定义标准，子类可以继承抽象类，也可以实现抽象类接口。

 1、抽象类通过abstract 关键字来定义

 2、Dart中的抽象方法不能用abstract声明，Dart中没有方法体的方法我们称为抽象方法。

 3、如果子类继承抽象类必须得实现里面的抽象方法

 4、如果把抽象类当做接口实现的话必须得实现抽象类里面定义的所有属性和方法。

 5、抽象类不能被实例化，只有继承它的子类可以

**extends抽象类 和 implements的区别：**

 1、如果要复用抽象类里面的方法，并且要用抽象方法约束自类的话我们就用extends继承抽象类

 2、如果只是把抽象类当做标准的话我们就用implements实现抽象类

```dart
案例：定义一个Animal 类要求它的子类必须包含eat方法

*/

abstract class Animal{
  eat();   //抽象方法
  run();  //抽象方法  
  printInfo(){
    print('我是一个抽象类里面的普通方法');
  }
}

class Dog extends Animal{
  @override
  eat() {
     print('小狗在吃骨头');
  }

  @override
  run() {
    // TODO: implement run
    print('小狗在跑');
  }  
}
class Cat extends Animal{
  @override
  eat() {
    // TODO: implement eat
    print('小猫在吃老鼠');
  }

  @override
  run() {
    // TODO: implement run
    print('小猫在跑');
  }

}

main(){

  Dog d=new Dog();
  d.eat();
  d.printInfo();

   Cat c=new Cat();
  c.eat();

  c.printInfo();


  // Animal a=new Animal();   //抽象类没法直接被实例化

}
```



```dart
abstract class Db {
  //当做接口   接口：就是约定 、规范
  String uri; //数据库的链接地址
  add(String data);
  save();
  delete();
}

class Mysql implements Db {
  @override
  String uri;

  Mysql(this.uri);

  @override
  add(data) {
    // TODO: implement add
    print('这是mysql的add方法' + data);
  }

  @override
  delete() {
    // TODO: implement delete
    return null;
  }

  @override
  save() {
    // TODO: implement save
    return null;
  }

  remove() {}
}

class MsSql implements Db {
  @override
  String uri;
  @override
  add(String data) {
    print('这是mssql的add方法' + data);
  }

  @override
  delete() {
    // TODO: implement delete
    return null;
  }

  @override
  save() {
    // TODO: implement save
    return null;
  }
}

main() {
  Mysql mysql = new Mysql('xxxxxx');

  mysql.add('1243214');
}

```



#### 一个类实现多个接口

```dart
/*
Dart中一个类实现多个接口：
*/

abstract class A{
  String name;
  printA();
}

abstract class B{
  printB();
}

class C implements A,B{  
  @override
  String name;  
  @override
  printA() {
    print('printA');
  }
  @override
  printB() {
    // TODO: implement printB
    return null;
  }

  
}


void main(){

  C c=new C();
  c.printA();


}
```





### 多态

```dart
/*
Datr中的多态：
    允许将子类类型的指针赋值给父类类型的指针, 同一个函数调用会有不同的执行效果 。

    子类的实例赋值给父类的引用。
    
    多态就是父类定义一个方法不去实现，让继承他的子类去实现，每个子类有不同的表现。

*/


abstract class Animal{
  eat();   //抽象方法 
}

class Dog extends Animal{
  @override
  eat() {
     print('小狗在吃骨头');
  }
  run(){
    print('run');
  }
}
class Cat extends Animal{
  @override
  eat() {   
    print('小猫在吃老鼠');
  }
  run(){
    print('run');
  }
}

main(){

  // Dog d=new Dog();
  // d.eat();
  // d.run();


  // Cat c=new Cat();
  // c.eat();

  Animal d=new Dog();
  d.eat();
  Animal c=new Cat();
  c.eat(); 
}
```



### mixins

```dart
/*
mixins的中文意思是混入，就是在类中混入其他功能。

在Dart中可以使用mixins实现类似多继承的功能


因为mixins使用的条件，随着Dart版本一直在变，这里讲的是Dart2.x中使用mixins的条件：

  1、作为mixins的类只能继承自Object，不能继承其他类
  2、作为mixins的类不能有构造函数
  3、一个类可以mixins多个mixins类
  4、mixins绝不是继承，也不是接口，而是一种全新的特性
*/

class A {
  String info = "this is A";
  void printA() {
    print("A");
  }
}

class B {
  void printB() {
    print("B");
  }
}

class C with A, B {}

void main() {
  var c = new C();
  c.printA();
  c.printB();
  print(c.info);
}

```





## 库

```dart
前面介绍Dart基础知识的时候基本上都是在一个文件里面编写Dart代码的，但实际开发中不可能这么写，模块化很重要，所以这就需要使用到库的概念。

在Dart中，库的使用时通过import关键字引入的。

library指令可以创建一个库，每个Dart文件都是一个库，即使没有使用library指令来指定。


Dart中的库主要有三种：

    1、我们自定义的库     
          import 'lib/xxx.dart';
    2、系统内置库       
          import 'dart:math';    
          import 'dart:io'; 
          import 'dart:convert';
    3、Pub包管理系统中的库  
        https://pub.dev/packages
        https://pub.flutter-io.cn/packages
        https://pub.dartlang.org/flutter/

        1、需要在自己想项目根目录新建一个pubspec.yaml
        2、在pubspec.yaml文件 然后配置名称 、描述、依赖等信息
        3、然后运行 pub get 获取包下载到本地  
        4、项目中引入库 import 'package:http/http.dart' as http; 看文档使用
```

