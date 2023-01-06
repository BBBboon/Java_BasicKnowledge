# MVC设计模式

### 视图模型层 view （处理数据）

1. 相关工具类 `view.utils`
2. 自定义view `view.ui`

### 控制器层 controller （处理业务逻辑）

1. 抽取相应的基类 `controller.base`
2. 存放fragment `controller.fragment`
3. 显示列表的适配器 `controller.adapter`
4. 和服务相关 `controller.service`

### 数据模型层 model （显示数据）

1. 数据对象封装 `model.bean/domain`
2. 数据库操作类 `model.dao`
3. 数据库 `model.db`



**用户输入** ---> 控制器 ---> 模型 ( <---> 数据库)---> 视图 ---> **反馈给用户**

​                                      