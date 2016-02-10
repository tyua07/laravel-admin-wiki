1.1 介绍
===

## 开始

* [wiki](http://wiki.laravel-administrotar.com/)
* [安装教程](http://blog.womenshuo.com/?p=162)
* [视频地址（字幕版）](http://pan.baidu.com/s/1i41oUTR)，视频是在docker环境下面操作的，如果不会docker，可以自己用自己的本地环境即可。
* [LNMP Dockerfile地址](https://github.com/tyua07/centsos_7_lnmp)

## 环境依赖

* php = 5.6
* mysql
* redis

## 计划

- [ ] 更新文档
- [ ] 重写js端
- [ ] 自动生成代码（快完成了,完善界面和交互有一个UserInfo1的例子）
- [ ] 自动布局（已经在生产环境上面使用，等稳定了再合并。）
- [ ] 写单元测试
- [ ] 计划在2月份发布第一个版本，如果单元测试没有写完或者单元测试没有测试完毕，则会跳票，希望理解。

## 快速构建CURD页面

### 开始

* 注入 控制器 ``` use App\Http\Controllers\Admin\HtmlBuilderController; ``` 

```

    protected $html_builder;

    /**
     * 构造方法
     *
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public  function __construct(HtmlBuilderController $html_builder)
    {
        parent::__construct();
        $this->html_builder = $html_builder;
    }
    
```

### 构建 列表页面

###### 显示列表页代码

```

    /**
     * 获得后台用户
     *
     * @return Response
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getIndex(Request $request)
    {
        return  $this->html_builder->
                builderTitle('后台用户列表')->
                builderSchema('id', 'id')->
                builderSchema('admin_name', '管理员名称')->
                builderSchema('limit_name','角色名称')->
                builderSchema('mobile', '手机号码')->
                builderSchema('state_name', '状态')->
                builderSchema('last_login', '最后一次登陆时间')->
                builderSchema('create_date', '创建时间')->
                builderSchema('handle', '操作')->
                builderSearchSchema('admin_name', '管理员名称')->
                builderBotton('增加后台用户', createUrl('Admin\Admin\AdminInfoController@getAdd'))->
                builderJsonDataUrl(createUrl('Admin\Admin\AdminInfoController@getSearch',[ 'limit_id' => $request->id ]))->
                builderList();
    }
    
```

###### 获取列表页数据代码

```
    /**
     * 搜索
     *
     * @param Request $request
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getSearch(Request $request)
    {
        //接受参数
        $search     = $request->get('search', '');
        $sort       = $request->get('sort', 'id');
        $order      = $request->get('order', 'asc');
        $limit      = $request->get('limit',0);
        $offset     = $request->get('offset', config('config.page_limit'));
        $limit_id   = $request->limit_id;

        //admin_info 表名
        $admin_info_table_name = tableName('admin_info');

        //解析params
        parse_str($search);

        //组合查询条件
        $map = [];

        if (!empty($limit_id)) {
            $map[$admin_info_table_name . '.limit_id'] = $limit_id;
        }
        if (!empty($admin_name)) {
            $map[$admin_info_table_name . '.admin_name'] = ['like','%'.$admin_name.'%'];
        }

        $data = AdminInfoModel::search($map, $sort, $order, $limit, $offset);

        echo json_encode([
            'total' => $data['count'],
            'rows'  => $data['data'],
        ]);
    }

```

###### 效果图

![列表页](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2056%20-%20%E5%90%8E%E5%8F%B0%E7%94%A8%E6%88%B7%E5%88%97%E8%A1%A8%20-%20http___www.laravel-admin.com_admin_admin_info.png)

### 构建 编辑 or 添加 页面

###### 代码

```
    /**
     * 编辑角色
     *
     * @param  int  $id
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getEdit(Request $request)
    {
        $infos = AdminInfoModel::find($request->get('id'));

        return  $this->html_builder->
                builderTitle('编辑后台用户')->
                builderFormSchema('admin_name', '管理员名称', $type = 'text')->
                builderFormSchema('password', '登录密码', $type = 'password', '', '', '', '')->
                builderFormSchema('password_confirmation', '确认密码', $type = 'password', '', '', '', '')->
                builderFormSchema('limit_id', '角色', $type = 'select', $default = '', $notice = '', $class = '', $rule = '*', $err_message = '', AdminInfoModel::adminInfoLimitName(), '', 'name')->
                builderFormSchema('mobile', '手机', $type = 'text', $default = '',  $notice = '', $class = '', $rule = '', $err_message = '', $option = '', $option_value_schema = '')->
                builderFormSchema('state', '状态', 'radio', '', '', '', '', '', [1=>'开启', '2'=>'关闭'] ,$infos->state)->
                builderConfirmBotton('确认', createUrl('Admin\Admin\AdminInfoController@postEdit'), 'btn btn-success')->
                builderEditData($infos)->
                builderEdit();
    }

```

###### 处理编辑代码

```
    /**
     * 处理更新角色
     *
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function postEdit(AdminInfoRequest $request)
    {

        $data   = $request->except('password_confirmation');

        $Model  = AdminInfoModel::findOrFail($data['id']);

        if (empty($data['password'])) {
            $data['password'] =$Model->password;
        }else{
            $data['password'] = bcrypt($data['password']);
        }

        $Model->update($data);
        //更新成功
        return $this->response(self::SUCCESS_STATE_CODE, trans('response.update_success'), [], true, createUrl('Admin\Admin\AdminInfoController@getIndex'));
    }

```

###### 效果图

![编辑或者添加页面](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2057%20-%20%E7%BC%96%E8%BE%91%E5%90%8E%E5%8F%B0%E7%94%A8%E6%88%B7%20-%20http___www.laravel-admin.com_admin_admin_info_edit_id=1.png)

###### 构建 tree 页面

###### 代码

```
 /**
     * 获得后台菜单
     *
     * @return Response
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getIndex()
    {
        return  $this->html_builder->
                builderTitle('后台菜单列表')->
                builderSchema('id', 'id')->
                builderSchema('menu_name', '菜单名称')->
                builderSchema('parent_name','父级菜单名称')->
                builderSchema('handle', '操作')->
                builderBotton('增加后台菜单', createUrl('Admin\Admin\AdminMenuController@getAdd'))->
                builderTreeData(AdminMenuModel::getAll())->
                builderTree();
    }

```

###### 效果图

![tree页面](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2058%20-%20%E5%90%8E%E5%8F%B0%E8%8F%9C%E5%8D%95%E5%88%97%E8%A1%A8%20-%20http___www.laravel-admin.com_admin_admin_menu.png)


### 构建 tab 页面

###### 代码

```
 /**
     * 编辑商品信息
     *
     * @param  Request  $request
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getEdit(Request $request)
    {
        $goods_info = GoodsModel::getGoodsInfo($request->get('id'));

        return  $this->html_builder->builderTabTitle(trans('goods.goods_title14'))
                ->builderTabSchema(
                    $this->html_builder->
                    builderTitle(trans('goods.goods_title15'))->
                    builderFormSchema('goods_name', trans('goods.goods_title4'))->
                    builderFormSchema('id', 'id', 'hidden')->
                    builderConfirmBotton(trans('base.comfirm_add_data'), '', 'btn btn-success')->
                    builderEditData($goods_info)
                )->builderTabSchema(
                    $this->html_builder->
                    builderTitle(trans('goods.goods_title32'))->
                    builderFormSchema('meta_title', trans('goods.goods_title33'))->
                    builderFormSchema('meta_keywords', trans('goods.goods_title34'), 'textarea')->
                    builderFormSchema('meta_description', trans('goods.goods_title35'), 'textarea')->
                    builderConfirmBotton(trans('base.comfirm_add_data'), '', 'btn btn-success')->
                    builderEditData($goods_info)
                )->builderBotton(trans('base.return'), createUrl('Admin\Goods\GoodsController@getIndex'), 'glyphicon glyphicon-arrow-left')
            

```

###### 效果图

![tab 页面](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2059%20-%20%E6%B7%BB%E5%8A%A0%E5%95%86%E5%93%81%20-%20http___admin.zaiseoul.com_admin_goods_goods_add_meitu_1.jpg)

## 生成 CURD 代码

> 注意：因为还没有完善好前端页面和js交互，所以只放出一张预览图，最终效果就是生成项目里面 UserInfo1这个模块

###### 效果图

![效果图](http://7xojjf.com1.z0.glb.clouddn.com/FireShot%20Capture%2060%20-%20%E6%9E%84%E5%BB%BA%E4%BB%A3%E7%A0%81%20-%20http___www.laravel-admin.com_auto-build_home.png)

## 自动布局简要介绍

###### 自动布局之前

![](http://7xojjf.com1.z0.glb.clouddn.com/autolayout%E5%89%8D_meitu_1.jpg)

###### 自动布局之后

![](http://7xojjf.com1.z0.glb.clouddn.com/autolayout%E4%B9%8B%E5%90%8E_meitu_2.jpg)

> 还有一些细节没有完善好，所以没有放出来。

## 注意

* 代码在继续完善中，已经用于生产环境使用，很多细节待完善，文档也会慢慢更新的！
* 需要下载一份sql执行到你的本地，然后使用这份sql的数据,sql地址保存在"资料文件"--> laravel.sql
* email:yangyifanphp@gmail.com
* 账户:yangyifan,密码：qiqi..
* [线上测试地址](http://test.admin.womenshuo.com/)

## 教程
* [用laravel自己创建一个属于自己的后台（一）之 构建后台登陆模块](http://blog.womenshuo.com/?p=137)
* [用laravel自己创建一个属于自己的后台（二）之 构建权限角色模块](http://blog.womenshuo.com/?p=141)
* [用laravel自己创建一个属于自己的后台（三）之 压缩网站静态文件](http://blog.womenshuo.com/?p=153)

## License

MIT 
