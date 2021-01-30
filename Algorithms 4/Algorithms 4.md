# Algorithms 4

## 第一章	基础

### 1.1 基础编程模型

- 基础编程模型：描述和实现算法所用到的<u>语言特性、软件库和操作系统特性</u>的总称

#### 1.1.1 Java程序的基本结构

- 一段Java程序（类）：是一个静态方法（函数）库，或者定义了一个数据类型

- Java语言的基础（7种语法）：

  - 原始数据类型：byte, short, int, long, float, double, char, boolean

  - 六种语句：声明、赋值、条件、循环、调用和返回
  - 数组
  - 静态方法
  - 字符串
  - 标准输入/输出
  - 数据抽象

- 执行java程序：javac编译 --> java字节码文件 --> java运行

#### 1.1.2 原始数据类型与表达式

- 数据类型：一组数据和对其所能进行的操作的集合
- 4种最基本的原始数据类型
  - 整型，及其算术运算符(int)
  - 双精度实数类型，及其算数运算符(double)
  - 布尔型，{true, false}，及其逻辑操作(boolean)
  - 字符型，char
- java程序控制的是用*标识符*命名的*变量*
- java程序基本组成：
  - 原始数据类型
  - 标识符：字母、数字、下划线和$组成的字符串，<u>首字母不能是数字</u>
  - 变量：[任意标识符]
  - 字面量：值在源码中的表示，eg：1, 2, 'a' ......
  - 表达式
- 加减乘除：被重载过——同样的运算符，对不同的类型执行不同的操作
  - 运算产生的数据类型和参与运算的数据类型是相同的

##### 1.1.2.1 表达式

- 中缀表达式
- 优先级：尽量使用<u>括号</u>
  - *, /, %	--->	+, -
  - !    --->   &&    --->   ||

##### 1.1.2.2 类型转换

- 自动提升为更高级的数据类型：
  - 1 + 2.5 ：1提升为1.0
- ()转换：<u>浮点--->整型    截断小数部分而非四舍五入</u>
  - <u>(int)4.7    ---->    4</u>
  - (double)3    --->    3.0

##### 1.1.2.3 比较

- 混合类型运算符（布尔表达式）：
  - ==, !=, >, >=, <, <=

##### 1.2.2.4 其他原始类型

- int：2^32 个值，子长为32位的机器字
- double：64位
- short：16位
- long：64位
- char：16位
- byte：8位
- float：32位

#### 1.1.3 语句

- java程序由语句组成，语句能够通过创建变量和操作变量、对变量赋值并控制这些操作的执行流程来描述运算

- 代码段：花括号中的一系列语句

- 组成：

  - 声明语句

    - 一个变量名和类型在编译时关联起来

  - 赋值语句：=

    - 左边：单个变量
    - 右边：能够得到相应类型值的任意表达式

  - 条件语句

    - ```java
      if ( <boolean expression> ) { <block statements> }  // 只有单句时，可以省略括号
      else					  { <block statements> }
      ```

  - 循环语句

    - ```java
      while ( <boolean expression> ) 
      	{ <block statements> } // 循环体
      /*
      * break: 立即从循环中跳出
      * continue: 立即开始下一轮循环
      **/
      ```

  - 调用和返回语句

- 代码的结构：<u>嵌套</u>

#### 1.1.4 简便记法

- 声明并初始化

  ```java
  int i = 1;
  ```

- 隐式赋值

  - i++, ++i......
  - i += 2......

- <u>单语句代码段，花括号可省略</u>

- for循环

  ```java
  for (<initialize>; <boolean expression>; <increment>) {
      <block statements>
  }
  // 等价于 ===>
  <initialize>;
  while ( <boolean expression> ) {
      <block statements>;
      <increment>;
  } 
  ```

#### 1.1.5 数组

- 数组：顺序存储相同类型的多个数据
- 访问：索引，0 ~ (N - 1)，a[i]唯一表示第i+1个值

##### 1.1.5.1 创建并初始化数组

- 创建数组分三步：
  - 声明数组名字和类型
  - 创建数组：<u>需指定数组长度</u>
  - 初始化数组元素
- 完整模式

    ```java
    double[] a; // 声明数组
    a = new double[N]; // 创建数组
    for (int i = 0; i < N; i++)
        a[i] = 0.0; // 初始化数组
    ```

##### 1.1.5.2 简化写法

- 简化写法

  ```java
  double[] a = new double[N]; // 默认初始化
  ```

  - 默认初始化：
    - <u>数组类型初始化为0，布尔类型初始化为false</u>
  
- 声明初始化

  ```java
  int[] a = {1, 2, 3, 4}; // 声明创建并初始化一个数组
  ```

##### 1.1.5.3 使用数组

- 方括号的索引访问

- 一经创建，大小固定

- a.length 可获取数组长度

  - 适应范围外的索引，会在运行时抛出ArrayIndexOutOfBoundsException异常而终止

