3.2.1 构建列表页
===

##### 构建数据列表页面

1. 自动注入 HtmlBuilderController 控制器
----------------------------------

```
    protected $html_builder;

    /**
     * 构造方法
     *
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function __construct(HtmlBuilderController $html_builder){
        $this->html_builder = $html_builder;
    }
```
 
2. 展现列表页
----------------------------------

```
    /**
     * 获得后台用户
     *
     * @return Response
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getIndex(){
        return  $this->html_builder->
                builderTitle('后台用户列表')->
                builderSchema('id', 'id')->
                builderSchema('email', '登录名')->
                builderSchema('mobile','手机号码')->
                builderSchema('status', '状态')->
                builderSchema('role_name', '角色')->
                builderSchema('created_at', '创建时间')->
                builderSchema('updated_at', '更新时间')->
                builderSchema('handle', '操作')->
                builderSearchSchema('email', '登录名')->
                builderSearchSchema('mobile', '手机号码')->
                builderSearchSchema($name = 'status', $title = '状态', $type = 'select', $class = '', $option = [1=>'开启', '2'=>'关闭'], $option_value_schema = '0')->
                builderSearchSchema('role_name', '角色')->
                builderBotton('增加后台用户', url('admin/admininfo/add'))->
                builderJsonDataUrl(url('admin/admininfo/search'))->
                builderList();
    }
```

##### 连贯操作说明
----------------------------------

方法名|说明
-----|---
builderTitle|构建当前页面标题
builderSchema|构建当前页面列表字段
builderSearchSchema|构建当前页面搜索字段
builderBotton|构建列表页面按钮
builderJsonDataUrl|构建数据源
builderList|展现页面

##### builderSchema 参数说明
----------------------------------

$schame|$comment|$type|$class|$url|$is_sort
-------|--------|------|------|----|------
字段名称|备注|字段类型|class名称|url|是否允许排序


##### builderSearchSchema参数说明
----------------------------------

$name|$title|$type|$class|$option|$option_value_schema
-------|--------|------|------|----|------
表单name|表单名称|表单类型|表单默认值|表单提示|表单class


3. 效果图
----------------------------------

![列表页](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2056%20-%20%E5%90%8E%E5%8F%B0%E7%94%A8%E6%88%B7%E5%88%97%E8%A1%A8%20-%20http___www.laravel-admin.com_admin_admin_info.png)

