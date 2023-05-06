# `Discuz!` 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)

## 插件语言包
### 创建语言包 
- 给插件创建语言包首先需要创建一个 `data/plugindata/*identifier*.lang.php` 文件，文件内容中包含 4 个数组，如下： 


```
<?php

$scriptlang['identifier'] = array(
  'english' => 'chinese',
  ...
);

$templatelang['identifier'] = array(
  'english' => 'chinese',
  ...
);

$installlang['identifier'] = array(
  'english' => 'chinese',
  ...
);

$systemlang['identifier'] = array(
  'file' => array(
     'english' => 'chinese',
     ...
  ),
  ...
);

?>

```
`$scriptlang` 为程序脚本文件的语言包。 

`$templatelang` 为模版文件的语言包。 

`$installlang` 为安装、升级、卸载脚本用的语言包。 

`$systemlang` 为系统语言包(`Discuz! X3` 新增)。 

如果插件不涉及某些类型的语言文字，变量可忽略。 

- 然后在插件基本设置中开启语言包选项后即可。 

### 调用语言包
模版中调用模板文件语言包，通过 `{lang *identifier*:english}` 方式调用。 

程序脚本中调用脚本文件语言包，通过 `lang('plugin/*identifier*', 'english')` 方式调用。 

安装脚本中调用安装脚本文件语言包，通过 `$installlang` 变量直接获取。如 `$installlang['english']`。 

系统语言包用于替换系统语言包中的某些语言条目。 

### 语言包导出
创建好的语言包在插件导出后会自动导出到 `XML` 文件中，供插件作者转码后发放多编码版本的插件。如上例中导出的 `XML` 中会包含以下内容： 


```
<item id="language">
    <item id="scriptlang">
        <item id="english"><![CDATA[chinese]]></item>
    </item>
    <item id="templatelang">
        <item id="english"><![CDATA[chinese]]></item>
    </item>
    <item id="installlang">
        <item id="english"><![CDATA[chinese]]></item>
    </item>
    <item id="systemlang">
        <item id="file">
            <item id="english"><![CDATA[chinese]]></item>
        </item>
    </item>
</item>

```
`data/plugindata/*identifier*.lang.php` 文件不必在插件发布的时候导出，此文件仅供插件设计者模式时使用。 

## 插件模板
插件的模板统一放置到 `source/plugin/*identifier*/template` 目录下，程序脚本通过以下语句调用插件模板文件，如下例，调用 `source/plugin/*identifier*/template/test`


```
include template('identifier:test');

```
模版中调用插件模版通过以下方法： 


```
{template identifier:test}

```
模板的编写详见[模板创建、解析原理详解](?ac=document&page=dev_template "模板创建、解析原理详解")

更新时间：2013-1-28