- 几个常用实现代码

  - max元素

    ```java
    double max = a[0];
    for (int i = 0; i < a.length; i++)
        if (a[i] > max) max = a[i];
    ```

  - 平均值

    ```java
    int N = a.length;
    double sum = 0.0;
    for (int i = 0; i < N; i++) 
        sum += a[i];
    double average = sum / N;
    ```

  - 赋值数组

    ```java
    int N = a.length;
    double[] b =  new double[N];
    for (int i = 0; i < N; i++) 
        b[i] = a[i];
    ```

  - 颠倒数组顺序

    ```java
    int N = a.length;
    for (int i = 0; i < N / 2; i++) {
        double temp = a[i];
        a[i] = a[N - 1 - i];
        a[N - 1 - i] = temp;
    }
    ```

  - 矩阵相乘

    ```java
    double result[][] = new double[matrix1.length][matrix2[0].length];
    for (int i = 0; i < matrix1.length; i++) // 控制行数
    	for (int j = 0; j < matrix2[0].length; j++) // 控制列数
    		for (int k = 0; k < matrix2.length; k++) // 控制次数
    			result[i][j] += matrix1[i][k] * matrix2[k][j];
    ```

##### 1.1.5.4 起别名

- 数组名表示整个数组
  - <u>一个数组变量赋予另一个数组变量（地址索引的赋值），则两个变量将会指向同一数组</u>
  - 如果**复制数组**，则应声明、创建并初始化一个新的数组，再按元素<u>挨个进行赋值</u>

##### 1.1.5.5 二维数组

- 即为：一维数组的数组
- M × N：M行，N列
- a[i]\[j]: 第i行，第j列的元素
- 同样会默认初始化
  - 数值初始化为0，布尔初始化为false

#### 1.1.6 静态方法

- java程序是以下其中一种：
  - 数据类型的定义
  - 静态方法库（函数）

##### 1.1.6.1 静态方法

- 静态方法的组成：
  - 签名：关键字public static以及函数的返回值、方法名以及一串各个类型的参数
  - 方法体：包含在{}中的代码

##### 1.1.6.2 调用静态方法

- 调用时表达式的一部分：方法的返回值代替表达式中的方法调用
- 仅有一个方法调用和一个分号组成的语句：用于产生副作用

##### 1.1.6.3 方法的性质

- 参数按值传递：改变一个参数变量的**值**对调用者没有影响
  - <u>数组参数是原数组的别名</u>，Arrays.sort()能够**改变**通过参数传递的<u>数组的内容</u>

- 方法名可以被重载

- 方法只有一个返回值，但是可以包含多个返回语句
  - 第一次执行到一个返回语句时，控制权将会回到调用代码中
- 方法可以产生副作用：void

##### 1.1.6.4 递归

- 方法可以调用自己
- 注意
  - 总有一个最简单的情况——方法的第一条语句总是一个包含return的条件语句
  - 递归调用总是去尝试解决一个<u>规模更小的子问题</u>，这样才能收敛到最简单情况
  - *递归调用的父问题和尝试解决的子问题之间不应该有交集*

```java
// 二分查找——递归实现
public static int rank(int[] arr, int key) {
    return rank(arr, key, 0, arr.length - 1);
}
private static int rank(int[] arr, int key, int lo, int hi) {
    if (lo > hi) return -1; // 数组中不存在key
    int mid = lo + ((hi - lo) >> 1); // 取中点——防止溢出
    if (arr[mid] > key)	rank(arr, key, lo, mid - 1);
    else if (arr[mid] < key) rank(arr, key, mid + 1, hi);
    else return mid;
}
```

##### 1.1.6.5 基础编程模型

- 静态方法库：一个Java类中的一组静态方法
- Java开发的基本模式：编写一个静态方法库（包含一个main()方法）来完成任务

##### 1.1.6.6 模块化编程

- 好处：
  - 代码量很大时，每次处理的模块大小仍然适中
  - 可以共享和重用代码而无需重新实现
  - 很容易用改进的实现替换老的实现
  - 可以为解决编程问题建立合适的抽象模型
  - 缩小调试范围

##### 1.1.6.7 单元测试

- Java编程的最佳实现之一：每个静态方法库中包含一个main()函数来测试库中的所有方法
  - 可以将main()方法作为一个开发用例
  - 也可以吧main编程一个测试用例来对所有代码进行全面测试
  - 用例变的复杂时，可将其独立成一个模块

##### 1.1.6.8 外部库

#### 1.1.7 API

- 目的：调用和实现分离 / 调用和实现的一份契约
- 可以学习一个StdRandom.java 和 StsStats.java 中的源码

#### 1.1.8 字符串

- 由一串字符（char）组成
- String类型的字面量包括一对双引号和其中的字符
- 非原始数据类型

##### 1.1.8.1 字符串拼接

- "+"

##### 1.1.8.2 类型转换

| String和数字之间相互转换的API       |                     |
| :---------------------------------- | ------------------- |
| *public class Integer*              |                     |
| static int parseInt(String s)       | String --->  int    |
| static String toString(int i)       | int  --->  String   |
| *public class Double*               |                     |
| static double parseDoubel(String s) | String ---> double  |
| static String toString(double x)    | double --->  String |

