1.5.1 git 基本使用
===

#### 开始
---------------------


1. 创建ssh-key 
---------------------

```
ssh-keygen -t rsa -C '这里填写备注'

```


2. 初始化版本库
---------------------

```
git init 

```

3. 新增.gitignore 文件，忽略列表
---------------------

```
vim .gitignore


//然后写入你要忽略的文件

.env
/storage/framwork/*
.idea/* 

```

4. 添加文件到暂存区
---------------------

```
git add ./ //添加所有文件（递归）到暂存区
git add ./file.txt // 添加 file.txt 到暂存区

```


5. 把暂存区内容提交到当前分支
---------------------

```
git commit -m  '这里填写你当次提交说明'
git commit -m  -a //这样可以不必要写 **提交说明** 但是不推荐使用

```

6. 添加远程仓库
---------------------

```
git remote add origin xxx //origin：表示当前远程仓库名称； xxx:表示提交地址

```


7. 提交远程仓库
---------------------

```
git push origin master // origin：表示远程仓库名称；master:表示分支

```

8.拉取远程仓库代码到本地
---------------------

```
git pull origin master // origin：表示远程仓库名称；master:表示分支

```


