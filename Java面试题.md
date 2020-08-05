# Java面试题

## java基础面试题

1. ##### JDK和JRE的区别

   JRE是Java Runtime Environment的缩写，顾名思义是java运行时环境，包含了java虚拟机，java基础类库。

   Jdk是Java Development Kit的缩写，顾名思义是java开发工具包，是程序员使用java语言编写java程序所需的开发工具包，是提供给程序员使用的。

   如果需要运行java程序，只需安装JRE就可以了。如果需要编写java程序，就需要安装JDK。

2. ##### 什么是基本数据类型，什么是引用数据类型

   基本类型：内置的数据类型、由编程语言本身定义，Java中的基本数据类型有byte、short、int、long、float、double、char、boolean

   引用数据类型：Java中一般都是通过类或接口进行构造，类提供了捆绑数据和方法的方式，同时可以针对程序外部进行信息隐藏。像数组、接口、封装对象。

3. ##### ==和equals的区别

   在没有重写equals方法的类中，比如User等自定义类中

   ==和equals比较的都是引用是否指向了同一块内存。

   在重写了equals方法的类中，比如String。

   使用==比较的是String的引用是否指向了同一块内存，同一个地址

   使用equals比较的是字符串内容是否相等。

4. ##### 两个对象的hashCode相同，则equals（）也一定为true吗

   equals相等，则hashcode一定相等，但是hashcode相同equals（）不一定为true。

5. ##### final在Java中有什么作用

   final作为Java中的关键字可以用于三个地方。用于修饰类、类属性和类方法，凡是引用final关键字的地方都不可以修改。

   修饰类时表示该类不能被继承；

   修饰方法时表示该方法不能被重写；

   修饰变量时表示该变量只能赋值一次后就不能被修改。

6. ##### Java中的Math.round（-1.5）等于等于多少？

   Math的round方法是四舍五入，如果参数是负数,则往大的数入，Math.round（-1.5） = -1

7. ##### 为什么说String不可变？

   `String` 是一个不可变的，由 `final` 修饰的类。它的底层使用char[ ]数组来保存字符，这个数组是被final修饰的，所以不可变。

8. ##### Java中操作字符串都有哪些类？它们之间有什么区别？

   Java 中，常用的对字符串操作的类有 String、StringBuffer、StringBuilder。

   - String : final 修饰，String 类的方法都是返回 new String。即对 String 对象的任何改变都不影响到原对象，对字符串的修改操作都会生成新的对象。
   - StringBuffer : 对字符串的操作的方法都加了synchronized，保证线程安全。
   - StringBuilder : 不保证线程安全，在方法体内需要进行字符串的修改操作，可以 new StringBuilder 对象，调用 StringBuilder 对象的 append()、replace()、delete() 等方法修改字符串。

9. ##### String str=“ i ”与String str = new String（“ i ”）一样吗？

   **不一样**

   因为内存的分配方式不一样。String str="i"的方式，Java 虚拟机会将其分配到常量池中；而 String str=new String(“i”)方式，则会被分到堆内存中。

   > Java 虚拟机会将其分配到常量池中：常量池不会重复创建对象。

   - 在String str1="i"中，把i值存在常量池，地址赋给str1。假设再写一个String str2=“i”，则会把i的地址赋给str2，但是i对象不会重新创建，他们引用的是同一个地址值，共享同一个i内存。

   > 分到堆内存中：堆内存会创建新的对象。

   - 假设再写一个String str3=new String(“i”)，则会创建一个新的i对象，然后将新对象的地址值赋给str3。虽然str3和str1的值相同但是地址值不同。

   > 堆内存用来存放由new创建的对象和数组。

10. ##### 如何将字符串反转？

    string.reverse（）方法和toCharArray（）再反向拼接

