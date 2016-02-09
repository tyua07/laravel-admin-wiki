3.2.7.6 构建 date 时间组件
===

#### 一些时间的表单，需要用时间组件
-------------------

例如：

```
builderFormSchema('create_date', '开始时间', 'date', $default= "dateFmt:'yyyy-MM-dd HH:mm:ss'")->
```

$name|$title|$type|$default
------|------|----|--------
表单名称|标题|类型|默认时间格式（默认是“年-月-日 小时：分钟：秒”）


##### 注：详细参数请看[文档链接](http://www.my97.net/dp/demo/index.htm)

