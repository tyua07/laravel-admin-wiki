4.2.1  开始
===

###### 开始

* 自动注入 推送组件

```
use App\Library\Jpush;
use JPush\Model as M;
```
* 使用

```
    /**
     * 处理推送
     *
     * @param Request $request
     * @author yangyifan <yangyifanphp@gmail.com>
     */
    public function postPush(Request $request)
    {
        $city_ids = $request->get('city_id');

        if(count($city_ids) == count(config('config.city_ids'))){
            $audience = 'all';
        }else{
            $audience = M\audience(M\alias($city_ids));
        }

        $status = Jpush::push($request->get('alert'), $request->get('type'), $request->get('platform'), $audience);

        return $status == true ? $this->response(200, trans('response.push_success'), [], false) : $this->response(400, trans('response.push_error'), [], false);
    }
```

###### 参数说明

$alert|$type|$platform|$city_id
-----------|----|-----|------
通知内容|消息类型|设备|城市id



