# Java 面向对象

1. Java 类及类的成员：属性，方法，构造器；代码块，内部类。

2. 面向对象的三大特征：封装性，继承性，多态性。

3. 一些关键字：

   `this`, `super`, `static`, `final`, `abstract`, `interface`, `package`, `import`等

类class：一类实物的描述，抽象的、概念上的定义。

对象object：实际存在的事物个体，也称为实例（instance）。

类的成员：

> 属性 （成员变量）field
>
> 方法（函数）method

创建类的对象（类的实例化）：

```java
person p = new person();
```

例如：

```java
public class PersonTest{
    public static void main(String[] args){
        //创建Person类的对象
        Person p = new Person();
        //调用对象的结构：属性、方法
        //调用属性："对象.属性"
        p.name = "Tom";
        p.isMale = true;
        //调用方法："对象.方法"
        p.eat();
        p.talk("Chinese");
    }
}
class Person{
    //属性
    String name;
    int age = 1;
    boolean isMale;
    
    //方法
    public void eat(){
        System.out.println("人可以吃饭。")
    }
    public void talk(String language){
        System.out.println("人可以说话，使用的是"+language);
    }
}
```

### 面向过程与面向对象的区别：

> 面向过程：强调的是功能行为，以函数为最小单位。
>
> 面向对象：将功能封装进对象，强调了功能的对象，以类/对象为最小单位。

-----

### 对象的创建和使用

![image-20220702170649590](Java 面向对象基础.assets/image-20220702170649590.png)

### 属性（成员变量）和局部变量的不同点：

* 类中声明的位置不同

  属性：定义在一对{ }内

  局部变量：声明在*方法内、方法形参、代码块内、构造器形参、构造器内部变量*

* 关于权限修饰符不同

  属性：可以在声明属性时，指明其权限，使用权限修饰符。（常见的权限修饰符：`private`、`public`、缺省、`protected`）

  局部变量：不可以使用权限修饰符。

  ```java
  class User{
      //属性
      private String name;
      public int age;
      boolean isMale;
      
      public void talk(String language){
          int number;
          //language和number都是形参
      }
  }
  ```

* 默认初始化值：

  属性：都有默认初始化值。

  ​			整型（`byte`、`short`、`int`、`long`）：0

  ​			浮点型（`float`、`double`）：0.0

  ​			字符型（`char`）：0

  ​			布尔型（`boolean`）：false

  ​			引用数据类型（类、数组、接口）：null

  局部变量：没有默认初始化值。意味着，在调用局部变量前需要显式赋值。

* 在内存中加载位置：

  属性：加载到堆空间（非`static`）。

  局部变量：加载到栈空间。

* 在方法的使用中，可以调用当前类的属性和方法。方法中不可以定义方法。

**所有变量：**

> 成员变量：a.实例变量（不以`static` 修饰）
>
> ​					b.类变量（以`static`修饰）
>
> 局部变量：a.形参（方法、构造器中的变量）
>
> ​					b.方法局部变量（方法内定义）
>
> ​					c.代码块局部变量（代码块内定义）