11. ##### String类的常用方法都有哪些？

    | `char`          | `charAt(int index)`  返回 `char`指定索引处的值。             |
    | --------------- | ------------------------------------------------------------ |
    | `int`           | `codePointAt(int index)`  返回指定索引处的字符（Unicode代码点）。 |
    | `int`           | `compareTo(String anotherString)`  按字典顺序比较两个字符串。 |
    | `int`           | `compareToIgnoreCase(String str)`  按字典顺序比较两个字符串，忽略病例差异。 |
    | `String`        | `concat(String str)`  将指定的字符串连接到该字符串的末尾。   |
    | `boolean`       | `contains(CharSequence s)`  当且仅当此字符串包含指定的char值序列时才返回true。 |
    | `boolean`       | `endsWith(String suffix)`  测试此字符串是否以指定的后缀结尾。 |
    | `boolean`       | `equals(Object anObject)`  将此字符串与指定对象进行比较。    |
    | `boolean`       | `equalsIgnoreCase(String anotherString)`  将此 `String`与其他 `String`比较，忽略案例注意事项。 |
    | `static String` | `format(Locale l, String format,  Object... args)`  使用指定的区域设置，格式字符串和参数返回格式化的字符串。 |
    | `byte[]`        | `getBytes()`  使用平台的默认字符集将此 `String`编码为字节序列，将结果存储到新的字节数组中。 |
    | `void`          | `getChars(int srcBegin,  int srcEnd, char[] dst, int dstBegin)`  将此字符串中的字符复制到目标字符数组中。 |
    | `int`           | `hashCode()`  返回此字符串的哈希码。                         |
    | `int`           | `indexOf(int ch)`  返回指定字符第一次出现的字符串内的索引。  |
    | `boolean`       | `isEmpty()`  字符串长度是否为0                               |
    | `static String` | `join(CharSequence delimiter, CharSequence... elements)` 以某字符串，连接某字符串数组 |
    | `int`           | `lastIndexOf(int ch)`  返回指定字符的最后一次出现的字符串中的索引。 |
    | `int`           | `length()`  返回此字符串的长度。                             |
    | `boolean`       | `matches(String regex)`  告诉这个字符串是否匹配给定的 正则表达式。 |
    | `String`        | `replace(char oldChar,  char newChar)`  字符串替换 。        |
    | `String`        | `replaceAll(String regex,  String replacement)`  带正则字符串替换 |
    | `String`        | `replaceFirst(String regex,  String replacement)`  替换第一个出现的目标字符串 |
    | `String[]`      | `split(String regex)`  以某正则表达式分割字符串。            |
    | `boolean`       | `startsWith(String prefix)`  测试此字符串是否以指定的前缀开头。 |
    | `boolean`       | `startsWith(String prefix,  int toffset)`  是否以目标字符串开头。 |
    | `String`        | `substring(int beginIndex)`  截取字符串。                    |
    | `char[]`        | `toCharArray()`  将此字符串转换为新的字符数组。              |
    | `String`        | `toLowerCase()`  将所有在此字符 `String`使用默认语言环境的规则，以小写。 |
    | `String`        | `toString()`  此对象（已经是字符串！）本身已被返回。         |
    | `String`        | `toUpperCase()`  将所有在此字符 `String`使用默认语言环境的规则大写。 |
    | `String`        | `trim()`  返回一个字符串，其值为此字符串，并删除任何前导和尾随空格。 |

12. ##### 抽象类必须要有抽象方法吗？

    抽象类不一定有抽象方法，但是包含抽象方法的类一定是抽象类。（有抽象方法就是抽象类，是抽象类可以没有抽象方法）

    抽象方法就是以abstract修饰的方法，这种方法只声明返回的数据类型、方法名称和所需的参数，没有方法体，也就是说抽象方法只需要声明而不需要实现。

13. ##### 普通类和抽象类有什么区别？

    - 抽象类不能被实例化
    - 抽象类可以有抽象方法，抽象方法只需申明，无需实现
    - 含有抽象方法的类必须申明为抽象类
    - 抽象的子类必须实现抽象类中所有抽象方法，否则这个子类也是抽象类
    - 抽象方法不能被声明为静态
    - 抽象方法不能用private修饰
    - 抽象方法不能用final修饰

