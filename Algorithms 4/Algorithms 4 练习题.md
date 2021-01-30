# Algorithms 4 练习题

## 第一章 基础

### 1.1 基础编程模型

1.  System.out.printf用法

   | 转 换 符 | 说  明             | 示  例       |
   | :------- | ------------------ | ------------ |
   | %s       | 字符串类型         | "mingrisoft" |
   | %c       | 字符类型           | 'm'          |
   | %b       | 布尔类型           | true         |
   | %d       | 整数类型（十进制） | 99           |
   | %f       | 浮点类型           | 99.99        |

   ![](img\printf.png)

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

2. && 比 || 的优先级更高

3. String.format("%.5f", data) : 也可以控制小数位数

4. String 比较数值要用equals

5. Integer.toBinaryString(int a) : 转化为二进制

6. Arrays.deepToString() : 打印二维数组

7. in.nextLine() : 输入中的换行

8. Integer.parseInt ：String -> int

9. 欧几里得算法：两个整数的最大公约数等于其中较小的那个数和两数相除余数的最大公约数

   ------

   a可以表示成a = kb + r（a，b，k，r皆为正整数，且r<b），则r = a mod b
   假设d是a,b的一个公约数，记作d|a,d|b，即a和b都可以被d整除。

   <span style = "color:red">而r = a - kb，两边同时除以d，r/d=a/d-kb/d=m，由等式右边可知m为整数，因此d|r</span>
   因此d也是b,a mod b的公约数
   假设d是b,a mod b的公约数, 则d|b,d|(a-k*b),k是一个整数。
   进而d|a.因此d也是a,b的公约数
   因此(a,b)和(b,a mod b)的公约数是一样的，其最大公约数也必然相等，得证


### 1.2 数据抽象

1. 区别使用原始数据类型和引用数据类型的原因是什么？为什么不只用引用类型？
   
   - 性能：原始数据类型更接近计算机硬件支持的数据类型，程序运行的更快
   
2. 数据类型必须是抽象吗？
   
   - 不；也可以public和protected的方式来访问实例变量
   
3. 在Java中，创建引用的方法只有一种（new），改变引用的方法也只要一种（赋值语句）

4. 实现继承有什么问题? 子类继承阻碍模块编程的原因？
   - 父类的任何改动都会影响到他的所有子类（脆弱的基类问题）
   - 子类代码可以访问所有实例变量，可能会扭曲父类代码的意图
   
5. 什么是null 空？
   
   - 不指向任意变量的字面量，引用null调用方法 ---> NullPointerException ，---》 请检查并确认构造函数是否正确的初始化了类的所有实例变量
   
6. String 字符串的创建和copy引用

   - public final class，创建以后不能改变

   - 用“”创建赋值时候，会先在“常量池”中检索，若存在，则直接赋值一个引用，没有在去创建值

     ```java
     String s1 = "hello";
     String s2 = "hello";
     System.out.println(s1 == s2); // true
     ```

   - new 创建字符串，都是重新创建

     ```java
     String s1 = "hello";
     String s2 = new String("hello");
     System.out.println(s1 == s2); // false
     ```

   - ```java
     String s1 = "hello";
     String s2 = s1;        
     s1 = "world";
     System.out.println(s1); // world
     System.out.println(s2); // hello
     ```

7. 传参数时，传的是引用

   ```java
   private static void exchange(int[] a, int[] b) {
       int[] t = a;
       a = b;
       b = t;
   }
   public static void main(String[] args) {
       int[] a = {1, 2};
       int[] b = {4, 3};
       System.out.println(Arrays.toString(a));
       System.out.println(Arrays.toString(b));
       System.out.println("函数交换后：");
       exchange(a, b);
       System.out.println(Arrays.toString(a));
       System.out.println(Arrays.toString(b));
       /**
        * 没有发生交换
        * [1, 2]
        * [4, 3]
        */
       int[] t = a;
       a = b;
       b = t;
       System.out.println("直接操作交换：");
       System.out.println(Arrays.toString(a));
       System.out.println(Arrays.toString(b));
       /**
        * 发生交换
        * [4, 3]
        * [1, 2]
        */
       Arrays.sort(a);
       System.out.println("排序：");
       System.out.println(Arrays.toString(a));
       /**
        * 发生排序，因为操作的是数组中的元素（基本类型）
        * [3, 4]
        */
   }
   ```

8. ![image-20210130230409848](img/image-20210130230409848.png)

