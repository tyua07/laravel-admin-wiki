构建request
===

## 支持的验证规则

```

"accepted"          => "请确认接受服务条款",
"active_url"        => "url格式不正确",
"after"             => ["after:%s", "当前时间不能小于%s"],
"before"            => ["before:%s", "当前时间不能大于%s"],
"alpha"             => "必须全部是数字",
"alpha_dash"        => "字母、数字、破折号（-）以及底线（_）",
"alpha_num"         => "必须是字母、数字",
"array"             => "必须是数组",
"between"           => ["between:%d,%d", "必须在%d-%d之间"],
"confirmed"         => ["confirmed_%s", "重复的%s不正确"],
"date"              => "时间格式不正确",
"date_format"       => ["date_format:%s" , "时间格式不正确"],
"different"         => ["different:%s", "不能和%s相同"],
"digits"            => ["digits:%d", "字段必须是数字,并且长度为%d"],
"digits_between"    => ["digits_between:%d,%d", "字段必须是数并，且长度在%d-%d之间"],
"boolean"           => "必须是boolean值",
"email"             => "邮箱格式不正确",
"exists"            => ["exists:%s,%s", "%s不能重复"],
"image"             => "必须是图片",
"in"                => ["in:%s", "必须为%s清单的其中一个值"],
"integer"           => "必须为整数",
"ip"                => "当前ip格式不正确",
"max"               => ["max:%d", "必须大于%d"],
"mimes"             => ["mimes:%s", "文件的Mime类型必须要为%s清单的其中一个值"],
"min"               => ["min:%d", "必须小于%d"],
"not_in"            => ["not_in:%s", "不能在%s其中"],
"numeric"           => "必须是数字",
"regex"             => ["regex:%s", "格式不正确"],
"required"          => ["required:%s", "%s不能为空"],
"url"               => "url格式不正确",

                
```

> Notice : 如果当前数组对应的value是数组,则表示需要有参数填写.例如 "required" 这个验证规则,就需要指明 "xx不能为空"