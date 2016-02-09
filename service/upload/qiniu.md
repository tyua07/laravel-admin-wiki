3.1.3 七牛上传组件
===

#### 说明
--------------------
由于第三方存储服务的差异化，本节说明七牛上传组件特性

###### 重命名文件

```
$this->upload->rename('aa1.txt'， 'aa.txt');
```

###### 复制文件

```
$this->upload->copy('aa1.txt'， 'aa.txt');
```

###### 移动文件到指定空间

```
$this->upload->move('aa1.txt'， 'new_bucket_name', 'aa.txt');
```

###### 改变文件 Mime类型

```
$this->upload->changeMime('aa1.txt'， 'text/html');
```

###### 从指定URL抓取资源，并将该资源存储到指定空间中

```
$this->upload->fetch('http://www.baidu.com/index.html'， 'baidu.html');
```



