3.2.7.12 构建双向选择器
===

#### 构建双向选择器
-------------------

例如：

```
builderFormSchema('access', '权限设置', 'multiSelect')->
buildFormMultiSelectDataSource(UserInfo1Model::select('id', 'created_at')->multiwhere(['status' => 2, 'id' => ['!=', $data->id] ])->get(), UserInfo1Model::multiwhere(['id' => $data->id])->get(), 'created_at')->            
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema
------|------|----|--------|------|--------|----|------------|-------|------------
表单名称|标题|类型|默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值


#### 效果图
----------------------------------

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/admin%2FmultiSelect.png)

