---
title: git
date: 2021-09-08 09:53:26
index_img: /img/git/git.jpg
banner_img: /img/git/git.jpg
tags: git
categories: git
---

## 0.配置全局的git

1. 配置全局的git.username
```
git config --global user.name "xxx"
git config --global user.email "xxx"
```
2. 查看配置
```
git config --list // 或者 git config查看所有的配置
```
<!-- more -->

## 1. 解决冲突
```
git merge dev/ master

git rebase（也可以使用）

合并分支出现冲突
git status 查看状态

再次
A. git add .
B. git commit -m "xxxxfix"
C. git push
```


## 2.使用了代码规范提交代码commit不上请使用
```
git commit --no-verify -m "xxxx"  //不推荐使用这种方法，但是管用
```


## 3.使用ssh-keygen去掉密码：
```
ssh-keygen -p [-P old_pass] [-N new_pass] [-f keyfile]
eg: ssh-keygen -p -P test1234 -N '' -f ~/.ssh/id_rsa
```


## 4.清除git的账户和密码
```
//清除掉缓存在git中的用户名和密码
git credential-manager uninstall
```


## 5.保存项目的用户名和密码
```
git config user.name
git config user.email

git config credential.helper store  //缓存用户信息


git pull -r  //直接查看拉取数据是否还是需要输入用户名和密码

```
## 6.删除git stash内容(缓存的内容)
```
git stash list //查看内容

git stash clear //删除全部内容

git stash drop stash@{0} //删除第一个队列

```
## 7.git本地commit撤销
```
git reset HEAD~1
OR
git reset HEAD~ //回滚全部
```
## 8.git merge 合并分支
```
git chekout master

git pull origin master

git merge dev

git status

git  push
```
## 9.git强制提交
```
git push -f origin master  
//origin远程仓库名，master分支名，-f为force，意为：强行、强制。
```

## 10.git拉取某个分支
```
git clone -b xxx.git
```

## 11.回滚
```
1、git log //获取提交的id日志

2、git reset --hard "id" //本地回滚

3、git push -f //远端回滚版本
```

## 12.git rebase
```
编辑完成后，可以点ESC 在输入:wq做保存，不想保存的话就输入:q!
结束上面流程后在查看一次log commit记录
```

## 13.git 使用.gitignore忽略已经提交的文件或者文件夹
```
git rm -r --cached <projectName>
git commit -m "<备注信息>"
git push //提交信息
```