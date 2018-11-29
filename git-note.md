# git使用方法简要说明

## 各种查看区别

git diff 查看暂存区和工作区的区别

git diff --cached 查看暂存区和仓库的区别

git diff HEAD 查看工作区和仓库的区别

## 显示历史

git log --graph --all 以图形方式显示git历史

## 各种取消

git reset HEAD filename 取消暂存的文件,该指令不修改工作区，只修改暂存区

git checkout -- filename **丢弃**工作区的内容，视情况恢复到版本库或者暂存区的状态

## rebase操作

git rebase -i start_commmit_id end_commit_id 用来对两个commit之间的提交信息进行修改
在弹出的交互操作中，使用r进行改名，s合并上一个commit，详见弹出提示

## 暂存修改

git stash 暂存当前的快照，工作区变为clean

git stash list 查看暂存的情况   

git stash pop 恢复工作区，同时记录清除


## 分支操作

git checkout branchname 更换分支

git checkout -b branchname 创建一个新的分支并且更换

git merge branchname 将当前分支合并到branchname对应的分支

git rebase branchname 将当前分支rebase到branchname对应的分支

git checkout commitid 让head指针跳转到某个提交上

git checkout commitid -b 从某个历史分支创建分支

## 远程仓库

向remote push某个分支

git push ( remote-name ) ( branch-name )

取回远程仓库的所有分支

git fetch ( remote-name )

给某个远程仓库取个名字

git remote add (shortname) (url) 

添加现有仓库到远程项目

git remote add origin url // 先取个名字

git push -u origin master 

远程仓库改名

git remote rename origin github

## 标签操作

git tag tagname (commit_id) 给某个commit打标签，默认为当前

git tag 查看所有标签

git tag -d 删除某个标签

## 杂项 

git commit -a 跳过add阶段直接提交

在window的git中，默认使用了凭证管理器，因此可以使用https的方式直接连接git，相当于每次都填写了表单

git pull会进行合并，所以可以用git fetch先取回远程的修改

关于reset和checkout的区别，[官网文档](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E7%BD%AE%E6%8F%AD%E5%AF%86)写得很清楚


>   下面的速查表列出了命令对树的影响。 “HEAD” 一列中的 “REF” 表示该命令移动了 HEAD 指向的分支引用，而`‘HEAD’' 则表示只移动了 HEAD 自身。 特别注意 WD Safe? 一列 - 如果它标记为 NO，那么运行该命令之前请考虑一下。
>   |  |HEAD|Index|Workdir|WD Safe?
>   ---|:--:|---:|:--:|---:
>   commmit|
>   reset --soft [commit]| REF| NO| NO| YES
>   reset [commit]| REF| YES| NO| YES|
>   reset --hard [commit]| REF| YES| YES| **NO**|
>   checkout [commit]| HEAD| YES| YES| YES|
>   |file
>   reset (commit) [file]| NO| YES| NO| YES|
>   checkout (commit) [file]| NO| YES| YES| **NO**|