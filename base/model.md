2.3 模型
===

1. 概览
--------------------------- 

本规范由编程原则组成，融合并提炼了开发人员长时间积累下来的成熟经验，意在帮助形成良好一致的编程风格。以达到事半功倍的效果，如果有需要本文档会不定期更新

1.1 查询语言 
--------------------------- 

* ** "普通查询" ** 查询

```
self::multiwhere( ['status' => 1 ] )

```

* ** "in" ** 查询

```
self::multiwhere( ['in' => [1, 2, 3] ] )

```

* ** "between" ** 查询

```
self::multiwhere( ['between' => [1, 5] ] )

```


