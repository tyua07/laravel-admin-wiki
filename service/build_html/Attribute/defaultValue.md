设置表单元素默认值
===

-------------------

例如：

```
builderFormSchema('text', '是否显示【1:未确认；2：已确认】', $type = 'ckeditor', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildFormDefaultValue('这里是一个默认值')->
```

> Notice: 支持的表单元素有:label,text,textarea,ckeditor,ueditor

$default_value|$form_schema_name
------|------
表单默认值|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` created_at ``` 设置默认值 )(选填)

#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/admindefaultValue.png)
