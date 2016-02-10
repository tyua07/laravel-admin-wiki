设置表单元素js验证规则错误时提示文字
===

-------------------

例如：

```
builderFormSchema('created_at', '创建时间', $type = 'date', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildFormRule('e')->
buildFormErrorMessage("自定义错误条件")->
```

$error_message|$form_schema_name
------|------
表单js规则验证错误时显示的错误提示文字|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` created_at ``` 设置表单js规则验证错误时显示的错误提示文字 )(选填)

#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/adminerrorMessage.png)