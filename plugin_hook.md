
# `Discuz!` 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)

## 页面嵌入类型脚本格式

```
<?php

//全局嵌入点类（必须存在）
class plugin_identifier {

    function HookId_1() {
        ......
        return ...;
    }

    function HookId_2() {
        ......
        return ...;
    }

    ......

}

//脚本嵌入点类
class plugin_identifier_CURSCRIPT extends plugin_identifier {

    function HookId_1() {
        ......
        return ...;
    }

    function HookId_2() {
        ......
        return ...;
    }

    ......

}

?>

```
### `plugin_`
普通版脚本中的类名以 `plugin_` 开头。手机版脚本中的类名以 `mobileplugin_` 开头。 

### `identifier`
插件的唯一标识符，在插件设置中设置。 

### `CURSCRIPT`
嵌入点位于的脚本名，如 `forum.php` 为 `forum`。 

X3.4 最新版本开始支持 `plugin.php` 为 `CURSCRIPT` 的插件之间的 `hook` 调用，`CURSCRIPT` 值为 `plugin`。`New!`

### `HookId`
#### **函数名**：`*HookId*()`
**调用位置**：所有模块执行前被调用  
**声明位置**：脚本嵌入点类  
**参数含义**： 

#### **函数名**：`*HookId*_output($value)`
**调用位置**：模块执行完毕，模板输出前被调用  
**声明位置**：脚本嵌入点类  
**参数含义**：


```
$value: array(
'template' => 当前要输出的模版, 'message' => showmessage 的信息内容, 'values' => showmessage 的信息变量, 
)

```
#### **函数名**：`global_*HookId*()`
**调用位置**：模块执行完毕，模板输出前被调用  
**声明位置**：全局嵌入点类 

#### **函数名**：`*HookId*_message($value)`
**调用位置**：`showmessage()` 执行时调用  
**声明位置**：脚本嵌入点类  
**参数含义**：


```
$value: array(
'param' => showmessage() 函数的参数数组, 
) 

```
#### **函数名**：`ad_*adId*($value)`
**调用位置**：相应的广告位中调用 函数名为广告位脚本 ID 如：`ad_headerbanner()`

**声明位置**：全局嵌入点类 脚本嵌入点类 

**参数含义**：


```
$value: array(
'params' => 广告位参数, 'content' => 当前广告位原本将要显示的内容, 
) 

```
#### **函数名**：`common()`
**调用位置**：所有模块执行前被调用  
**声明位置**：全局嵌入点类 

#### **函数名**：`discuzcode($value)`
**调用位置**：`discuzcode()` 函数执行时调用 用于在帖子内容解析时嵌入自己的功能，函数中 `$_G['discuzcodemessage']` 变量为待解析的字串 

**声明位置**：全局嵌入点类  
**参数含义**：


```
$value: array(
'param' => caller 函数的参数数组, 'caller' => caller 函数，此嵌入点被哪个函数调用 'discuzcode' 被 discuzcode() 调用 'messagecutstr' 被 messagecutstr() 调用 
) 

```
#### **函数名**：`deletethread($value)`
**调用位置**：`deletethread()` 函数执行时调用 用于在主题删除前后嵌入自己的功能，此函数将在 `deletethread()` 中被调用 2 次，函数中 `$_G['deletethreadtids']` 变量为待处理的 TID 数组 

**声明位置**：全局嵌入点类  
**参数含义**：


```
$value: array(
'param' => deletethread() 函数的参数数组, 'step' => 删除的步骤 'check' 检测步骤 'delete' 删除步骤
)

```
#### **函数名**：`deletepost($value)`
**调用位置**：`deletepost()` 函数执行时调用 用于在帖子删除前后嵌入自己的功能，此函数将在 `deletepost()` 中被调用 2 次，函数中 `$_G['deletepostids']` 变量为待处理的 ID 数组 

**声明位置**：全局嵌入点类  
**参数含义**：


```
$value: array(
'param' => deletepost() 函数的参数数组, 'step' => 删除的步骤 'check' 检测步骤 'delete' 删除步骤 
)

```
#### **函数名**：`avatar($value)`(`X2.5` 新增)
**调用位置**：`avatar()` 函数执行时调用 用于在头像调用时嵌入自己的功能，函数中 `$_G['hookavatar']` 变量为新头像返回值 

**声明位置**：全局嵌入点类  
**参数含义**：


```
$value: array(
'param' => avatar() 函数的参数数组 
) 

```
#### **函数名**：`profile_node($post, $start, $end)`(`X3.0` 新增)
**调用位置**：贴内用户信息标记，返回值为标记显示内容  
**声明位置**：全局嵌入点类  
**参数含义**：`$post:` 当前帖子信息数组 `$start:` 用户填写的前置字符 

`$end:` 用户填写的后置字符 

#### **函数名**：`identifier__hookid(_output)()`(`X3.4` 新增`New!`)
**调用位置**：插件的`hook`调用 `identifier`为输出对象的应用ID，`hookid`为输出对象应用自定义的`hook`名称

其他使用方法参考`HookId()`以及`HookId_output($value)`

**参数含义**： 

**声明位置**：脚本嵌入点类应用互动嵌入点类 

要查看所有的预定义嵌入点，请打开 `config/config_global.php` 文件，将文件结尾添加的设计者模式值改成“2”，然后更新缓存即可。在页面源码中查找""可搜索到嵌入点。（详细内容可参阅的《[插件嵌入点列表](?ac=document&page=plugin_hooklist "插件嵌入点列表")》） 


```
$_config['plugindeveloper'] = 2;
```
预定义的嵌入点会在页面预置好的位置输出函数返回的内容。函数返回值类型如果是 `array` 且是空值的，必须输出一个空数组，如： 


```
return array();
```
函数名并不限于以上列表，您可以自定义，只要符合以下规则，函数就会在适当的地方被调用。 


```
function CURMODULE_USERDEFINE[_output]()
```
`CURMODULE` 指明了此函数在哪个模块执行，可通过常量 `CURMODULE` 得到当前页面的 `CURMODULE` 值。 `USERDEFINE` 可自定义，如果函数名以`“_output”`结尾则会在模板输出前调用，否则会在模块执行前调用。 如：`attachment_test()` 函数会在论坛的下载附件的时候执行。 `“_output”`结尾的函数的第一个参数为数组，含义为 `array('template' => 要输出的模板名, 'message' => showmessage 的文字)` 如：以下函数将在登录的时候输出调试文字 


```
function logging_test_output($a) {
    print_r($a);
    print_r($_POST);
}
```
`plugin_identifier` 类中的其它函数为了便于阅读建议以`“_”`开头，如： 


```
<?php

class plugin_sample {

    function _updatecache() {
        ......
        return ...;
    }

}

class plugin_sample_forum extends plugin_sample {

    function viewthread_posttop() {
        ......
        return ...;
    }

    ......

}

?>
```
## 插件嵌入点列表
附: [插件嵌入点列表](?ac=document&page=plugin_hooklist "插件嵌入点列表")

更新时间：2013-1-28
