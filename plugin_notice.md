## Discuz! 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)请在您动手编写插件之前，还需要仔细的阅读以下原则，遵循这些原则，将有效的避免可能发生的问题： 

- 所有与插件的程序，包括其全部的前后台程序，请全部放入 source/plugin/ 目录中，同时在插件的安装说明中指出，插件的文件需要复制到哪些目录。为了避免与其他插件冲突，请尽量建立 source/plugin/ 下的子目录，并将插件程序放置于子目录下，这样您编写的插件将获得更好的兼容性。 
- 如果您的插件包含“导航栏”模块，该模块将统一用 plugin.php?identifier=xxx&module=yyy 的方式调用，请在相应链接、表单中使用此方式。其中 xxx 为插件的惟一标识符，yyy 为模块名称。前台插件外壳程序 plugin.php 已经加载了通用初始化模块 /source/class/class_core.php，不需再次引用。 
- 如果您的插件包含“管理中心”模块，该模块将统一用 admin.php?action=plugins&identifier=xxx&pmod=yyy 的方式调用，请在相应链接、表单中使用此方式。其中 xxx 和 yyy 的定义与“导航栏”模块中的相同。系统还允许用 admin.php?action=plugins&edit=$edit&pmod=$mod 的方式来生成链接和表单地址，$edit 和 $mod 变量已经被插件后台管理接口赋值，因此将这两个变量值带入 URL 中也是被支持的。由于后台模块是被 admin.php 调用，因此已加载了通用初始化模块 /source/class/class_core.php 并进行了后台管理人员权限验证，因此模块程序中可直接写功能代码，不需再进行验证。 
- 请勿绕过插件的前后台外壳（plugin.php 和 admin.php）而以直接调用某程序的方式编写插件，因为这样既导致了用户使用不便，代码冗余和不规范，同时又产生了因验证程序考虑不周到而带来的安全隐患。您可以在任何地方，包括链接、表单等处方便的使用上述 URL 地址对插件模块进行调用。 
- 所有与插件有关的程序，包括全部的前台程序，因全部使用外壳调用，请务必在第一行加入 

```	
if(!defined('IN_DISCUZ')) {
	exit('Access Denied');
}

```
后台程序第一行加入 

```	
if(!defined('IN_DISCUZ') || !defined('IN_ADMINCP')) {
	exit('Access Denied');
}

```
- 以免其被 URL 直接请求调用，产生安全问题。 
- 一般情况下，您发布插件请使用插件导出的功能，以方便使用者一次性导入插件的配置数据，极特殊的情况下，也可以分步骤告知使用者如何进行插件配置管理和安装此插件。 
- 如果功能独立，请尽量使用单独程序的方式编写插件（即外挂型插件），而尽量少的对论坛本身代码进行修改，这将为使用者今后的升级带来很大方便。 
- 您可以修改 Discuz! 本身的数据结构，但更推荐在不很影响效率的前提下将插件数据用另外的数据表存储，因为不能排除您增加的字段或索引和今后版本 Discuz! 核心数据字段重名的可能。在任何情况下，请不要删除 Discuz! 标准版本数据结构中已有的字段或索引。 
- 请在插件说明书中对插件做以详尽的描述，例如增加了哪些字段、哪些表，修改了或新增了哪些程序，版本兼容性，后续支持的提供方式（例如不提供支持，或以什么样的方式提供）。如果方便，请尽可能提供插件的卸载方法，例如去除哪些字段、删除哪些新增的程序、将哪些被插件修改的程序恢复原状等等，使用者会感激您为此付出的辛勤劳动，甚至愿意支付相应的费用支持您未来的发展。 
- 如果插件使用另外的数据表存储，请在插件管理中准确的设置插件所使用的数据表名称（不包含前缀），这样用户在备份数据的时候，能够把插件数据一同备份。 
- Discuz! 内置了 8 种自定义积分，存储于 common_member 表中的 extcredits1 至 extcredits8 字段中，类型为有符号整数。 

更新时间：2012-5-3

