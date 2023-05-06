[« 返回](?ac=document&page=dev)## Discuz! 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)插件实现流程 开始编写社区插件，您应当首先对插件实现的流程有一个大致的了解，以下是我们推荐的插件编写流程： 

- 熟练使用 Discuz! 社区系统后，对希望完善或补充的个性化功能进行评估，进而提出插件的功能需求。 
- 对插件做一个概括性的设计，例如：需要使用什么菜单、什么参数，配置哪些选项、数据结构如何设计、前后台实现哪些功能等等。 
- 阅读本文档并在系统设置中实际体验 Discuz! 插件接口所实现的功用，例如：您的插件应当如何设计才能良好的挂接到社区系统中来。插件接口能够实现哪些功能、不能实现哪些功能，插件为此而需要做的优化、改造和取舍。 
- 编写相应程序代码和模板语句，实现所需的功能并进行代码测试、兼容性测试和代码改进。 
- 如果需要公开您的插件，可以用插件导出的方式，将插件配置信息导出到一个 XML 文件中，连同相应的程序和模板文件一同打包。同时，编写一个适合新手的插件的说明书也是必不可少的，其中包括：插件适用的 Discuz! 版本、功能概述、兼容性声明、安装方法、使用方法、卸载方法等等。 
- 将插件提供给他人，或自己使用，根据使用者反馈，对插件进行完善。插件实现流程至此结束。 

  


文件命名规范 Discuz! 按照如下的规范对程序和模板进行命名，请在设计插件时尽量遵循此命名规范： 

- 可以直接通过浏览器访问的普通程序文件，以 .php 后缀命名。 
- 被普通程序文件引用的程序文件，以 .inc.php 后缀命名。 
- 被普通程序文件，或引用程序文件引用的函数库或类库，以 .func.php(函数库) 或 .class.php(类库) 后缀命名。 
- 模板文件，以 后缀命名，插件模板文件存在于 source/plugin/*identifier*/template/ 目录中，手机版插件模板存在于 source/plugin/*identifier*/template/mobile/目录中 
- 模板语言包文件，以 .lang.php 后缀命名，插件语言包文件开发时存放于 data/plugindata/ 目录中，文件名为*identifier*.lang.php。 
- 动态缓存文件，存放于 ./data/cache 目录中，依据不同的功用进行独立的命名。 
- 使用后台数据备份功能生成的备份文件，通常以 .sql 为后缀，存放于 data/ 目录中。 
- 有些目录中存在内容为空白的 index 文件，此类文件是为了避免 Web 服务器打开 Directory Index 时可能产生的安全问题。 
- [X2.5新增内容] 从 Discuz! X2.5 开始，产品对数据表进行了封装，封装后的文件统一命名为 Table 类，通过“C::t(Table类文件名)”方式调用。插件如需封装自己的数据表，可将 Table 类文件存放于 source/plugin/*identifier*/table/ 目录下，并以 table_表名.php 格式命名，详见[X2.5的新程序架构](http://dev.discuz.org/wiki/index.php?title=X2.5%E7%9A%84%E6%96%B0%E7%A8%8B%E5%BA%8F%E6%9E%B6%E6%9E%84 "X2.5的新程序架构")。 

  


class_core.php 模块功能白皮书 source/class/class_core.php 是 Discuz! 的通用初始化模块程序，其几乎被所有的外部代码所引用，在您开始插件设计之前，可以先对该模块的大致功能做一定的了解。class_core.php 主要完成了以下任务： 

- 对不同 PHP 及操作系统环境做了判断和兼容性处理，使得 Discuz! 可以运行于各种不同配置的服务器环境下。 
- 初始化常量 IN_DISCUZ 为 TRUE，用于 include 或 require 后续程序的判断，避免其他程序被非法引用。 
- 读取社区程序所在绝对路径，存放于常量 DISCUZ_ROOT 中。 
- 加载所需的基本函数库 source/function/function_core.php。 
- 通过 config/config_global.php 中提供的数据库账号信息，建立数据库连接。Discuz! 支持数据表的前缀，如需获得表的全名，可使用“DB::table('tablename')”方式。 
- 判断用户是否登录，如登录标记 $_G['uid'] 为非 0，同时将 $_G['username']（加了 addslashes 的用户名，可用于不加修改的插入数据库）、 $_G['member']['username']（原始的用户名，可用于页面显示）、$_G['member']['password']（用户密码的MD5串）等相应用户信息赋值，其他用户信息存放于 $_G['member']，更多信息可通过“getuserprofile()”获取。 
- 判断用户管理权限，将管理权限标记 $_G['adminid'] 为 1~3 中间的值。0 代表普通用户；1 代表论坛管理员；2 代表超级版主；3 代表论坛版主。 将用户权限按照其所在的主用户组 ID 标记为 $_G['groupid']，相关权限从该 $_G['groupid'] 所对应的系统缓存中读出，存放于 $_G['group']。 
- 预置读入了每个模块的各种设置变量。 
- [X2.5变更内容] $_G['username'] 将不进行 addslashes 处理。 

更新时间：2012-5-3

