git Notes
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
+ 在执行完上述命令后，会进入编辑器编辑描述内容，默认进入nano编辑器，如需修改默认编辑器，使用下述命令
```
$ git config --global core.editor 编辑器名称
```
+ 也可以通过如下命令简化该过程
```
$ git commit -m "描述内容"
```

**5.修改提交内容**
+ 修改最后一次提交内容
```
$ git commit --amend
```
+ 修改历史提交
```
$ git rebase -i 提交:将相应的提交当作最后一次提交
将pick修改为edit保存并退出
$ git commit --amend:修改提交内容
$ git rebase --continue:将提交顺序恢复
```
+ 将远程仓库合并到当前分支
```
$ git pull
```

**6.查看仓库状态**
+ 查看状态
```
$ git status
```
+ 查看详细修改信息
```
$ git diff 文件名
```

**7.退回到历史版本**
+ 查看提交历史(查询commit ID)
```
$ git log
```
+ 查看命令历史(查询commit ID)
```
$ git reflog
```
+ 回到历史版本
```
$ git reset --hard 版本/commit ID
```
```
HEAD^:上一个版本
HEAD^^:上上一个版本
```

**8.撤销修改**
+ (未add)舍弃工作区的修改，回到上次commit或add的状态
```
$ git checkout -- 文件名
```
+ (add后)把暂存区的修改撤销掉
```
$ git reset HEAD 文件名
$ git checkout -- 文件名
```

**9.删除文件**
```
$ git rm 文件名
$ git commit
```

#### 5.远程仓库
+ 生成SSH Key
```
$ ssh-keygen -t rsa -C "邮箱"
```
+ 将SSH添加到GitHub的SSH Key
+ 添加远程库
```
$ git remote add 远程库简称 git@github.com:GitHub用户名/分支
```
+ 若远程库已存在，可以将之前的关联删除再关联新远程库
```
$ git remote rm origin
```
+ 提交到远程库
```
$ git push -u 远程库简称 master
$ git push 远程库简称 master
```
+ 从远程库克隆到本地目录下
```
git clone git@github.com:GitHub用户名/远程库
```

#### 6.分支管理
- 基本操作
	+ 列出所有分支
```
$ git branch
```
	+ 创建分支
```
$ git branch 分支名称
```
	+ 删除分支
```
$ git branch -d 分支名称
```
	+ 切换分支
```
$ git checkout 分支名称
```
	+ 合并指定分支到当前分支(直接指针跳转"快进模式"没有commit)
```
$ git merge 分支名称
```
	+ 合并指定分支到当前分支(禁用"快进模式"会生成commit)
```
$ git merge --no-ff -m "描述文本" dev
```
+ Dug分支
当你正在对某一分支做修改时，需要立即进行另一个文件操作，此时需要暂存当前修改，而不影响其他操作
	- 将当前分支编辑的工作隐藏
```
$ git stash
```
	- 查看隐藏工作
```
$ git stash list
```
	- 隐藏内容恢复
```
$ git stash apply
$ git stash apply stash@{num}:恢复指定隐藏工作
```
	- 清楚隐藏工作列表
```
$ git stash drop
```
	- 恢复隐藏工作并清楚隐藏工作列表
```
$ git stash pop
```
+ Feature分支
开发新功能
	- 使用上述功能进行操作与合并
	- 强行删除分支未同步的分支
```
git branch -D 分支名称
```
	- 删除分支已同步的分支
```
git branch -d 分支名称
```

#### 7.标签管理
所有标签都储存在本地，不会自动推送到远程
+ 查看所有标签
```
$ git tag
```
+ 为当前分支打标签
```
$ git tag 标签
```
+ 为commid ID打标签
```
$ git tag 标签 commit ID
```
+ 附加说明文字
```
$ git tag -a 标签 -m "" commit ID
```
+ 查看标签信息
```
$ git show 标签
```
+ 删除标签
```
$ git tag -d 标签
```
+ 推送标签到远程
```
$ git push 远程库 标签
$ git push 远程库 --tags
```
+ 删除远程标签
```
$ git tag -d 标签
$ git push 远程库 :refs/tags/标签
```













