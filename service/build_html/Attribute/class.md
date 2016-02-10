设置表单元素class
===

-------------------

例如：

```
builderFormSchema('created_at', '创建时间', $type = 'date', $default = '', $notice = '', $class = '', $rule = '', $err_message = '')->
buildFormClass('aa')->
```

$class|$form_schema_name
------|------
表单自定义class|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` created_at ``` 设置class )(选填)

#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/adminbuild_class.png)
