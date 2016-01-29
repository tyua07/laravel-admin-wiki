3.2.7.10 构建 checkbox 多选框
===

#### 多选框也是一种比较常见的表单元素
-------------------

例如：

```
builderFormSchema('platform[]', '设备', 'checkbox', '', '', '', '', '', ['ios' => 'ios', 'android' => 'android'], ['ios', 'android'])->
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema
------|------|----|--------|------|--------|----|------------|-------|------------
表单名称|标题|类型|默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值

####### $option 选项

####### $option 是一个数组 key => value,$option_value_schema 对应 $option 的key，也是一个数组。

例如：

```
$option = [1=> trans('response.is_new_1'), '2'=>trans('response.is_new_2'), '3'=>trans('response.is_new_3') ]

$option 是一个多维数组。$option_value_schema的值是['ios', 'android']，则表示，表单默认值是“ios” & “android” 都是选中状态
```



