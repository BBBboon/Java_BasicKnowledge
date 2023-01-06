# Java 包装类

* 理解：使八种基本数据类型有了相应的引用数据类型，有了类的特点就可以调用类中的方法，一些面向对象的特征才得以体现出来。

| 基本数据类型  | 包装类       |
|:-------:|:---------:|
| byte    | Byte      |
| short   | Short     |
| int     | Integer   |
| long    | Long      |
| float   | Float     |
| double  | Double    |
| boolean | Boolean   |
| char    | Character |

## 基本数据类型转换为包装类

**方法：**  调用包装类的构造器

* 整形

```java
int num = 10;
System.out.println(num.toString()); //错误！因为基本数据类型无法调用方法。
Integer in1 = new Integer(num);
System.out.println(in1.toString()); //转换为包装类后可以调用丰富的方法。

Integer in2 = new Integer("123");
System.out.println(in2.toString()); //也可以输入String型，但是只能有数字不能带字符
```

* 浮点型

```java
Float f1 = new Float(12.3f);
Float f2 = new Float("12.3");
System.out.println(f1);
System.out.println(f2.toString());
```

* 布尔类型

```java
Boolean b1 = new Boolean(true); 
Boolean b2 = new Boolean("TrUe"); 
System.out.println(b2); //布尔类型比较特殊，只要不是忽略大小写的true，一律都是false
Boolean b3 = new Boolean("true123");
System.out.println(b3); //false
```

## 包装类转换为基本数据类型

**方法：** 调用包装类的xxxValue( )

* Integer

```java
Integer in1 = new Integer(12);

int i1 = in1.intValue();
System.out.println(i1 + 1); //转换为基本数据类型后可以方便加减乘除
```

* 浮点型

```java
Float f1 = new Float(12.3);
float f2 = f1.floatValue();
System.out.println(f2 + 1);
```

## 自动装箱与自动拆箱（JDK 5.0 新特性）

**说明：** 自动装箱：基本数据类型 ——> 包装类            自动拆箱：包装类——>基本数据类型

* 自动装箱

```java
int num = 10;
Integer i = num; //自动装箱

boolean boo = true;
Boolean b = boo;
```

* 自动拆箱

```java
System.out.println(i.toString());
int num = i; //自动拆箱
```

## 基本数据类型、包装类转换为String类型

**方法：** 调用String重载的valueOf（Xxx xxx）

```java
int num = 10;
String str1 = num + ""; //方式一：使用连接运算符

//基本数据类型转换
float f = 12.3f;
String str2 = String.valueOf(f); //"12.3" 方式二：调用String重载的valueOf（Xxx xxx） 

//包装类转换
Double d = new Double(12.4);
String str3 = String.valueOf(d); //"12.4"
```

## String类型转换为基本数据类型、包装类

**方法：** 调用包装类的parseXxx(String s)

```java
String str1 = "123";
int num = Integer.parseInt(str1);
System.out.printin(num + 1);

String str2 = "true";
boolean b = Boolean.parseBoolean(str2);
System.out.println(b);
```

## 一些面试题

1. ```java
   Object o1 = true ? new Integer(1) : new Double(2.0); //三元运算符
   System.out.prointln(o1); //结果为1.0
   
   Object o2;
   if(true)
       o2 = new Integer(1);
   else
       o2 = new Double(2.0);
   System.out.println(o2); //结果为1
   ```
   
   第一段代码Integer自动类型提升为Double，所以输出为1.0
   
   - 三元运算符的一些补充知识：
     
     1. 说明：需要三个数据才能进行操作的运算符
     
     2. 数据类型 变量名称 = 条件判断 ? 表达式A : 表达式B
        
        若判断为true，则将A的值赋给左侧变量；若为false，则将B的值赋给左侧变量。
        
        示例：
        
        ```java
        int a = 10;
        int b = 20;
        
        int max = a > b ? a : b; //结果为20
        ```
     
     3. 注意：表达式A和B必须都符合左侧数据类型的要求；表达式A和表达式B的类型可以统一，必要时其中一个表达式可以自动类型提升。

2. ```java
   Integer i = new Integer(1);
   Integer j = new Integer(1);
   System.out.println(i == j); //false 引用数据类型比较地址值
   
   Integer m = 1;
   Integer n = 1; //自动装箱
   System.out.println(m == n); //true 都用数组中的值，所以是同一个地址
   
   Integer x = 128;
   Integer y = 128;
   System.out.println(x == y); //false 超出数组范围，new新的对象地址不同
   ```
   
   `Integer` 内部定义了`IntegerCache` 结构，该结构中定义了`Integer[]` 保存-128 ~ 127范围内的整数。若我们采用自动装箱的方式给 `Integer` 赋值的范围在-128 ~ 127内时，我们可以直接使用数组中的元素儿不用再去new了。
   
   ----
   
   ## 练习
   
   ```java
   import java.util.Scanner;
   import java.util.Vector;
   
   public class ScoreTest {
       public static void main(String[] args) {
           Scanner scan = new Scanner(System.in);
           Vector v = new Vector(); //相当于数组，但是不需要提前指定长度
           int maxScore = 0;
           for(;;) {
               System.out.println("请输入学生成绩：（当输入为负数时表示结束）");
               int score = scan.nextInt();
               if(score < 0) {
                   break;
               }
               if(score > 100) {
                   System.out.println("输入的成绩非法，请重新输入！");
                   continue;
               }
               Integer inScore = new Integer(score);
               v.addElement(inScore); //多态 添加操作：v.addElement(Object obj)
               if(maxScore < score) {
                   maxScore = score;
               }
           }
   
               char level;
               for(int i = 0;i < v.size();i++) {
                   Object obj = v.elementAt(i);
                   Integer inScore = (Integer)obj;
                   int score = inScore.intValue();
   
                   if(maxScore - score <= 10) {
                       level = 'A';
                   }else if(maxScore - score <= 20) {
                       level = 'B';
                   }else if(maxScore - score <= 30) {
                       level = 'C';
                   }else {
                       level = 'D';
                   }
                   System.out.println("student-" + i + " score is " + score + " , level is " + level);
               }
       }
   }
   ```