##### 1.1.8.3 自动转换

- 如果“ + ”的一个参数是字符串，Java自动将其他参数转化为字符串
  - 可以<u>通过""空字符串将任意数据类型转化为String</u>

##### 1.1.8.4 命令行参数

- 使程序接受到从命令行传递来的信息

#### 1.1.9 输入输出

- 一个Java程序和外界交流的简易模型：可以从*命令行参数*或者一个名为*标准输入流*的抽象字符流中获得输入，并将输出写入另一个名为*标准输出流*的字符流中

##### 1.1.9.1 命令和参数

- 终端窗口包含一个提示符，通过它我们能够向操作系统输入命令和参数
- Java类都包含一个静态方法main，它有一个String数组类型的参数args[]——我们输入的命令行参数，操作系统会将它传给Java。Java和操作系统都默认参数为字符串

| 命令  |                  参数                  |     作用     |
| :---: | :------------------------------------: | :----------: |
| javac |              .java 文件名              | 编译Java程序 |
| java  | .class文件名（不需要）<br>和命令行参数 | 运行Java程序 |
| more  |               任意文本名               | 打印文本内容 |

##### 1.1.9.2 标准输出

- StdOut库

##### 1.1.9.3 格式化输出

- printf

| 转 换 符 | 说  明             | 示  例       |
| :------- | ------------------ | ------------ |
| %s       | 字符串类型         | "mingrisoft" |
| %c       | 字符类型           | 'm'          |
| %b       | 布尔类型           | true         |
| %d       | 整数类型（十进制） | 99           |
| %f       | 浮点类型           | 99.99        |

   ![](L:\Dokuments\Java\Algorithms 4\img\printf.png)

```java
double d = 345.678;
        String s = "你好！";
        int i = 1234;
        // "%"表示进行格式化输出，"%"之后的内容为格式的定义。
        System.out.printf("%f", d);// "f"表示格式化输出浮点数。
        System.out.println();
        System.out.printf("%9.2f", d);// "9.2"中的9表示输出的长度，2表示小数点后的位数。
        System.out.println();
        System.out.printf("%+9.2f", d);// "+"表示输出的数带正负号。
        System.out.println();
        System.out.printf("%-9.4f", d);// "-"表示输出的数左对齐（默认为右对齐）。
        System.out.println();
        System.out.printf("%+-9.3f", d);// "+-"表示输出的数带正负号且左对齐。
        System.out.println();
        System.out.printf("%d", i);// "d"表示输出十进制整数。
        System.out.println();
        System.out.printf("%o", i);// "o"表示输出八进制整数。
        System.out.println();
        System.out.printf("%x", i);// "d"表示输出十六进制整数。
        System.out.println();
        System.out.printf("%#x", i);// "d"表示输出带有十六进制标志的整数。
        System.out.println();
        System.out.printf("%s", s);// "d"表示输出字符串。
        System.out.println();
        System.out.printf("输出一个浮点数：%f，一个整数：%d，一个字符串：%s", d, i, s);
        // 可以输出多个变量，注意顺序。
        System.out.println();
        System.out.printf("字符串：%2$s，%1$d的十六进制数：%1$#x", i, s);
    double x = 2.0 / 3;
    //保留两位小数,用printf与println的不同操作方法
    System.out.println("x is " + (int)(x * 100) / 100.0);
    System.out.printf("%.2f", x);
```

##### 1.1.9.4 标准输入

##### 1.1.9.5 重定向与管道

##### 1.1.9.6 基于文件的输入输出

##### 1.1.9.7 标准绘图库（基本方法）

##### 1.1.9.8 标准绘图库（控制方法）

#### 1.1.10 二分查找

- 注：数组必须是有序的

```java
public static int rank (int[] arr, int key) {
    // 数组必须是有序的
    int lo = 0;
    int hi = arr.length - 1;
    while (lo <= hi) {
        int mid = lo + ((hi - lo) >> 1); // 取中点——防止溢出
        if (arr[mid] > key)	hi = mid - 1;
        else if (arr[mid] < key) lo = mid + 1;
        else return mid;
    }
    return -1;
}
```

##### 1.1.10.3 白名单过滤

#### 1.1.11 展望

- 数据抽象 / 面向对象编程
- 数据抽象已经成为现代程序开发的核心
  - 允许通过*模块化编程*服用代码
  - 可轻易构造出*链式数据结构*
  - 可以准确的定义所面对的算法问题

### 1.2 数据抽象

- 数据类型：<u>一组值</u>和**一组对这些值操作**的集合
- 数据抽象：定义和使用数据类型
- Java编程的基础主要是使用*class*关键字构造被称为*引用类型*的数据类型
  - 此种编程风格——面向对象编程：核心概念是对象
- 抽象数据类型（ADT）：一种能够对使用者隐藏数据表示的数据类型
  - 主要不同：将<u>数据</u>和<u>函数的实现</u>关联，并将数据的表示方式<u>隐藏</u>起来
  - 重要之处：支持封装

