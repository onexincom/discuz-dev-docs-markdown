[« 返回](?ac=document&page=dev)## Discuz! 的模板机制
[模板风格创建](?ac=document&page=dev_template)|[Discuz!模板解析语法](?ac=document&page=template_coderule)|[模板缓存与CSS缓存](?ac=document&page=template_css)|[内置常用CSS代码分析 ](?ac=document&page=template_sample)-  在设计模板之初，您需要详细了解一下模板解析语法，以进行模板制作实战 
-  语法示例中，变量可根据实际情况使用，本处仅使用：**变量$my_var****数组$my_arr**进行演示， 

## 目录
- [1PHP中使用template()函数显示已存在模板](?ac=document&page=template_coderule#PHP.E4.B8.AD.E4.BD.BF.E7.94.A8template.28.29.E5.87.BD.E6.95.B0.E6.98.BE.E7.A4.BA.E5.B7.B2.E5.AD.98.E5.9C.A8.E6.A8.A1.E6.9D.BF)
- [2PHP格式的模板](?ac=document&page=template_coderule#PHP.E6.A0.BC.E5.BC.8F.E7.9A.84.E6.A8.A1.E6.9D.BF)
- [3模板语法](?ac=document&page=template_coderule#.E6.A8.A1.E6.9D.BF.E8.AF.AD.E6.B3.95)
    - [3.1变量输出](?ac=document&page=template_coderule#.E5.8F.98.E9.87.8F.E8.BE.93.E5.87.BA)

    - [3.2条件判断](?ac=document&page=template_coderule#.E6.9D.A1.E4.BB.B6.E5.88.A4.E6.96.AD)

    - [3.3循环输出](?ac=document&page=template_coderule#.E5.BE.AA.E7.8E.AF.E8.BE.93.E5.87.BA)

    - [3.4模板嵌套](?ac=document&page=template_coderule#.E6.A8.A1.E6.9D.BF.E5.B5.8C.E5.A5.97)

    - [3.5插件钩子](?ac=document&page=template_coderule#.E6.8F.92.E4.BB.B6.E9.92.A9.E5.AD.90)

    - [3.6变量数组嵌套使用](?ac=document&page=template_coderule#.E5.8F.98.E9.87.8F.E6.95.B0.E7.BB.84.E5.B5.8C.E5.A5.97.E4.BD.BF.E7.94.A8)

    - [3.7PHP解析](?ac=document&page=template_coderule#PHP.E8.A7.A3.E6.9E.90)

    - [3.8语言包使用](?ac=document&page=template_coderule#.E8.AF.AD.E8.A8.80.E5.8C.85.E4.BD.BF.E7.94.A8)


- [4插件模板和语言包的设计](?ac=document&page=template_coderule#.E6.8F.92.E4.BB.B6.E6.A8.A1.E6.9D.BF.E5.92.8C.E8.AF.AD.E8.A8.80.E5.8C.85.E7.9A.84.E8.AE.BE.E8.AE.A1)
- [5综合示例](?ac=document&page=template_coderule#.E7.BB.BC.E5.90.88.E7.A4.BA.E4.BE.8B)

  
## PHP中使用template()函数显示已存在模板
-  在Discuz!程序执行中可以通过 include template('模板文件夹/模板名称无后缀');的方式进行解析，前提是您使用的Discuz!程序已经包含了 ./source/function/function_core.php 的函数库 

## PHP格式的模板
[X2.5新增内容] 

从 Discuz! X2.5 开始，模板文件支持 PHP 扩展名的格式，你可以创建例如 ./template/mytext/common/forum/discuz.php 文件，PHP 的模板文件中你只需在原有 HTM 的模板文件开头添加一行代码即可，如： 

```	
<?php exit;?>

```
```	
<?php echo '你不能看此模板的内容';exit;?>

```
PHP 的模板文件的模板数据内容将从文件的第二行开始解析。PHP 和 HTM 模板文件同时存在时，会优先解析 PHP 模板文件 

## 模板语法
### 变量输出
-  输出一个变量的值，等同于php的 <?php echo $my_var;?>，花括号可以省略但不建议去掉。 

```	
{$my_var}

```
### 条件判断
-  通过if判断流程分支 
    -  如果写在HTML表单元素中，可以省去使代码更清晰易读，如{if $my_var}xxx{/if} 



```	
<!--{if $my_var}-->
    任意html语句
<!--{/if}-->

```
-  带有多条件的if写法，可使用PHP常规判断中的按位运算符等 

```	
<!--{if $my_var && ($my_var2 & 1 || $my_var3 == 3)}-->
    任意html语句
<!--{/if}-->

```
-  带有分支条件的if写法 

```	
<!--{if $my_var == 1}-->
    变量为1
<!--{elseif $my_var == 2}-->
    变量为2
<!--{else}-->
    其他情况
<!--{/if}-->

```
### 循环输出
-  带有数组键的循环写法 

```	
<!--{loop $my_arr $key $val}-->
    循环输出的HTML语句
<!--{/loop}-->

```
-  没有数组键的循环写法 

```	
<!--{loop $my_arr $val}-->

```
### 模板嵌套
-  将被嵌套模板内容解析为PHP语句并合并入本模板中的写法 
    -  common/header 对应某个模板套系中的common目录的header模板文件 



```	
<!--{subtemplate common/header}-->

```
-  程序运行时include嵌套模板内容 

```	
<!--{template common/header}-->

```
### 插件钩子
-  在模板中设立插件钩子 [插件模板和语言包的设计](?ac=document&page=plugin_language "插件模板和语言包的设计")
    -  hook为关键词，意为将index_top定义为钩子 



```	
<!--{hook/index_top}-->

```
### 变量数组嵌套使用
-  条件判断或变量输出时用到 

```	
<!--{if $my_arr[$my_var]}-->
<!--{if $my_arr[0]}-->
<!--{if $my_arr[$my_arr2[$my_var]]}-->

```
### PHP解析
-  在模板中使用PHP语句可以通过{eval}进行 

```	
<!--{eval $my_var = 1;}-->
<!--{eval echo $my_var;}-->
<!--{eval $my_arr = array(1, 2, 3);}-->
<!--{eval print_r($my_arr);}-->
<!--{eval output();}-->
<!--{eval exit();}-->

```
-  多行PHP解析(Discuz! X3 新增) 

```	
<!--{eval}-->
...PHP语句...
<!--{/eval}-->

```
### 语言包使用
-  在模板中可以通过下面的代码来使用语言包中的某个值 

```	{lang index_yesterday}
```
-  其中语言包在 ./source/language/目录下，以PHP数组形式存放 

## 插件模板和语言包的设计
**请参见：[插件模板和语言包的设计](?ac=document&page=plugin_language "插件模板和语言包的设计")**

## 综合示例
-  综合示例题目1：php程序中创建一个数组并在模板中循环，并且根据模板显示奇数行输出不同的CSS样式 

1.  PHP端代码： 

-  此PHP代码省略了包含 class_core.php 以及初始化$_G变量，详细请查看： 

```	
<?php
    /*此处省略include class_core.php*/
    $my_arr = array('one', 'two', 'three', 'four');
    include template('forum/mytest'); //使用自定义模板套系中的forum目录的mytest
?>

```
1.  模板代码： 

```	
    <!--{loop $my_arr $key $val}-->
        <div {if $key % 2 == 1}style="background: #ccc;"{/if}>
            这里是value值：{$val}
        </div>
    <!--{/loop}-->

```
-  综合示例题目2：结合风格常量与javascript，动态改变模板页面的字体大小,并引用默认模板的header和footer 
    -  默认风格中，小号字体大小 {SMFONTSIZE}为0.83em，主题列表字体大小 {THREADTITLEFONTSIZE}为14px，**在Disucz!X2中使用时，需要使用$_G['style']['SMFONTSIZE']和$_G['style']['THREADTITLEFONTSIZE']**。 

    -  $('test1')此写法是因为header中已经加载了common.js全局javascript脚本文件，可以通过简写来达到document.getElementById('test1')的效果 

    -  ./template/mytest/forum/mytest模板代码如下 



```	
<!--{subtemplate common/header}-->
<div id="test1" style="font-size:{$_G['style']['FONTSIZE']};">
    这是一个改变字体的实例
</div>
<span onclick="changefontsize('{$_G['style']['SMFONTSIZE']}');">改变小号字</span><span onclick="changefontsize('{$_G['style']['THREADTITLEFONTSIZE']}');">改变为大号字</span>
<script type="text/javascript">
function changefontsize(size) {
    $('test1').style.fontSize = size;
}
</script>
<!--{subtemplate common/footer}-->

```
更新时间：2013-9-4

