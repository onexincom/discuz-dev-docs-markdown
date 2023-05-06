
# Discuz! 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)

## 目录
1. [广告类](?ac=document&page=plugin_classes#.E5.B9.BF.E5.91.8A.E7.B1.BB)
1. [道具类](?ac=document&page=plugin_classes#.E9.81.93.E5.85.B7.E7.B1.BB)
1. [任务类](?ac=document&page=plugin_classes#.E4.BB.BB.E5.8A.A1.E7.B1.BB)
1. [验证问答类](?ac=document&page=plugin_classes#.E9.AA.8C.E8.AF.81.E9.97.AE.E7.AD.94.E7.B1.BB)
1. [验证码类(`Discuz! X2.5` 新增)](?ac=document&page=plugin_classes#.E9.AA.8C.E8.AF.81.E7.A0.81.E7.B1.BB.28Discuz.21_X2.5_.E6.96.B0.E5.A2.9E.29)

## 广告类
脚本位置：`source/class/adv/adv_name.php`

语言包位置：`source/language/adv/lang_name.php`

【`Discuz! X3.0` 新增】 

脚本位置：`source/plugin/(identifer)/adv/adv_name.php`

缩略图：`source/plugin/(identifer)/adv/adv_name.gif`


```
<?php

class adv_name {

    var $version = '1.0';//脚本版本号
    var $name = 'name';//广告类型名称 (可填写语言包项目)
    var $description = 'desc';//广告类型说明 (可填写语言包项目)
    var $copyright = 'Comsenz Inc.';//版权 (可填写语言包项目)
    var $targets = array('portal', 'home', 'member', 'forum', 'group', 'userapp', 'plugin', 'custom');//广告类型适用的投放范围
    var $imagesizes = array('120x60', '120x240');//图片广告推荐大小

    function getsetting() {//返回设置项目
        $settings = array(
            'text' => array(
                'title' => 'text_title',//设置项目名称 (可填写语言项目)
                'type' => 'mradio',//项目类型
                'value' => array(),//项目选项
                'default' => 0,//项目默认值
            )
        );
        return $settings;
    }

    function setsetting(&$advnew, &$parameters) {//保存设置项目
    }

    function evalcode() {//广告显示时的运行代码
        return array(
            //检测广告是否投放时的代码
            'check' => '
            if(condition) {
                $checked = false;
            }',
            //广告显示时的代码 (随机调用投放的广告)
            'create' => '$adcode = $codes[$adids[array_rand($adids)]];',
        );
    }
}

?>

```
## 道具类
脚本位置：`source/class/magic/magic_name.php`

语言包位置：`source/language/magic/lang_name.php`

【`Discuz! X3.0` 新增】 

脚本位置：`source/plugin/(identifer)/magic/magic_name.php`

图标：`source/plugin/(identifer)/magic/magic_name.small.gif、source/plugin/(identifer)/magic/magic_name.gif`


```
<?php

class magic_name {

    var $version = '1.0';//脚本版本号
    var $name = 'name';//道具名称 (可填写语言包项目)
    var $description = 'desc';//道具说明 (可填写语言包项目)
    var $price = '10';//道具默认价格
    var $weight = '10';//道具默认重量
    var $copyright = 'Comsenz Inc.';//版权 (可填写语言包项目)

    function getsetting() {//返回设置项目
        $settings = array(
            'text' => array(
                'title' => 'text_title',//设置项目名称 (可填写语言项目)
                'type' => 'mradio',//项目类型
                'value' => array(),//项目选项
                'default' => 0,//项目默认值
            )
        );
        return $settings;
    }

    function setsetting(&$advnew, &$parameters) {//保存设置项目
    }

    function usesubmit($magic, $parameters) {//道具使用
    }

    function show($magic) {//道具显示
    }

}

?>

```
## 任务类
脚本位置：`source/class/task/task_name.php`

语言包位置：`source/language/task/lang_name.php`

【`Discuz! X3.0` 新增】 

脚本位置：`source/plugin/(identifer)/task/task_name.php`

图标：`source/plugin/(identifer)/task/task_name.gif`


```
<?php

class task_name {

    var $version = '1.0';//脚本版本号
    var $name = 'name';//任务名称 (可填写语言包项目)
    var $description = 'desc';//任务说明 (可填写语言包项目)
    var $copyright = 'Comsenz Inc.';//版权 (可填写语言包项目)
    var $icon = '';//默认图标
    var $period = '';//默认任务间隔周期
    var $periodtype = 0;//默认任务间隔周期单位
    var $conditions = array(//任务附加条件
        'text' => array(
            'title' => 'text_title',//设置项目名称 (可填写语言项目)
            'type' => 'mradio',//项目类型
            'value' => array(),//项目选项
            'default' => 0,//项目默认值
            'sort' => 'complete',//条件类型 (apply:申请任务条件 complete:完成任务条件)
        ),
    );

    function preprocess($task) {//申请任务成功后的附加处理
    }

    function csc($task = array()) {//判断任务是否完成 (返回 TRUE:成功 FALSE:失败 0:任务进行中进度未知或尚未开始  大于0的正数:任务进行中返回任务进度)
    }

    function sufprocess($task) {//完成任务后的附加处理
    }

    function view($task, $taskvars) {//任务显示
    }

    function install() {//任务安装的附加处理
    }

    function uninstall() {//任务卸载的附加处理
    }

    function upgrade() {//任务升级的附加处理
    }

}

?>

```
## 验证问答类
脚本位置：`source/class/secqaa/secqaa_name.php`

语言包位置：`source/language/secqaa/lang_name.php`

【`Discuz! X3.0` 新增】 

脚本位置：`source/plugin/(identifer)/secqaa/secqaa_name.php`


```
<?php

class secqaa_name {

    var $version = '1.0';//脚本版本号
    var $name = 'name';//验证问答名称 (可填写语言包项目)
    var $description = 'desc';//验证问答说明 (可填写语言包项目)
    var $copyright = 'Comsenz Inc.';//版权 (可填写语言包项目)

    function make(&$question) {//返回安全问答的答案和问题 ($question 为问题，函数返回值为答案)
    }

}

?>

```
## 验证码类(`Discuz! X2.5` 新增)
脚本位置：`source/class/seccode/seccode_name.php`

语言包位置：`source/language/seccode/lang_name.php`

【`Discuz! X3.0` 新增】 

脚本位置：`source/plugin/(identifer)/seccode/seccode_name.php`


```
<?php

class seccode_name {

    var $version = '1.0';//脚本版本号
    var $name = 'name';//验证码类型名称 (可填写语言包项目)
    var $copyright = 'Comsenz Inc.';//版权 (可填写语言包项目)
    var $setting = array();//后台设置后的变量

    function check() {//检查输入的验证码，返回 true 表示通过       
    }

    function make() {//输出验证码，echo 输出内容将显示在页面中
    }

    function image() {//纯图片验证码 URL，用于移动端显示(Discuz! X3.1 新增)
    }

}

?>

```
友情提示：[下载学习 Discuz! X3 范例插件](https://addon.dismall.com/resource/Discuz_X3.0_Plugin_Sample.zip)

更新时间：2013-10-16
