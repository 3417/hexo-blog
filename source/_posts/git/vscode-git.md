---
title: vscode的git提交流程
date: 2021-09-08 10:01:09
tags: git
categories: git
---

## 基本操作
1. 添加暂存：
```
git add . //当前目录及其子目录
git add -A (仓库内所有的变更加入暂存区)
git add 文件1 文件2...(把指定文件添加到暂存区)
```
<!-- more -->
2. 本地commit
```
git commit -m "暂存信息"
```
3. push云端
```
git push
```
4. 拉取云端代码：
```
git pull --rebase  // git pull -r
```

5. 撤销commit
```
git revert HEAD //撤销前一次的commit
git revert commit //撤销指定版本，撤销也作为第一次提交保存
```
6. 查看git在那个分支上
```
git branch -v
```
7. 切换到指定的分支
```
git checkout 指定分支
```
8. 比较差异
```
git diff 某文件 (比较文件差异)
git diff --cache(比较暂存区和head的差异)
git diff (比较工作区和暂存区的所有差异)
git diff --cache 某文件(比较某文件暂存区和head的差异)
```
9. 回滚
```
git reset 文件1 文件2...(把暂存区指定文件回复和head一样)
git reset --hard(把暂存区和工作区所有文件恢复成和head一样)
```
10. 比较difftool比较任意两个commit的差异
```
git difftool commit1 commit2

注意，从工作区回滚到暂存区则用 checkout ，否则用 reset
```
11. 查看哪些文件没有被git管控
``` 
git ls-files --others
12.git reflog //获取本地commit所有的信息
```

## 查看git的信息
```
git log --oneline
git reflog
```

## 使用commitizen规范commit消息
```
全局安装:
npm install commitizen -g //全局安装规范化
本地安装:
npm:
npm install commitizen --save-dev
npm commitizen init cz-conventional-changelog --save-dev --save-exact

yarn:
yarn add commitizen --dev
yarn commitizen init cz-conventional-changelog --yarn --dev --exact

手动配置package.json
script:{
    commit:git-cz
}
```
### 使用
1. git cz 代替git commit
```
feat：新功能（feature）
fix：修补bug
docs：文档（documentation）
style： 格式（不影响代码运行的变动）
refactor：重构（即不是新增功能，也不是修改bug的代码变动）
test：增加测试
chore：构建过程或辅助工具的变动
perf:提高性能的代码更改
ci:对CI配置文件和脚本的更改（示例范围：travis、circle、browserstack、sattlabs）
...
```
2. 提交结构分为三部分

```
head、body、footer 
提交时，分别对应的是提交的类别、提交影响的范围、提交的简短描述、提交的变动信息。
```