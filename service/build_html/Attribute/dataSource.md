设置(radio|select|checkbox)数据源
===

#### 设置数据源,当然我们也可以按照普通构建表单的方式,用参数的形式设置数据源,这里我们还提供单独设置数据源的方式
-------------------

例如：

```

#单选框
builderFormSchema('status1', '是否显示【1:未确认；2：已确认】', $type = 'radio', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildDataSource([1=>'开启', '2'=>'关闭'], 1)->

#多选框
builderFormSchema('status2', '是否显示【1:未确认；2：已确认】', $type = 'checkbox', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildDataSource([1=>'开启', '2'=>'关闭'], [1, 2])->

#下拉列表框
builderFormSchema('status3', '是否显示【1:未确认；2：已确认】', $type = 'select', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildDataSource([ [ 'id' => 1, 'name' => '开启'], ['id' => 2, 'name' => '关闭']], 1, 'name')->

```

$data_source|$select|$option_name|$form_schema_name
------|-------|------
数据源|需要选中的元素(选填)|选项名称(选填)|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` status ``` 设置数据源 )(选填)


