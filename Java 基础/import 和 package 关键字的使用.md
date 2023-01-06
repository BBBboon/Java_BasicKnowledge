# import 和 package 关键字的使用

## `package`关键字的使用

1. 在源文件首行
2. 属于标识符规范 `xxxyyyzzz`
3. 每 `.` 一次代表一层文件目录

## `import`关键字的使用

1. 导入指定包下的类、接口（本包下的可以直接用）
2. 若使用了不同包下的同名的类，则至少有一个类以全类名显示

```java
import java.util.ArrayList;
import java.util.Arrays;
//有多个同一包下的方法可以这样表示：
import java.util.*;

import com.atguigu.exer4.Account;
Account acct = new Account(1000);
//由于和上面类名一样，需要全类名
com.atguigu.exer3.Account acct1 = new com.atguigu.exer3.Account(1,2,3); 
```

