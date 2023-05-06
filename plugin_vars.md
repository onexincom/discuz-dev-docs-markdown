[« 返回](?ac=document&page=dev)## Discuz! 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)编写插件程序时，可能需要读取一些插件的信息，如果插件需要使用者进行配置，还需要读取使用者设置的参数值。Discuz! 允许插件程序使用数据库读取和缓存读取这两种方法获取插件信息和参数。Discuz! 的插件接口已经对插件信息进行了合理的缓存，使用缓存读取的方式，将比数据库读取速度更快，消耗的资源更是几乎可以忽略不计。缓存读取唯一的局限是需要插件使用插件接口提供的通用后台管理程序。如果使用自定义后台模块的方式，需要后台模块将参数存放到 pluginvars 数据表中，才能被系统正常缓存。我们强烈推荐您通过缓存读取插件信息和配置数据。 

由于调用系统缓存统一通过“loadcache()”函数调用，并存放于 $_G['cache'] 中，因此“loadcache('plugin')”后插件的变量缓会存放于 $_G['cache']['plugin'] 中。嵌入点插件和以 plugin.php 为主脚本调用的插件无需加载此缓存，系统已自动加载了缓存。变量配置类型为“版块/*”的变量会保存在 $_G['cache']['forums'][fid]['plugin'] 中。变量配置类型为“用户组/*”的变量会保存在 $_G['cache']['usergroup_groupid']['plugin'] 和 $_G['group']['plugin'] 中。 

更新时间：2012-5-3

