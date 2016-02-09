3.2.7.7 构建 image 选择框
===

#### 由于所有的图片都是先上传后搜索，所以这里的 image组件只是一个选择图片的组件
-------------------

例如：

```
builderFormSchema('brand_logo', '品牌logo', $type = 'image', $default = $data-> brand_logo_name,  $notice = '', $class = '', $rule = '*', $err_message = '', $option = BrandInfoModel::getImageDialogOption())->
```

$name|$title|$type|$default|$notice|$class|$rule|$err_message|$option
------|------|----|--------|------|--------|----|------------|-------
表单名称|标题|类型|图片真实路径|表单提示|表单class|表单验证规则|表单验证提示文字|选项

```
   $option 是一个数组

   /**
     * 获得品牌图片弹出框 图片属性
     *
     * @return array
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public static function getImageDialogOption()
    {
        return ['source' => 1, 'image_type' => 1];
    }

   $data->brand_logo_name 为组合过的路径
   $data->brand_logo_name   = Image::getImageRealPath($data->brand_logo, self::IMAGE_SOURCE, self::IMAGE_TYPE);
```

