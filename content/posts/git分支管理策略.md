+++
title="git分支管理策略"
description="一个成功的git分支模型"
date="2021-01-25"
draft=true
+++

针对当下而言，最成熟的版本控制系统无疑是git了，相对其他的版本控制系统，git的使用比较广泛，分支比较灵活，分支灵活的优点是自由度高。

但同样自由度高时就代表着版本管理规范依赖自己或者社区探索，以下所要讲述的就是一个相对来说应用比较广的分支管理策略

### 主分支master
首先是主分支master，master主要是预备生产分支

```shell
git tag -a v1.0 -m "test" //新建一个tag，备注版本信息
git push origin v1.0    //tag 推送到远程
git ls-remote   //列出远程所有tag
```

### 开发分支develop
主分支用来发布大版本，日常开发分支我们使用develop，有人称为集成分支，来源于master，最终又合并到master

```
   git checkout -b develop 
   git checkout master 
   git merge merge develop //或者git merge --no-ff develop 后面在解答为什么使用 --no-ff
```

那么，为什么使用--no-ff呢，暂时不讨论这个问题

### 辅助分支
辅助分支和关键分支一起，用来支持团队成员并行开发，使用完成之后需要产出，主要包括
- 功能（feature）分支
- 预发布（release）分支
- 修补bug（fixbug）分支

##### 功能分支
一般从develop分离出来，开发完成又合并到master






