设置时间类型表单的时间格式
===

-------------------

例如：

```
builderFormSchema('created_at', '创建时间', $type = 'date', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildFormDefaultValue("dateFmt:'yyyy-MM-dd'")->
```

$date_format|$form_schema_name
------|------
时间格式|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` created_at ``` 设置时间格式 )(选填)
