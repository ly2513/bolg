---
layout: post
title:  解决.gitignore失效问题
categories: others
---

## 遇到的问题 ##

刚才写完文章之后发现我使用```git add *```的时候总是会把```_site/```下面所有的文件内容都会add到Git的缓存区中，而我本身设置的```.gitignore```文件无论我如何使用通配符去除```_site```都没有起到忽略的作用。

## 问题的原因 ##

由于我之前已经将```_site```目录纳入到了版本库之中，所以无论我现在怎么对```.gitignore```文件进行配置都无济于事。解决的思路是先将已经加入到版本库的缓存从版本库删除，然后修改.gitignore文件。

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

(全文完)



