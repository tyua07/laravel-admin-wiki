执行 构建curd操作
===

## 支持的验证规则

参数|说明
----|----
Request 文件名| Request 保存的的绝对路径
Request 文件标题|用于文件的注释信息
Model 文件名|Model 保存的的绝对路径
Model 文件标题|用于文件的注释信息
Controller 文件名|Controller 保存的的绝对路径
Controller 文件标题|用于文件的注释信息

## 注意

* 文件保存在 ``` stroage/build/output ``` 文件夹下面,需要自己手动拷贝文件到 ``` app ``` 目录下面,然后设置路由
* 如果控制器文件需要设置某些表单为 (radio|selece|checkbox|multiSelect)等类型表单,需要手动设置数据源信息
* js验证规则需要手动设置(后续会修改成在构建Controller配置文件时设置)
* 文档可能还不是很完善,请多多看看源码,谢谢!