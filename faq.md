---
layout: page
title: F&Q
permalink: /faq/
---

F&Q原本写作FAQ ，是Frequently Asked Questions的首字母构成的缩略词。

**(1) 问：如何让SSH保持长连接？**

**答：** 首先：修改配置文件 /etc/ssh/sshd_config 加入以下两个参数。

```shell
TCPKeepAlive yes
ServerAliveInterval 60 # 时间单位为秒，多少秒自动请求一次
```
然后：重启ssh服务

```shell
/etc/init.d/ssh restart
```
**(2) 问：SMTP和POP和IMAP的作用是什么？POP和IMAP有什么不用？**

**答：** 简单可以这么理解，SMTP是用来发送邮件的，POP/IMAP是用来接收邮件的。其中采用POP协议，客户端对邮件的删改操作不能和服务器端同步，而使用IMAP协议是可以同步的。

**(3) 问：Git http方式如何记住密码？**

**答：** 输入密码前先执行如下命令，再次提交的时候就不需要输入密码了。

```shell
git config --global credential.helper store
```

**(4) 问：Ubuntu编译PHP报错怎么办？**

**答：** 查看./configuer --.....的最后一行缺少什么，然后缺什么补什么就可以。一般都是缺少类库导致的。



{% include extends/disqus.html %}



