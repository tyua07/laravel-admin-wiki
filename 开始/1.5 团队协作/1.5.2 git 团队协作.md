1.5.2 git 团队协作
===

#### 约定
---------------------

* 以代码为主的项目,项目主负责人在项目初始化时,确保中心仓库有两个远程分支:master && dev,master为稳定分支,dev为master开发分支.
* 建议项目负责人在项目setting设置dev为默认分支.
* 尽可能的在自己的本地上面开发新功能.
* dev分支功能开发分支,是可供运行和测试的hot code分支,请确保每个人合并到dev分支的功能可以运行和测试.
* master 分支为稳定主线分支,在master扥之打tag的静态版本来上线或者回滚.
* 专人负责将dev merge 到master分支,然后打tag上线.
* 除非有必要,不建议讲本地分支推送到远端.
* 合并代码的基本原则,先人后己.

#### 开发排期比较长(预定2天以上为长开发周期)
---------------------

* 参与项目,从中心仓库拉取代码 

```
$ git clone 或者项目的gitlab路径 
 
```

* 创建本地开发分支,已 feature 为例,具体的开发分支尽量取有意义的英文名称(多个单词用下下划线分隔)

```

$ git checkout master       # 从master 分支创建最新开发分支,限定当前开发分支不依赖其他任何分支代码.
$ git pull origin master    # 容错操作.
$ git branch feature        # 创建本地开发分支.
$ git checkout feature      # 切换到本地开发分支.
$ git push origin feature   # 多人参与一个开发分支,所以需要将此分支推送到远端.

仅参与开发的同学,在执行完第一步后,执行以下命令:

$ git fetch --all
$ git checkout feature

```
* 在本地分支开发新功能
* 将新功能代码提交到本地分支中

```
    git add .
    git commit -m '提交本地(提交规范请参考1.5.3章节)'
    
```
* 将新功能代码推送到远端

```

$ git push origin feature

```
* 发起提测邮件进入测试流程,如果有问题请重复2-5 步;如果测试确认没有问题,发起上线.以邮件的形式通知相关人员.
* 项目负责人做 code review ,并将feature merge到master,完成上线

```
$ git checkout master
$ git pull origin master    # master 上有可能存在 hotfixes 代码
$ git merge feature
$ git push origin master
打 tag ,推送tag到远端,执行上线.

```
* 完成上线后将新上线的功能 merge 到 dev 分支,并通知 dev 分支开发的同学拉取最新代码

```

$ git checkout dev
$ git pull origin dev   #拉取远端最新代码
$ git merge master      # 将 feature 功能推送到 dev 远端

```

* 为防止以后误操作,做好善后

```
$ git push origin :feature      # 删除已经完成上线的远端分支
$ git branch -D feature         # 删除本地分支

```

#### dev 分支多人开发

适合短平快的开发模式,开发周期在2天以内

* 参与项目,从中心仓库拉取代码

```
$ git clone 或者项目的gitlab路径 
 
```

* 创建本地开发分支,已 feature 为例,具体的开发分支尽量取有意义的英文名称(多个单词用下下划线分隔)

```

$ git branch feature        # 创建本地开发分支.
$ git checkout feature      # 切换到本地开发分支.

```
* 在本地分支开发新功能
* 将新功能代码提交到本地分支中

```
    git add ./
    git commit -m '提交本地(提交规范请参考1.5.3章节)'
    
```

* 切换到 dev 分支,并更新 dev 将他人的成果 merge 到本地分支,确保代码与中心库一致.

```

$ git checkout dev
$ git pull origin dev
$ git checkout feature
$ git merge dev
merge 如果有冲突,请解决冲突后,再执行第四步,如果没有冲突,可以将新功能代码 merge dev 分支.
$ git checkout dev 
$ git merge feature

```
* 将新功能推送到远端

```

git push origin dev

```

* 发起提测邮件进入测试流程,如果有问题请重复2-5 步;如果测试确认没有问题,发起上线.以邮件的形式通知相关人员.
* 项目负责人做 code review ,并将feature merge到master,完成上线

```
$ git checkout master
$ git pull origin master    # master 上有可能存在 hotfixes 代码
$ git merge feature
$ git push origin master
打 tag ,推送tag到远端,执行上线.

```

#### hotfixes

难免上线出现紧急问题,紧急修复流程如下:

* 拉取最新线上代码,并且创建紧急修复分支

```

$ git checkout master
$ git pull origin master
$ git branch hotfixes
$ git checkout hotfixes

```

* 完成修复并且提交代码

```
$ git add 修复的代码文件
$ git commit # 提交到本地
$ git checkout master
$ git master hotfixes
$ git push origin master

```

* 在线上线预览回归
* 完成上线后的善后

```
$ git checkout master
$ git pull origin master
$ git checkout dev
$ git pull origin dev
$ git merge master # hotfixes 的代码 merge 到 dev 分支
$ git branch -D hotfixes # 删除临时分支,防止以后误操作

```