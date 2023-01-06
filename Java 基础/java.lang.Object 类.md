# java.lang.Object 类

## Object类的介绍

1. Object类是所有 Java类的根父类

2. 若在类中未使用 extends 关键字指明其父类，则默认其父类为 java.lang.Object类

3. Object类中的功能具有通用性

   > 无属性
   >
   > 只声明了一个空参构造器
   >
   > 方法：`equals()`  `toString()`  `getClass()`  `hashCode()`  `Clone()`  `finalize()`  `wait()`  `notify()`  `notifyAll()`



* 关于方法 `finalize()` 的一些说明：

  在垃圾回收机制回收任何对象之前，总会先调用它的 `finalize()`  方法。不要主动调用该方法，让垃圾回收机制调用。

  

## 补充例题

* 一些相关面试题：

  > * `final`  `finally`  `finalize`  的区别？
  >
  > * `==`  和 `equals()`  的区别？
  >
  >   > `==`  属于运算符
  >   >
  >   > 可以使用在基本数据类型变量和引用数据类型变量中
  >   >
  >   > > 基本数据类型变量，比较数据是否相等但类型可以不相同
  >   > >
  >   > > ```java
  >   > > int i = 10;
  >   > > double j = 10.0;
  >   > > char c = 10;
  >   > > System.out.println(i == j); //true
  >   > > System.out.println(i == c); //true
  >   > > 
  >   > > ```
  >   > >
  >   > > 引用数据类型变量，比较两个对象的地址值是否相同
  >   > >
  >   > > ```java
  >   > > Customer c1 = new Customer(123);
  >   > > Customer c2 = new Customer(123);
  >   > > System.out.println(c1 == c2); //false
  >   > > 
  >   > > String s1 = new String("hello");
  >   > > String s2 = new String("hello");
  >   > > System.out.println(s1 == s2); //false
  >   > > 
  >   > > ```
  >
  >   > `equals()`  属于方法
  >   >
  >   > 只适用于引用数据类型
  >   >
  >   > Object类中 `equals()`  的定义：(和  `==`  的作用相同)
  >   >
  >   > ```java 
  >   > public boolean equals(Object obj){
  >   >  return (this == obj);
  >   > }
  >   > ```
  >   >
  >   > 特别的，String, Date, File, 包装类等都重写了 Object类中的 `equals()` 方法，重写后变为比较两个对象的内容是否相同。
  >   >
  >   > 通常情况下，都需要对 `equals()` 进行重写（可以自动生成）来比较内容是否相同。
  >   >
  >   > 自己随意diy一个 `equals()` 试一下！！
  >   >
  >   > ```java
  >   > public boolean equals(Object obj) {
  >   > 		if(this == obj) {
  >   > 			return true;
  >   > 		}
  >   > 		if(obj instanceof Circle) {
  >   > 			Circle c = (Circle)obj;
  >   > 			return this.radius == c.radius;
  >   > 		}
  >   > 		return false;
  >   > 	}
  >   > ```
  >   >
  >   > 

## `toString()` 的使用

1. 当输出一个对象的引用时，实际上就是调用当前对象的 `toString()` 方法。

   ```java
   Customer cust = new Customer("Tom",21);
   System.out.println(cust.toString()); //结果为cust的地址值
   System.out.prinfln(cust); //输出对象的引用，结果为地址值2. `toString()` 
   ```

2.  `String()`, `Date()`, `File()`, 包装类等都重写了Object类中的 `toString()` 方法，使得在调用 `toString()` 方法时返回实体内容的信息。
3. 可以根据需要自动生成 `toString()` 代码