14. ##### 抽象类能用final修饰吗？

    抽象类的作用是用于被继承，由子类来重写抽象类中的抽象方法，实现具体功能，但是final修饰的类不能被继承，那么抽象方法也没有意义。

    final不能修饰被abstract修饰的类。

15. ##### 接口和抽象类有什么区别？

    | 参数               | 抽象类                                                       | 接口                                                         |
    | ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
    | 默认的方法实现     | 它可以有默认的方法实现                                       | 接口完全是抽象的。它根本不存在方法的实现                     |
    | 实现               | 子类使用extends关键字来继承抽象类。如果子类不是抽象类的话，它需要提供抽象类中所有声明的方法的实现。 | 子类使用关键字implements来实现接口。它需要提供接口中所有声明的方法的实现 |
    | 构造器             | 抽象类可以有构造器                                           | 接口不能有构造器                                             |
    | 与正常Java类的区别 | 除了你不能实例化抽象类之外，它和普通Java类没有任何区别       | 接口是完全不同的类型                                         |
    | 访问修饰符         | 抽象方法可以有public、protected和default这些修饰符           | 接口方法默认修饰符是public。你不可以使用其它修饰符。         |
    | main方法           | 抽象方法可以有main方法并且我们可以运行它                     | 接口没有main方法，因此我们不能运行它。（java8以后接口可以有default和static方法，所以可以运行main方法） |
    | 多继承             | 抽象方法可以继承一个类和实现多个接口                         | 接口只可以继承一个或多个其它接口                             |
    | 速度               | 它比接口速度要快                                             | 接口是稍微有点慢的，因为它需要时间去寻找在类中实现的方法。   |
    | 添加新方法         | 如果你往抽象类中添加新的方法，你可以给它提供默认的实现。因此你不需要改变你现在的代码。 | 如果你往接口中添加方法，那么你必须改变实现该接口的类。       |

    [这里]: 抽象类与接口.md

    

16. ##### Java中IO流分为几种？

17. ##### BIO、NIO、AIO有什么区别？

18. ##### Files的常用方法都有哪些？

## Java核心面试题

### 主要面试题

### 反射

### 容器

### 异常

### 设计模式

## JavaWeb

## Spring

## SpringMVC

## MyBatis

1. ##### 什么是MyBatis

2. ##### MyBatis框架的优缺点

3. ##### MyBatis框架的使用场合

4. ##### MyBatis与Hibernate有哪些不同

5. ##### #{}和${}的区别是什么

6. ##### 当实体类中的属性名和表中的字段名不一样该怎么办

7. ##### 模糊查询like语句该怎么写

8. ##### 通常一个XML映射文件，都会写一个Dao接口与之对应，请问这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗?

9. ##### MyBatis是如何进行分页处理的？分页插件的原来是什么

10. ##### MyBatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？

11. ##### 如何执行批量插入？

12. ##### 如何获取自动生成的主键？

13. ##### 在mapper中如何传递多个参数？

14. ##### MyBatis动态sql有什么用？执行原理？有哪些动态sql

15. ##### XML映射文件中，除了常见的select|insert|update|delete标签外，还有哪些标签？

16. ##### 为什么说MyBatis是半自动ORM映射工具？它与全自动的区别在哪里？

17. ##### 一对一、一对多的关联查询？

18. ##### MyBatis实现一对一有几种方式？具体怎么操作的？

19. ##### MyBatis实现一对多又几种方式？怎么操作？

20. ##### MyBatis是否支持延迟加载？如果支持，它的实现原理是什么？

21. ##### MyBatis的一级、二级缓存

22. ##### 什么是MyBatis的接口绑定？有哪些实现方式？

23. ##### 使用MyBatis的mapper接口调用时又哪些要求？

24. ##### Mapper编写有哪几种方式？

25. ##### 简述MyBatis的插件运行原理，以及如何编写一个插件

## 数据库

### MySQl

### Oracle

## SpringBoot

## SpringCloud

## 多线程

## JVM面试题

# 前端面试题

## Javascript

## Jquery

## Ajax

## VUE

# 拓展内容

### 抽象类与抽象方法