#### 1.2.1 使用抽象数据类型

- 要使用一种抽象数据类型不一定要知道它是如何实现的

##### 1.2.1.1 抽象数据类型的API

- 计数器的API

  | public class Count |                                                     |
  | ------------------ | --------------------------------------------------- |
  | Count(String id)   | 创建一个名为id的计数器                              |
  | void increment()   | 将计数器的值加1                                     |
  | int tally()        | 该对象创建之后计数器加1的次数（返回当前计数器的值） |
  | String toString()  | 返回对象的字符串表示                                |

##### 1.2.1.2 继承的方法

- Java中所有的数据类型都会继承：toString(), equals(), compareTo(), hashCode()
- toString()
  - Java会在<u>**+**</u>用运算符 的任意数据类型的值和String值连接时调用该方法
  -  <u>默认实现</u>：返回该数据类型值的<u>内存地址</u>（即：返回引用的数值） ---> 并不实用，往往会重写

##### 1.2.1.3 用例代码

- 模块化编程：用例代码和抽象数据类型class分开编写

##### 1.2.1.4 对象

- **对象**：能够承载<u>数据类型的值</u>的**实体**
- 对象三大特性：
  - 状态：数据类型中的值
    - 可以为用例代码提供信息，或者产生某种副作用，或是被数据类型的操作说改变
    - <u>*数据类型的值*的表示细节与*用例代码*无关</u>
  - 标识：一个对象区别于另一个对象
    - 内存中的位置
  - 行为：数据类型的操作

- 引用：访问对象的一种方式
  - 可以认为引用即为内存地址

##### 1.2.1.5 创建对象

- 每种数据类型的值都存储于一个对象中
- 创建对象：new关键字 + （）---->  <u>触发构造函数</u>
- 构造函数：<u>无返回值</u>   <---   总是返回它的数据类型的对象的引用
- **使用了new** ----->
  - 为新的对象分配内存空间
  - 调用构造函数初始化对象中的值
  - 返回该对象的一个引用

```java
Counter heads = new Counter("heads");
// 左边：变量和对象的引用  关联的声明语句
// 右边：调用构造函数来创建一个对象
```

##### 1.2.1.6 调用实例方法

- 实例方法的意义：操作数据类型中的值
- 调用方式：对象变量名.实例方法名称(参数1, 参数2, ...)

|          |        实例方法        |    静态方法    |
| :------: | :--------------------: | :------------: |
|   举例   |   heads.increment()    | Math.sqrt(2.0) |
| 调用方式 |         对象名         |      类名      |
|   参量   | 对象的引用和方法的参数 |   方法的参数   |
| 主要作用 |   访问或改变对象的值   |   计算返回值   |

##### 1.2.1.7 使用对象

- 开发某种数据类型的用例：
  - 声明该类型的变量，以用来引用对象
  - 使用new关键字触发能够创建该类型的对象的一个构造函数
  - 使用变量名在语句或者表达式中调用实例方法

##### 1.2.1.8 赋值语句

- **引用类型的赋值语句**将会<u>创建该引用的**一个副本**</u>
  - 复制的是引用，而非实际的值
  - <u>不会创建新的对象</u>，只是创建另一个指向某个已经存在的对象的引用——别名：<u>两个变量名同时指向同一个对象</u>

- 原始数据类型：复制的是值

##### 1.2.1.9 将对象作为参数

- 调用一个需要参数的方法时：相当于
  - <u>每个参数值出现在赋值语句的右侧，参数名在赋值语句的左侧</u>
- **按值传递**：方法无法改变调用端变量的值
  - 原始数据类型：参数值和参数 两个变量互相独立
  - <u>引用类型：传递对象的引用</u>，虽然<u>无法改变原始引用</u>，但是**能够改变该对象的值**

##### 1.2.1.10 将对象作为返回值

- Java中只能有一个返回值——<u>有了对象实际上就能返回多个值</u>

##### 1.2.1.11 数组也是对象

- Java中，所有**非原始数据类型都是对象**
- 数组的特殊支持：声明、初始化和索引
- 将数组传给一个方法或是将一个数组变量放在赋值语句的右侧时，是在
  - <u>创建数组引用的一个副本，而非数组的副本</u>

##### 1.2.1.12 对象的数组

- 创建一个对象的数组
  - 使用[]语法调用数组的构造函数创建数组
  - 对于每个数组元素调用它的构造函数创建相应的对象
- 对象数组：由<u>对象的引用</u>组成的数组

#### 1.2.2 抽象数据类型举例

- java.lang中的标准Java系统类型
- 其他Java数据类型
- 标准I/O类型
- 用于用例的面向数据的数据类型
- 用于算法分析的数据类型
- 集合数据类型
- 面向数据的图数据类型
- 面向操作的图数据类型

##### 1.2.2.1 几何对象

##### 1.2.2.2 信息处理

##### 1.2.2.3 字符串

