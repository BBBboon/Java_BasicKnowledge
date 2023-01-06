# String类型变量的使用

1. 声明String类型变量时，使用一对" "
2. String可以和8种基本数据类型变量做运算，且运算只能是**连接运算（用+符号）**，运算结果仍然是String类型。若int型和char型、char型和char型相加结果都是int型。

## 一些例子：

1. 字符串之间加和

   ```java
   int number = 1001;
   String numberStr = "学号：";
   String info = numberStr + number;
   ```

   输出>> 学号：1001

2. 字符串和字符和整型的加和

   ```java
   //单引号是字符型，双引号字符串
   char c = 'a';
   int num = 10;
   String str = "hello";
   ```
   
   ```java
   //字符型和整型相加的结果再和字符串相加得：107hello
   System.out.println(c + num + str); 
   
   //字符型先和字符串相加得到一个字符串又和整形相加得：ahello10
   System.out.println(c + str + num); 
   
   //内部括号里的整型和字符串加和为字符串，再和外面的字符型加和，最后结果为字符串：a10hello
   System.out.println(c + (num + str)); 
   
   //字符串和整形加和得字符串，然后再和字符型相加最后结果为字符串：hello10a
   System.out.println(str + num + c);
   ```
   
   ```java
   //直接输出字符串
   System.out.println("*  *"); //*  *
   //char型相加得到int型然后再和char型相加得int型
   System.out.println('*' + '\t' + '*'); //93
   //char型和字符串相加得到一个新的字符串，再和char型相加还是字符串
   System.out.println('*' + "\t" + '*'); //*  *
   //char型和char型先加法得到一个int，然后再和字符串连接
   System.out.println('*' + '\t' + "*"); //51*
   //括号内先和字符串相连接，再和外面的连接
   System.out.println('*' + ('\t' + "*")); //*  *
   ```
   
   小练习：
   
   ```java
   //浮点型加String型，得到一个字符串"3.5"
   String str2 = 3.5f + "";
   System.out.println(str2); //3.5
   ```
   
   

