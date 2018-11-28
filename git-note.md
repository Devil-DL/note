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

## 分支操作

git checkout branchname 更换分支

git checkout -b branchname 创建一个新的分支并且更换

git merge branchname 将当前分支合并到branchname对应的分支

git rebase branchname 将当前分支rebase到branchname对应的分支

git checkout commitid 让head指针跳转到某个提交上

## 杂项 

在window的git中，默认使用了凭证管理器，因此可以使用https的方式直接连接git，相当于每次都填写了表单

git pull会进行合并，所以可以用git fetch先取回远程的修改