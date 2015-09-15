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

{% include extends/disqus.html %}



