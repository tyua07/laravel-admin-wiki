3.2.4 构建tree页面
===

##### 构建tree页面

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
 
2. 展现tree页
----------------------------------

```
        /**
	 * 获得菜单列表
	 *
	 * @return Response
     * @author yangyifan <yangyifanphp@gmail.com>
	 */
	public function getIndex(){
        return  $this->html_builder->
                builderTitle('文章分类')->
                builderSchema('id', 'id')->
                builderSchema('menu_name', '菜单名称')->
                builderSchema('pid_name','父级栏目')->
                builderSchema('status', '状态')->
                builderSchema('sort', '排序')->
                builderSchema('created_at', '创建时间')->
                builderSchema('updated_at', '更新时间')->
                builderSchema('handle', '操作')->
                builderAddBotton('增加菜单分类', url('admin/menu/add'))->
                builderTreeData(MenuModel::getAll())->
                builderTree();
	}
```

##### 连贯操作说明
----------------------------------

方法名|说明
-----|---
builderTitle|构建当前页面标题
builderSchema|构建当前页面列表字段
builderSearchSchema|构建当前页面搜索字段
builderAddBotton|构建当前页面按钮
builderTreeData|构建数据源
builderTree|展现页面

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


