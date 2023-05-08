# Discuz! Debug 模式
## 面向对象：
有一定 `php, mysql` 基础的站长，程序开发者
## 作用：
可以明细的列出当前页面的查询可以具体查询出现的文件，和时间。并且有查询的 `explain` 信息。便于检查哪里出现了慢查询。
可以查看当前页面内存使用情况
可以列出当前页面 `$_G` 变量中的内容
可以列出当前页面的 `cookie` 内容
可以查看当前浏览器的信息，`User Agent` 等

## 所需文件：

[function_debug.zip](https://www.dismall.com/forum.php?mod=attachment&aid=MTEyfDhkMDVlNDBkfDE2ODM1MzEzMDd8MHwyMTc%3D) 解压，将 `function_debug.php` 放到 `source/function` 目录下。

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
未完待续。
