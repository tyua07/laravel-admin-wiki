4.1 Excel 扩展
===

###### 开始

* 自动注入 上传组件

```
use App\Library\Excel;
```
* 使用

```
    /**
     * 导出优惠券excel表格
     *
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function getExport(Request $request, Excel $excle)
    {
        $title          = 'title';
        $file_name      = 'file';
        $data           = CouponModel::where('coupon_type_id', '=', $request->get('coupon_type_id'))->get();
        $head           = ['id', '优惠券类型', '券码', '用户', '订单id', '使用时间', '状态', '创建时间'];

        //导出excle
        $excle->export($file_name, $data, $head, $title);
    }
```

###### 参数说明

$file_name|$data|$head|$title
-----------|----|-----|------
文件名称|数据|头|标题






