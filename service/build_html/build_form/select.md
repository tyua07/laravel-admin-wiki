
3.2.7.11 构建 select 下拉列表框
===

#### 下拉列表框也是一种比较常见的表单元素
-------------------

例如：

```
builderFormSchema('time_type', '有效期类型', 'select', $default = '',  $notice = '', $class = '', $rule = '*', $err_message = '', CouponTypeModel::getTimeType(), 0,'name')->
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema|$option_value_name
------|------|----|--------|------|--------|----|------------|-------|------------
表单名称|标题|类型|默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值|选项名称

####### $option 选项


例如：

```
$option = [
['id' => 1, 'name' => trans('response.is_new_1')],
['id' => 2, 'name' => trans('response.is_new_2')],
['id' => 3, 'name' => trans('response.is_new_3')],
]

$option 是一个多维数组。$option_value_schema的值是1，则表示，表单默认值是 trans('response.is_new_1') 
```


#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/adminselect.png)