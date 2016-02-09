3.2.5 构建tab 页面
===

##### 构建tab 页面

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
 
2. 展现tab 页面
----------------------------------

```
        /**
	 * 网站配置
	 *
	 * @return Response
     * @author yangyifan <yangyifanphp@gmail.com>
	 */
	public function getIndex(){
          return $this->html_builder->builderTabSchema(
                    $this->html_builder->
                    builderTitle('基本设置')->
                    builderFormSchema('site_name', '网站名称')->
                    builderFormSchema('keywords', '关键字', $type = 'text', $default = '',  $notice = '', $class = '', $rule = 'e', $err_message = '', $option = '', $option_value_schema = '')->
                    builderFormSchema('description', '网站描述', $type = 'text', $default = '',  $notice = '', $class = '', $rule = 'e', $err_message = '', $option = '', $option_value_schema = '')->
                    builderConfirmBotton('确认', url('admin/config/edit'), 'btn btn-success')->
                    builderEditData(ConfigModel::getAll())
                )->builderTabHtml();
	}
```

##### 连贯操作说明
----------------------------------

方法名|说明
-----|---
builderTabSchema|构建选项卡
builderTitle|构建当前页面标题
builderFormSchema|构建表单字段
builderConfirmBotton|构建当前页面按钮
builderEditData|构建数据源
builderTabHtml|展现页面

##### builderFormSchema参数说明
----------------------------------

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option|$option_value_schema
-------|--------|------|------|-------|------|------|----|-------|----
表单name|表单名称|表单类型|表单默认值|表单提示|表单class|表单验证规则|表单验证提示文字|选项|选项值


3. 效果图
----------------------------------

![tab 页面](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2059%20-%20%E6%B7%BB%E5%8A%A0%E5%95%86%E5%93%81%20-%20http___admin.zaiseoul.com_admin_goods_goods_add_meitu_1.jpg)
