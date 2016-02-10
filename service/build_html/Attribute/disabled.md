设置表单元素禁用
===

#### 有的时候,我们展现的数据不需要修改,也不需要提交,则可以使用该方法,禁用当前表单
-------------------

例如：

```
builderFormSchema('created_at', '创建时间', $type = 'text', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildFormDisabled()->
```

> Notice: 除了基本的表单类型之外,多选框表单没有效果

$form_schema_name|$type
------|------
需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` created_at ``` 设置禁用 )|是否设置禁用(true:是;false:否),默认为true(选填)

#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/admindisabled.png)