- Java中的部分字符串API

  | Public class String |                          |                                             |
  | ------------------- | ------------------------ | ------------------------------------------- |
  |                     | String()                 | 创建空字符串                                |
  | int                 | length()                 | 字符串长度                                  |
  | int                 | charAt(int i)            | 第i个字符                                   |
  | int                 | indexOf(String p)        | p第一次出现的位置（没有返回 -1）            |
  | int                 | indexOf(String p, int i) | p在i个字符后第一次出现的位置（没有返回 -1） |
  | String              | concat(String t)         | 将t附在字符串结尾                           |
  | String              | substring(int i, int j)  | 子串(第i个到j-1个)                          |
  | String[]            | split(String delim)      | 使用delim分隔符切割字符串                   |
  | int                 | compareTo(String t)      | 比较字符串                                  |
  | boolean             | equals(String t)         | 该字符串的值和t值是否相同                   |
  | int                 | hashCode()               | 散列值                                      |

- 典型字符串处理代码

  - 回文字符串判断

    ```java
    public static boolean isPalindrome(String s) {
        int N = s.length();
        for (int i = 0; i < N / 2; ++i) {
            if (s.charAt(i) != s.charAt(N - 1 - i))
                return false;
        }
        return true;
    }
    ```

  - 命令行参数中提取文件名和拓展名

    ```java
    String s = args[0];
    int dot = s.indexOf(".");
    String base = s.substring(0, dot);
    String extension = s.substring(dot + 1, s.length());
    ```

  - 打印标准输入中所有含有通过命令行指定行指定的字符串的行

    ```java
    String query = args[0];
    while (!StdIn.isEmpty()) {
        String s = StdIn.readLine();
        if (s.contains(query)) StdIn.prindln(s);
    }
    ```

  - 以空白字符为分隔符从StdIn中创建一个字符串数组

    ```java
    String input = StdIn.readAll();
    String[] words = input.split("\\s+"); 
    //  \\s : 空格,回车,换行等空白符
    //    + : 一个或多个
    ```

  - 检查一个字符串数组中的元素是否按照字母表顺序排列

    ```java
    public boolean isSorted(String[] a) {
        for (int i = 1; i < a.length; i++) {
            if (a[i - 1].compareTo(a[i]) > 0)
                return false;
        }
        return true;
    }
    ```

    - public int **compareTo**(String anotherString)
      
      - 按字典顺序比较两个字符串。该比较基于字符串中各个字符的 Unicode 值。按字典顺序将此 String 对象表示的字符序列与参数字符串所表示的字符序列进行比较。如果按字典顺序<u>此 String 对象位于参数字符串之前，则比较结果为一个负整数</u>。如果按字典顺序此 String 对象位于参数字符串<u>之后</u>，则比较结果为一个<u>正整数</u>。如果<u>这两个字符串相等，则结果为 0；compareTo 只在方法 equals(Object) 返回 true 时才返回 0</u>。 
      
      - 这是字典排序的定义。如果这两个字符串不同，那么它们要么*在某个索引处的字符不同*（该索引对二者均为有效索引），要么*长度不同*，或者同时具备这两种情况。如果它们在一个或多个索引位置上的字符不同，假设 k 是这类索引的最小值；则在位置 k 上具有较小值的那个字符串（使用 < 运算符确定），其字典顺序在其他字符串之前。在这种情况下，compareTo 返回这两个字符串在位置 k 处两个char 值的差，即值： 
      
         this.**charAt(k)** - anotherString.**charAt(k)**
      
      - 如果<u>没有字符不同的索引位置</u>，则较短字符串的字典顺序在较长字符串之前。在这种情况下，compareTo 返回这两个字符串长度的差，即值： 
         this.length() - anotherString.length()
      
      ```java
      String s1 = "test";
      String s2 = "test123";
      String s3 = "tast";
      System.out.println(s1.compareTo(s2));  // -3
      System.out.println(s2.compareTo(s1));  // 3
      System.out.println(s1.compareTo(s3));  // 4
      System.out.println(s3.compareTo(s1));  // -4
      ```

##### 1.2.2.4 再谈输入输出

#### 1.2.3 抽象数据类型的实现

```java
public class Counter { // 类名
    // 实例变量
    private final String name;
    private int count;
    
    // 构造函数
    public Counter(String id) { // 类名
        name = id;
    }
    
    // 实例方法
    public void increment() {
        count++;
    }
    public int tally() {
        return count;
    }
    public String toString() {
        return count + " " + name; // name：实例变量名 
    }
    
    // 测试用例
    public static void main(String[] args) {
        // 创建并初始化对象
        Counter heads = new Counter("heads");
        Counter tails = new Counter("tails"); // 触发构造函数
        
        heads.increment();
        heads.increment();
        tails.increment();
        
        System.out.println(heads + " " + tails); // 自动调用toString方法
        System.out.println(heads.tally() + tails.tally()); 
    }
}
```

##### 1.2.3.1 实例变量

- 实例变量：
  - private final String name;
  - private int count;
- 实例变量和局部变量的区别：
  - 每一时刻每个局部变量只会有一个值
  - 每个实例变量对应无数个值（每个实例对象都有一个）

