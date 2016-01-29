3.2.7.9 构建 radio 单选框
===

#### 单选框也是一种比较常见的表单元素
-------------------

例如：

```
builderFormSchema('is_new', '是否新老用户可用', 'radio', '', '', '', '', '', [1=> trans('response.is_new_1'), '2'=>trans('response.is_new_2'), '3'=>trans('response.is_new_3') ], '3')->
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema
------|------|----|--------|------|--------|----|------------|-------|------------
表单名称|标题|类型|默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值

####### $option 选项

####### $option 是一个数组 key => value,$option_value_schema 对应 $option 的key。

例如：

```
$option = [1=> trans('response.is_new_1'), '2'=>trans('response.is_new_2'), '3'=>trans('response.is_new_3') ]

$option 是一个多维数组。$option_value_schema的值是3，则表示，表单默认值是3
```




