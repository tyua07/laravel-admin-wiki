2.2 控制器
===

1. 概览
--------------------------- 

本规范由编程原则组成，融合并提炼了开发人员长时间积累下来的成熟经验，意在帮助形成良好一致的编程风格。以达到事半功倍的效果，如果有需要本文档会不定期更新

1.1 响应
--------------------------- 
* 遵循 [1.2 响应状态码](http://doc.oschina.net/laravel-admin?t=32958) 章节状态码
* 使用基础控制器 ** response ** 方法响应

例如：
```

@param $code     状态码
@param $msg      提示文字
@param $data     数据
@param $target   是否跳转到新页面 true 跳转 false 不跳转
@prams $href     跳转的网址      跳转的网址


$this->response($code = 200, $msg = '', $data = [], $target = true, $href = '');

```