##### 1.2.3.2 构造函数

- 每个Java类至少含有一个构造函数以创建一个对象的标识
- 类似于一个静态方法，但是能够直接访问实例变量并向调用者返回一个该对象的引用
- 名称总和类名相同
- 可重载
- 若没有定义，类将提供一个默认的无参数的构造函数，并将实例变量初始化：0，false，null
- 可以在声明语句中初始化实例变量改变默认值
- 使用new关键字时，自动触发实例变量

##### 1.2.3.3 实例方法

- 实例方法： 每个对象的行为

##### 1.2.3.4 作用域

- Java中的三种变量
  - 参数变量
  - 实例变量
    - 如果出现二义性，可用this前缀区别实例变量
  - 局部变量

##### 1.2.3.5 API、用例与实现

- 为了强调用例和实现的分离，一般将用例独立成为含有一个静态方法main()的类
- 开发每种数据类型是为了满足<u>用例的需求</u>，分为*三步*用抽象数据类型满足：
  - 定义一份API：API的作用是<u>将使用和实现分离</u>，

#### 1.2.4 更多抽象数据类型的实现

##### 1.2.4.1 日期

##### 1.2.4.2 维护多个实现

##### 1.2.4.3 累加器

##### 1.2.4.4 可视化的累加器

#### 1.2.5 数据结构的设计......

- 抽象数据类型：一种向用例

### 1.3 背包、队列和栈

- Bag, Queue, and Stack
- 本节目标
  - 对集合中对象的表示方式将直接影响各种操作的效率
  - 泛型和迭代
  - 链式数据结构的重要性

#### 1.3.1 API

- 泛型可迭代的基础数据类型的API

  | 背包Bag                                              |                |
  | ---------------------------------------------------- | :------------- |
  | public class Bag\<Item\> implements Iterable\<Item\> |                |
  | Bag()                                                | 创建一个空背包 |
  | void add(Item item)                                  | 添加一个元素   |
  | boolean isEmpty()                                    | 是否为空       |
  | int size()                                           | 元素数量       |

  | 先进先出（FIFO）队列                                   |                  |
  | ------------------------------------------------------ | :--------------- |
  | public class Queue\<Item\> implements Iterable\<Item\> |                  |
  | Queue()                                                | 创建一个空队列   |
  | void enqueue(Item item)                                | 添加一个元素     |
  | Item dequeue()                                         | 删除最早添加元素 |
  | boolean isEmpty()                                      | 是否为空         |
  | int size()                                             | 元素数量         |

  | 先进后出（FILO，下压）栈                               |                  |
  | ------------------------------------------------------ | :--------------- |
  | public class Stack\<Item\> implements Iterable\<Item\> |                  |
  | Stack()                                                | 创建一个空栈     |
  | void push(Item item)                                   | 添加一个元素     |
  | Item pop()                                             | 删除最近添加元素 |
  | boolean isEmpty()                                      | 是否为空         |
  | int size()                                             | 元素数量         |

##### 1.3.1.1 泛型

- 泛型（参数化类型）：存储任意类型的数据
  - 一份API（和一次实现）处理所有类型的数据

##### 1.3.1.2 装箱

- 使泛型代码能够处理原始数据类型

  ```java
  Stack<Integer> stack = new Stack<Integer>();
  stack.push(17); // 自动装箱（int ---> Integer）
  int i = stack.pop(); // 自动拆箱（Integer ---> int）
  ```

- | 原始数据类型    | 引用类型  |
  | --------------- | --------- |
  | int（4字节）    | Integer   |
  | byte（1字节）   | Byte      |
  | short（2字节）  | Short     |
  | long（8字节）   | Long      |
  | float（4字节）  | Float     |
  | double（8字节） | Double    |
  | char（2字节）   | Character |
  | boolean（未定） | Boolean   |

##### 1.3.1.3 可迭代的几何类型

- 迭代访问集合中的所有元素，只是用某种方式对每个元素进行处理

  ```java
  Queue<Transaction> collection = new Queue<>();
  // 若集合可迭代，用例用一行代码就可以打印出列表
  for (Transaction t : collection) {  // foreach语句
      System.Out.println(t);
  }
  ```

##### 1.3.1.4 背包

- 不支持从中删除元素的集合数据类型
- 目的：帮助用例**收集元素**并**迭代遍历所有收集到的元素**
- 迭代的**顺序不确定**，且与**用例无关**

##### 1.3.1.5 先进先出队列

- foreach语句迭代访问时，元素处理的顺序就是它们被添加到队列中的顺序

##### 1.3.1.6 下压栈

- 后进先出

##### 1.3.1.7 算数表达式求值

- 表达式组成：括号、运算符和数字（操作数）

