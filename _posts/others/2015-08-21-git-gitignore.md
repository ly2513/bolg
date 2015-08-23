---
layout: post
title:  解决.gitignore失效问题
categories: others
---

## 遇到的问题 ##

刚才写完文章之后发现我使用git add *的时候总是会把_site/下面所有的文件内容都会add到git的缓存区中，而我本身设置的.gitignore文件无论我如何使用通配符去除_site都没有作用。

## 问题的原因 ##

因为之前我手贱，已经将_site目录纳入到了版本库之中，所以无论我现在怎么对.gitnore文件进行配置都无济于事。

## 解决的办法 ##

将之前不该加入到版本库的缓存文件进行删除

```shell
# 使用下面命令进行删除
git rm -rf --cached _site
```

将_site加入到.gitignore文件之中

```shell
# 如果你还需要屏蔽其他的文件，就别这么玩，老老实实vim修改.gitignore文件吧。
echo "_site" > .gitignore
```

然后进行commit和push操作。



