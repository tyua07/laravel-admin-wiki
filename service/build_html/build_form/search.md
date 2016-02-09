3.2.7.13 构建搜索框
===

#### 由于有的时候数据太多，造成不能使用select表单来构建，所以这里就使用到了搜索框组件

-------------------

例如：

```
builderFormSchema('index_cat_id', '所属大栏目', 'search', $default = $info->index_cat_id_name,  $notice = '', $class = '', $rule = '*', $err_message = '', $option = IndexCatListModel::getSearchCatParams())->
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option
------|------|----|--------|------|--------|----|------------|-------
表单名称|标题|类型|用于显示的名称|表单提示|表单class|表单验证规则|表单验证提示文字|选项

```
   $option 是一个数组

    /**
     * 获得页面，搜索组件 option 参数 [搜索首页栏目]
     *
     * @return string
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public static function getSearchCatParams()
    {
        return json_encode(['url' => createUrl('这里是一个路由')]);
    }

   对应的控制器，也只是做搜索返回json数据就好了
   /**
     * 搜索APP首页栏目
     *
     * @param Request $request
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getSearchOnes(Request $request)
    {
        $name = trim($request->get('name'));
        //todo request

        $admin_list = IndexCatModel::multiwhere(['cat_name' => ['like', '%' . $name . '%'] ])->select('cat_name as name', 'id')->get();
        return !empty($admin_list) ? $this->response(self::SUCCESS_STATE_CODE, '', $admin_list) : $this->response(self::ERROR_STATE_CODE, trans('response.search_empty'));
    }

   比如我们 这个控制器显示要关联一个分类表，但是这个分类表可以有1k的数据，我们这个时候用select显然不合适，所以我们就构建了一个搜索框
   
   $data->index_cat_id_name   就是 上图文本框的内容;
```

#### 效果图
----------------------------------

![图片1](http://static.womenshuo.com/@/other/images/22222.png)