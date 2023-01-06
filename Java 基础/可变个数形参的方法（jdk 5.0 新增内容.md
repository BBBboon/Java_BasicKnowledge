# 可变个数形参的方法（jdk 5.0 新增内容

1. 格式：数据类型 ... 变量名
2. 调用可变个数形参方法时，传入的参数个数可以是 0个，1个，2个...
3. 可变个数形参方法与本类中方法名相同，**形参不同**的方法之间构成重载。
4. 可变个数形参方法与本类中方法名相同，**形参类型也相同的数组**之间不能构成重载。（不能共存）
5. 可变个数在方法的形参中必须只声明在末尾，而且最多只能声明一个可变形参。

```java
public class MethodArgsTest{
    public static void main(String[] args){
        MethodArgsTest test = new MethodArgsTest();
        test.show("hello");
        test.show("hello", "world");
    }
    
    //下面两个方法构成重载
    public void show(String s){
        System.out.println("show(String)");
    }
    public void show(String ... strs){
        System.out.println("show(String ... strs)");
    }
    
    //这个方法和上面的方法不能构成重载，不能共存。
    public void show(String[] strs){}
    
    //报错，应该把可变类型形参放在最后
    public void show(String ... strs, int i){}
}
```



