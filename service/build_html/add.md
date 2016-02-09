3.2.3 构建增加页面
===

##### 构建增加页面

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
 
2. 展现增加页
----------------------------------

```
    /**
     * 编辑角色
     *
     * @param  int  $id
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getAdd($id){
        return  $this->html_builder->
                builderTitle('编辑后台用户')->
                builderFormSchema('id', 'id', 'hidden')->
                builderFormSchema('email', '登录邮箱', $type = 'text', $default = '',  $notice = '', $class = '', $rule = 'e', $err_message = '', $option = '', $option_value_schema = '')->
                builderFormSchema('password', '登录密码', $type = 'password', $default = '',  $notice = '', $class = '', $rule = '')->
                builderFormSchema('mobile', '手机号码', $type = 'text', $default = '',  $notice = '', $class = '', $rule = 'm', $err_message = '', $option = '', $option_value_schema = '')->
                builderFormSchema('status', '状态', 'radio', '', '当前角色是否开启，如果关闭，则属于当前角色都不可用', '', '', '', [1=>'开启', '2'=>'关闭'], '2')->
                builderFormSchema('face', '头像', 'image')->
                builderFormSchema('role_id', '所属角色', 'select', $default = '',  $notice = '', $class = '', $rule = '*', $err_message = '', AdminRoleModel::getRoleList(), 'role_name')->
                builderMethod('get')->
                builderConfirmBotton('确认', url('admin/admininfo/edit'), 'btn btn-success')->
                builderAdd();
    }
```

##### 连贯操作说明
----------------------------------

方法名|说明
-----|---
builderTitle|构建当前页面标题
builderFormSchema|构建当前表单字段
builderSearchSchema|构建当前页面搜索字段
builderMethod|构建当前表单提交方式
builderConfirmBotton|构建当前页面按钮
builderAdd|展现页面

##### builderFormSchema参数说明
----------------------------------

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema
-------|--------|------|------|-------|------|------|----|-------|----
表单name|表单名称|表单类型|表单默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值


