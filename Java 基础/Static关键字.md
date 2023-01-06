## Static关键字

1. static：静态的

2. 可以用来修饰：属性、方法、代码块、内部类
   
   > **static修饰属性：** 
   > 
   > 使用static修饰的属性叫做静态变量 ，未使用static修饰的叫做非静态变量或实例变量
   > 
   > > **实例变量：** 在创建了类的多个对象后，每个对象都独立地拥有一套类中的非静态属性。当修改其中一个对象的非静态属性时，不会导致其他对象中同样的属性值改变。
   > > 
   > > **静态变量：** 在创建了类的多个对象后，多个对象共用同一个静态变量。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，该变量的值也已经改变了。
   > 
   > 一些说明：
   > 
   > * 静态变量随着类的加载而加载，可以直接“类.静态变量 ”的方式进行调用。而实例变量是随着对象的创建而创建的，晚于静态变量的创建。
   > 
   > * 由于类只会加载一次，则静态变量也只会存在一份。（存在方法区的静态域中）
   > 
   > * |        | 静态变量（类变量） | 实例变量 |
   >   |:------:|:---------:|:----:|
   >   | 类（调用）  | yes       | no   |
   >   | 对象（调用） | yes       | yes  |
   > 
   > **static修饰方法：**
   > 
   > 使用static修饰的方法叫做静态方法。静态方法随着类的加载而加载，可以通过 “类 . 静态方法 ” 的方式进行调用。
   > 
   > > 设置static的一些情况：
   > > 
   > > **属性：** 
   > > 
   > > * 被多个对象所共享，不会随着对象的不同而改变。
   > > * 常量也常常声明为 static
   > > 
   > > **方法：** 
   > > 
   > > * 操作静态属性的方法，通常设置为 static
   > > * 工具类中的方法，习惯上声明为 static。例如，`Math` , `Arrarys` , `Collections` 
   > 
   > 一些说明：
   > 
   > * |        | 静态方法 | 非静态方法 |
   >   |:------:|:----:|:-----:|
   >   | 类（调用）  | yes  | no    |
   >   | 对象（调用） | yes  | yes   |
   > 
   > * 静态方法中，只能调用静态的方法或属性；非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性。
   > 
   > * 在静态方法内，不能使用 `this` 关键字、`super` 关键字
   
   ----
   
   ## 应用
   
   ```java
   public class Account(){
       int id; //帐号（自动增加）
       double balance; //余额
   
       static double interestRate; //利率
       static int init = 1001; 
   
       public Account(){
           id = init++; //实现帐号自动生成
       }
       public Account(double balance){
           this();
           this.balance = balance;
       }
   }
   
   public class AccountTest {
       public static void main(String[] args) {
           Account acct1 = new Account();
           Account acct2 = new Account(20.0);
   
           Account.interestRate = 0.1;
           System.out.println("账户：" + acct1.id + "利率：" + acct1.interestRate);                 
           //账户：1001 利率：0.1
   
           Account.interestRate = 0.5;
           System.out.println("账户：" + acct1.id + "利率：" + acct1.interestRate); 
           //账户：1001 利率：0.5
           System.out.println("账户：" + acct2.id + "利率：" + acct1.interestRate); 
           //账户：1002 利率：0.5
       }
   }
   ```