# this关键字

1. `this` 关键字可以用来修饰和调用：**属性、方法和构造器**。
2. `this` 可以理解为当前对象或者当前正在创建的对象。
3. 当方法或构造器的**形参**和类或构造器的**属性**同名时，我们必须显式地使用 `this.变量` 的方式来表明此变量是属性，而非形参。

```java
class Person{
    private String name;
    private int age;
    
    public Person(String name){
        this.name = name;
    }
}
```

4. `this`调用构造器
   * 在类的构造器中可以显式地使用 `this(形参列表)` 方式来调用本类中其他构造器。
   * 构造器中不能通过 `this` 调用自己。
   * `this` 必须声明在当前构造器首行。
   * 构造器内部只能声明一个 `this` 来调用其他构造器。

```java
class Person{
    private String name;
    private int age;
    
    public Person(){
        this.eat();
    }
    public Person(String name){
        this(); //这个this会调用上面构造器，执行eat()，再继续向下执行。
        this.name = name;
    }
}
```