- E.W.Dijkstra在20世纪60年代发明了一个简单的算法：使用两个栈 —— 一个保存运算符，一个保存数字（操作数）
  - 根据以下四种情况，从左到右逐个将实体送入栈处理：
    - 数字压入数字栈
    - 运算符压入运算符栈
    - 忽略左括号
    - 在遇到右括号时弹出一个运算符，弹出所需数量的数字，并将运算符和数字的运算结果压入操作数栈  ---> 其实，该<u>运算结果代替了括号内表达式的值</u>
  
  ```java
  /**
  * 双栈算数表达式求值
  * designed by E.W.Dijkstra
  * 简化版：未省略括号
  * @param str
  * @return
  */
  private static double calculate(String str) {
      String[] strs = str.split(" ");
      Stack<String> ops = new Stack<>(); // 操作符栈
      Stack<Double> vals = new Stack<>(); // 数字栈
      for (String s : strs) {
          if (s.equals("(")) ;
          else if (s.equals("+") ||
                   s.equals("-") ||
                   s.equals("*") ||
                   s.equals("/") ||
                   s.equals("sqrt") ) {
              ops.push(s);
          }
          else if (s.equals(")")) {
              // 在遇到右括号时弹出一个运算符，弹出所需数量的数字，并将运算符和数字的运算结果压入操作数栈
              // --->
              // 其实，该<u>运算结果代替了括号内表达式的值</u>
              String op = ops.pop();
              double v = vals.pop();
              if (op.equals("+")) v = vals.pop() + v;
              else if (op.equals("-")) v = vals.pop() - v;
              else if (op.equals("*")) v = vals.pop() * v;
              else if (op.equals("/")) v = vals.pop() / v;
              else if (op.equals("sqrt")) v = Math.sqrt(v);
              vals.push(v);
          } else {
              vals.push(Double.parseDouble(s));
          }
      }
      return vals.pop();
  }
  ```

#### 1.3.2 集合类数据类型的实现

##### 1.3.2.1 定容栈

- ```java
  /**
   * 定容字符串栈
   */
  public class FixedCapacityStackOfStrings {
      private String[] a; // stack entries
      private int N; // size
  
      public FixedCapacityStackOfStrings(int n) {
          a = new String[n];
      }
  
      /**
       * 是否为空
       * @return
       */
      public boolean isEmpty() {
          return N == 0;
      }
  
      /**
       * 字符串数量
       * @return
       */
      public int size() {
          return N;
      }
  
      /**
       * push元素
       * @param item
       */
      public void push (String item) {
          a[N++] = item;
      }
  
      /**
       * 弹出最近添加的String
       * @return
       */
      public String pop() {
          return a[--N];
      }    
  }
  ```

##### 1.3.2.2 泛型

- FixedCapacityStackOfStrings的第一个缺点：<u>只能处理String对象</u>， ---> **泛型**

  - ```java
    public class FixedCapacityStackOfStrings<Item>
    ```

  - String用Item代替

  - **a = (Item[]) new Object[n];**  // 强制转换成Item[]类型

- ```java
  public class FixedCapacityStack<Item> {
      private Item[] a; // stack entries
      private int N; // size
  
      public FixedCapacityStack(int n) {
  //        a = new Item[n];  // 错误
          a = (Item[]) new Object[n];  // 强制转换成Item[]类型
      }
  
      /**
       * 是否为空
       * @return
       */
      public boolean isEmpty() {
          return N == 0;
      }
  
      /**
       * 字符串数量
       * @return
       */
      public int size() {
          return N;
      }
  
      /**
       * push元素
       * @param item
       */
      public void push (Item item) {
          a[N++] = item;
      }
  
      /**
       * 弹出最近添加的Item
       * @return
       */
      public Item pop() {
          return a[--N];
      }
  }
  
  ```

##### 1.3.2.3 调整数组大小

- 数组表示栈的内容：要预估栈的最大容量；

  - 数组一旦创建，不能更改 ， 栈的使用空间只能是最大容量的一部分  <--- <u>动态调整数组大小</u>
  - 集合变的比数组更大，有可能会溢出  <--- <u>push中检测是否满，添加isFull() 方法</u>

- 实现方法：

  1. 将栈移动到另一个大小不同的数组中

     ```java
     /**
     * 将大小为 N <= max 的栈移动到一个新的max大小的数组中
     * @param max
     */
     private void resize(int max) {
     Item[] temp = (Item[]) new Object[max];
     for (int i = 0; i < N; i++) temp[i] = a[i];
     a = temp;
     }
     ```

  2. push()中检查能否容纳新的元素，不能则数组长度加倍

     ```java
     public void push (Item item) {
         if (N == a.length) resize(a.length * 2);
         a[N++] = item;
     }
     ```

  3. pop()中检查数组是否太大，太大则数组长度减半

     - if (N > 0 && N == **a.length / 4**) resize(a.length / 2); //数组长度改变之后，状态是<u>半满</u>；<u>下次改变数组大小之前，仍能**多次push和pop**</u>

     ```java
     public Item pop() {
         Item item = a[--N];
         a[N] = null; // 避免对象游离
         if (N > 0 && N == a.length / 4) resize(a.length / 2);
         // 数组长度改变之后，状态是半满；下次改变数组大小之前，仍能多次push和pop
         return item;
     }
     ```

