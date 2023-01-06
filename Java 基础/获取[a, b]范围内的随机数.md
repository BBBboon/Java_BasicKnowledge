# 获取[a, b]范围内的随机数

## 代码：

```java
(int)(Math.random() * (b-a+1) + a);
```

## 推导：

生成两位数的随机数

```java
Math.random(); //[0.0, 1]
Math.random()*90: //[0.0, 90.0]
(int)(Math.random()*90) //[0.0, 89]
(int)(Math.random()*90 + 10) //[0.0, 99]
//通过上面的推导得出规律
```
