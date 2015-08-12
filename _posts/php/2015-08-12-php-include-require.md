---
layout: post
title:  PHP中的include和require详解
categories: [php]
---

接触过PHP的都知道PHP引入文件的方式有两个类型：include类型和require类型。这两种类型又对应这四种方法include_once()和require_one()。这篇文章主要介绍他们的异同。


## require和inlcude原理 ##

require和include对文件的处理方式不一样。include引入文件每次都会对文件进行读取和评估，而require只是把文件内容读取到引入的位置。当然，include_once()和reqire_once()同理。

require_once() 和 include_once()则保证一个脚本内对同一个文件的包含只进行一次。

## 实验：当引用文件不存在时 ##

include和include_once在引用不存在的文件的时候会打开文件失败的警告。而require和require_once则会报打开文件的错误。具体的实验如下。前提：test.php不存在。

注意：我测试环境是MAC OS，PHP的版本为5.6.11。

**include测试**

```php
// 测试脚本
<?php 
	include "test.php";
	echo "hello world";
?>
// 输出结果
Warning: include(): Failed opening 'test.php' for inclusion......
hello world
```

**include_once测试**

```php
// 测试脚本
<?php
	include_once "test.php";
	echo "hello world";
?>
// 输出结果
Warning: include_once(): Failed opening 'test.php' for inclusion......
hello world
```

**require测试**

```php
// 测试脚本
<?php  
	require "test.php";
	echo "hello world";
?>
// 输出结果
Fatal error: require(): Failed opening required 'test.php'......
```

**require_once测试**

```php
// 测试脚本
<?php  
	require_once "test.php";
	echo "hello world";
?>
// 输出结果
Fatal error: require_once(): Failed opening required 'test.php'......
```
**结论**

引用文件不存在的时候include报警告，脚本继续执行，require报错误，脚本终止执行。

## 结论：我们用什么？ ##

这里先贴出一下```stackoverflow```牛人的回答。

The require() function is identical to include(), except that it handles errors differently. If an error occurs, the include() function generates a warning, but the script will continue execution. The require() generates a fatal error, and the script will stop.

The require_once() statement is identical to require() except PHP will check if the file has already been included, and if so, not include (require) it again.

所以用什么，第一看你是否在文件不存在的时候直接终止程序的执行，如果是用require系列否则用include系列。就是这么简单。而在性能上几乎没有什么差别。

## 参考链接 ##

[stackoverflow]

[stackoverflow]:http://stackoverflow.com/questions/2418473/when-should-i-use-require-once-vs-include