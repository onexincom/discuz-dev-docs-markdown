# 其它模块
## 计划任务模块开发
- 本功能为 `Discuz! X3.0` 新增内容 
- 计划任务模块用于拓展一个计划任务项目，本模块会在插件安装时自动添加到系统计划任务中，并在插件卸载时自动从中删除 

脚本位置：`source/plugin/插件目录/cron/cron_name.php`


```
<?php

//cronname:mycron     计划任务名称，可写脚本语言包中的项目
//week:1              设置星期几执行本任务，留空为不限制
//day:1               设置哪一日执行本任务，留空为不限制
//hour:1              设置哪一小时执行本任务，留空为不限制
//minute:0,30         设置哪些分钟执行本任务，至多可以设置 12 个分钟值，多个值之间用半角逗号 "," 隔开，留空为不限制

if(!defined('IN_DISCUZ')) {
    exit('Access Denied');
}

//您的计划任务脚本内容

?>

```
## 缓存更新模块开发
- 本功能为 `Discuz! X3.0` 新增内容 
- 缓存更新模块用于在系统更新缓存时拓展一个缓存更新项目 

脚本位置：`source/plugin/插件目录/cache/cache_name.php`


```
<?php

if(!defined('IN_DISCUZ')) {
    exit('Access Denied');
}

function build_cache_plugin_name() {
    //您的缓存更新脚本内容
}

?>

```
友情提示：[下载学习 `Discuz! X3` 范例插件](?ac=document&page=download)

更新时间：2013-1-28
