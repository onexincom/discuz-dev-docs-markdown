# Discuz! Debug 模式
## 面向对象：
有一定 `php, mysql` 基础的站长，程序开发者

## 作用：
可以明细的列出当前页面的查询可以具体查询出现的文件，和时间。并且有查询的 `explain` 信息。便于检查哪里出现了慢查询。 可以查看当前页面内存使用情况 可以列出当前页面 `$_G` 变量中的内容 可以列出当前页面的 `cookie` 内容 可以查看当前浏览器的信息，`User Agent` 等

## 所需文件：
将 `function_debug.php` 放到 `source/function` 目录下。

在 `Git` 上一键复制 [`function_debug.php`](https://gitee.com/Discuz/DiscuzX/blob/v3.5/upload/source/function/function_debug.php) 源码，或者下载 [`function_debug.zip`](https://www.dismall.com/forum.php?mod=attachment&aid=MTEyfDhkMDVlNDBkfDE2ODM1MzEzMDd8MHwyMTc%3D) 解压。

## 修改配置文件：
修改 `config\config_global.php`，在 `$_config = array();` 后加入一行：


```php
$_config['debug'] = 1;
```
则，每个页面都将开启 `debug` 模式。

如果修改为：


```php
$_config['debug'] = 'debug';
```
则不是每个页面都显示 `debug` 信息只有在 `url` 后面加上 `&debug=debug` 才会显示，这就可以避免普通用户也看到 `debug` 信息了。

## `debug` 信息解释

```php
文件版本: Discuz! X3.5 20230316
ModID: forum::index
包含: [文件列表] 51 in 0.054800s
执行:

服务器环境: WINNT, Apache/2.4.23 (Win32) OpenSSL/1.0.2j mod_fcgid/2.3.9 MySQL/5.7.26(db_driver_mysqli)
内存: 3,425,856 bytes, 峰值 3,566,816 bytes
SQL: [SQL列表][AjaxSQL列表] 18(discuz_table: 21, Using filesort: 4) in 0.130452s
内存缓存:

客户端 [详情] firefox:true chrome:112.0.0.0 safari:537.36 mozilla:5.0 webkit:537.36

[TOP] $_COOKIE 执行 update.php

```
