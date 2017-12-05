#git Notes
---
#### 1.安装

[官网下载安装](https://git-scm.com/downloads)
#### 2.设置用户名与邮箱
在Git Bush中输入命令修改用户名与邮箱
```
$ git config --global user.name "用户名"
$ git config --global user.email "邮箱"
```
#### 3.创建版本库
到你所选择的目录下创建一个空目录
```
$ mkdir 目录名
$ cd 目录名
```
初始化该目录为Git管理的仓库
```
$ git init
Initialized empty Git repository in F:/Repository/Diantask/.git/
```
#### 4.将文件添加到版本库
**1.将文件放到仓库目录下**
**2.将文件添加到暂存区**
```
$ git add 文件名
```
此时文件有三种状态
+ Untracked files:文件未被暂存
+ Changes to be committed:文件已被暂存
+ Changes bu not updated:已暂存过，但文件被修改还未暂存

**3.将文件提交到仓库**
```
$ git commit:提交暂存区里的内容
$ git commit -a:提交暂存区里的内容与Changes bu not updated的文件
```
**4.编辑更新描述**
在执行完上述命令后，会进入编辑器编辑描述内容，默认进入nano编辑器，如需修改默认编辑器，使用下述命令
```
$ git config --global core.editor 编辑器名称
```
也可以通过如下命令简化该过程
```
$git commit -m "描述内容"
```
**5.修改提交内容**
修改最后一次提交内容
```
$ git commit --amend
```
修改历史提交
```
$ git rebase -i 提交:将相应的提交当作最后一次提交
将pick修改为edit保存并退出
$ git commit --amend:修改提交内容
$ git rebase --continue:将提交顺序恢复
```
**6.查看仓库状态**
查看状态
```
$ git status
```
查看详细修改信息
```
$ git diff 文件名
```
**7.退回到历史版本**
查看提交历史(查询commit ID)
```
$ git log
```
查看命令历史(查询commit ID)
```
git reflog
```
回到历史版本
```
git reset --hard 版本/commit ID
```
```
HEAD^:上一个版本
HEAD^^:上上一个版本
```












