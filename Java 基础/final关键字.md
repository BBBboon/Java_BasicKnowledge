# final关键字

1. final修饰类
   
   * 此类不能被其他类所继承（如 `String`类，`System`类，`StringBuffer`类）
     
     ```java
     final class A{
     
     }
     class B extends A{
     
     } //报错
     ```

2. final修饰方法
   
   * 此方法不可以被重写
     
     ```java
     class A{
         public final void show(){
         }
     }
     class B extends A{
         public void show(){
         } //报错
     }
     ```

3. final修饰变量
   
   * 当用final修饰变量时，此时的变量可以看成一个常量
   
   * final修饰属性，可以赋值的位置有：
     
     > 显式初始化
     > 
     > 代码块中初始化
     > 
     > 构造器中初始化
     
     ```java
     public class FinalTest{
     
         final int A = 1;
         final int B;
         final int C;
     
         {
             B = 1;
         }
     
         public FinalTest(){
             C = 3;
         }
     }
     ```
   
   * final修饰局部变量：
     
     ​    当使用final修饰形参时，表明此形参是一个常量。当调用此方法时，应给常量赋一个实参，一旦赋值以后，就只能在这个方法体内使用这个形参，不能重新赋值了。