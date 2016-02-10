设置双向选择器数据源
===

#### 设置数据源,当然我们也可以按照普通构建表单的方式,用参数的形式设置数据源,这里我们还提供单独设置数据源的方式
-------------------

例如：

```
builderFormSchema('access', '权限设置', 'multiSelect')->
buildFormMultiSelectDataSource(UserInfo1Model::select('id', 'created_at')->multiwhere(['status' => 2, 'id' => ['!=', $data->id] ])->get(), UserInfo1Model::multiwhere(['id' => $data->id])->get(), 'created_at')->            
```

$option|$option_value_schema|$option_value_name|$form_schema_name
------|-------|------
未选择数据|已选择数据|数据对应的键值|需要设置的表单名称(如果没有填写该参数,则默认为上一个,例如例子中的代码,则是给 ``` access ``` 设置数据源 )(选填)


#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/admin%2FmultiSelect.png)