##### 1.3.2.4 对象游离

- 游离：保存一个不需要对象的引用
- Java垃圾回收机制：回收所有无法被访问的对象内存
- <u>a[N] = null; // 避免对象游离</u>
  - 覆盖无用的引用，使系统可以在用例用完被弹出的元素后回收它的内存

##### 1.3.2.5 迭代

- foreach语句只是while语句（像for）的一种间歇方式

  - ```java
    // foreach
    Stack<String> collection = new Stack<String>();
    for (String s : collection) 
        System.out.println(s);
    ```

  - ```java
    // while
    Stack<String> collection = new Stack<String>();
    Iterator<String> i = collection.iterator();
    while (i.hasNext()) {
        String s = i.next();
        System.out.println(s);
    }
    ```

- 由上述代码，可知：**任意可迭代的几何数据类型汇中需要实现：**

  - 必须实现一个iterator()方法并返回一个Iterator对象
  - Iterator类必须实现两个方法：hasNext()（返回一个布尔值）和next()（返回集合中的一个泛型元素）

- 要使一个类可迭代 ---> 声明中加入 implements Iterable\<Item\>  （即java.<u>*lang*</u>.Iterable）:

  - ```java
    public interface Iterable<T> {
        Iterator<T> iterator();  // 返回一个迭代器
    }
    ```

- 迭代器：实现了hasNext()和next()方法的类的对象，由以下接口所定义（java.<u>*util*</u>.Iterator）

  ```java
  public interface Iterator<Item> {
      boolean hasNext();
      Item next();
      void remove();
      // 虽然有remove方法，通常为空，因为希望避免在迭代中穿插修改数据结构的操作
  }
  ```

- **过程**：

1. 使类可迭代： 声明中加入 implements Iterable\<Item\>
2. 类中添加方法：iterator(), 并返回一个迭代器Iterator\<Item\>

 ```java
 @Override
 public Iterator<Item> iterator() {
     return new ReverseArrayIterator();  //逆序遍历整个数组
 }
 ```

3. 实现ReverseArrayIterator

 ```java
 /**
  * 嵌套类：可以访问包含它的类的实例变量（即：a[]和 N）
  * 支持先进后出的迭代
  */
 private class ReverseArrayIterator implements Iterator<Item> {
     private int i = N;
 
     @Override
     public boolean hasNext() {
         return i > 0;
     }
 
     @Override
     public Item next() {
         return a[--i];
     }
 }
 ```

- **下压FILO栈**(动态调整数组大小)实现:

  - ```java
    package chapter1_3;
    
    import java.util.Iterator;
    
    public class ResizingArrayStack<Item> implements Iterable<Item>{
        private Item[] a; // stack entries
        private int N; // size
    
        public ResizingArrayStack(int n) {
    //        a = new Item[n];  // 错误
            a = (Item[]) new Object[n];  // 强制转换成Item[]类型
        }
    
        /**
         * 是否为空
         * @return
         */
        public boolean isEmpty() {
            return N == 0;
        }
    
        /**
         * 字符串数量
         * @return
         */
        public int size() {
            return N;
        }
    
        /**
         * 将大小为 N <= max 的栈移动到一个新的max大小的数组中
         * @param max
         */
        private void resize(int max) {
            Item[] temp = (Item[]) new Object[max];
            for (int i = 0; i < N; i++) temp[i] = a[i];
            a = temp;
        }
    
        /**
         * push元素
         * @param item
         */
        public void push (Item item) {
            if (N == a.length) resize(a.length * 2);
            a[N++] = item;
        }
    
        /**
         * 弹出最近添加的Item
         * @return
         */
        public Item pop() {
            Item item = a[--N];
            a[N] = null; // 避免对象游离
            if (N > 0 && N == a.length / 4) resize(a.length / 2);
            // 数组长度改变之后，状态是半满；下次改变数组大小之前，仍能多次push和pop
            return item;
        }
    
        @Override
        public Iterator<Item> iterator() {
            return new ReverseArrayIterator();
        }
    
        /**
         * 嵌套类：可以访问包含它的类的实例变量（即：a[]和 N）
         * 支持先进后出的迭代
         */
        private class ReverseArrayIterator implements Iterator<Item> {
            private int i = N;
    
            @Override
            public boolean hasNext() {
                return i > 0;
            }
    
            @Override
            public Item next() {
                return a[--i];
            }
        }
    }
    ```

#### 1.3.3 链表

- 链表：一种递归的数据结构
  - 或者为空null，或者指向一个**节点**（Node）的引用
  - 节点：含有一个<u>泛型的元素</u>和一个<u>指向另一条链表的引用</u>

##### 1.3.3.1 节点记录

- 嵌套类定义节点的抽象数据类型

  - ```java
    // 节点嵌套类
    private class Node {
        Item item;
        Node next;  // 链式本质
    }
    ```

  - 标记为**private**：并不是为用例准备的

- Node和它的用例代码都会封装在相同的类中，且无法被该类的用例访问（因为私有）