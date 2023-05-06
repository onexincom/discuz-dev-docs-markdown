# Discuz! 的插件机制
[准备工作](?ac=document&page=dev_plugin)|[插件接口](?ac=document&page=plugin_module)|[参数读取](?ac=document&page=plugin_vars)|[页面嵌入](?ac=document&page=plugin_hook)|[特殊主题](?ac=document&page=plugin_specialthread)|[第三方拓展类](?ac=document&page=plugin_classes)|[其它模块](?ac=document&page=plugin_other_module)  
[安装脚本](?ac=document&page=plugin_install)|[模板和语言包](?ac=document&page=plugin_language)|[注意事项](?ac=document&page=plugin_notice)

## 安装脚本
### 目录
- [安装、卸载](?ac=document&page=plugin_install#.E5.AE.89.E8.A3.85.E3.80.81.E5.8D.B8.E8.BD.BD)
- [升级](?ac=document&page=plugin_install#.E5.8D.87.E7.BA.A7)
- [检测](?ac=document&page=plugin_install#.E6.A3.80.E6.B5.8B)
- [开启、关闭(`Discuz! X3.1` 新增)](?ac=document&page=plugin_install#.BF.AA.C6.F4.A1.A2.B9.D8.B1.D5)
- [授权协议、插件介绍](?ac=document&page=plugin_install#.E6.8E.88.E6.9D.83.E5.8D.8F.E8.AE.AE.E3.80.81.E6.8F.92.E4.BB.B6.E4.BB.8B.E7.BB.8D)
- [Discuz! 版本兼容性设置](?ac=document&page=plugin_install#Discuz.21_.E7.89.88.E6.9C.AC.E5.85.BC.E5.AE.B9.E6.80.A7.E8.AE.BE.E7.BD.AE)
- [其他论坛数据导入](?ac=document&page=plugin_install#.E5.85.B6.E4.BB.96.E8.AE.BA.E5.9D.9B.E6.95.B0.E6.8D.AE.E5.AF.BC.E5.85.A5)
- [小提示](?ac=document&page=plugin_install#.E5.B0.8F.E6.8F.90.E7.A4.BA)

## 安装、卸载
插件作者可以设计 2 个脚本文件用于插件的安装和卸载，文件名任意。脚本中可用 `runquery()` 函数执行 SQL 语句，表名可以直接写“cdb_”。插件作者只需在导出的 XML 文件结尾加上安装、卸载脚本的文件名即可 


```
            <item id="installfile"><![CDATA[install.php]]></item>
            <item id="uninstallfile"><![CDATA[uninstall.php]]></item>
        </item>
    </root>

```
安装、卸载程序中可随意设计页面的跳转，只要在插件安装、卸载结束时候输出添加以下代码即可 


```
$finish = TRUE;
```
从 `Discuz! X3.1` 开始，卸载程序将不再支持页面的跳转及上面的 `$finish` 变量

## 升级
插件作者可以设计一个脚本文件用于插件的升级，文件名任意。脚本中可用 `runquery()` 函数执行 SQL 语句，表名可以直接写`“cdb_”`。插件作者只需在导出的 XML 文件结尾加上升级脚本的文件名即可 


```
            <item id="upgradefile"><![CDATA[upgrade.php]]></item>
        </item>
    </root>

```
升级程序中可通过 `$fromversion` 和 `$toversion` 变量判断升级的具体版本号，并随意设计页面的跳转，只要在插件升级结束时候输出添加以下代码即可。 


```
$finish = TRUE;
```
插件的当前版本号位于 XML 文件的以下分支中，可自行更改。 


```
        <item id="plugin">
            ......
            <item id="version"><![CDATA[当前版本]]></item>
            ......
        </item>

```
## 检测
插件作者可以设计一个脚本文件用于插件在安装、卸载、升级操作前的检测，文件名任意。插件作者只需在导出的 XML 文件结尾加上检测脚本的文件名即可 


```
            <item id="checkfile"><![CDATA[check.php]]></item>
        </item>
    </root>

```
## 授权协议、插件介绍
插件在安装的时候您可以自定义授权信息文本，文本支持 `Discuz!` 代码，站长同意后才能安装插件。如果插件存在后台管理界面或者变量配置，那么插件介绍文本会显示在插件后台页面中。插件作者只需在导出的 XML 文件结尾加上以下内容即可 


```
            <item id="license"><![CDATA[授权协议文本]]></item>
            <item id="intro"><![CDATA[插件介绍文本]]></item>
        </item>
    </root>

```
## 开启、关闭(`Discuz! X3.1` 新增)
插件作者可以设计 2 个脚本文件用于插件在开启和关闭时执行，文件名任意。脚本中可用 `runquery()` 函数执行 SQL 语句，表名可以直接写`“cdb_”`。插件作者只需在导出的 XML 文件结尾加上开启、关闭脚本的文件名即可 


```
            <item id="enablefile"><![CDATA[enable.php]]></item>
            <item id="disablefile"><![CDATA[disable.php]]></item>
        </item>
    </root>

```
## Discuz! 版本兼容性设置
请仔细检查您的插件是否可以在相应的 `Discuz!` 版本中运行。然后在 XML 文件的以下分支中自行更改。 

如您的插件兼容多个版本，请用逗号(,)分隔，如`“X2,X2.5”`（此写法从 `Discuz! X2 R20120329` 后开始支持） 


```
        <item id="Data">
            <item id="plugin">
                    ......
            </item>
            ......
            <item id="version"><![CDATA[兼容性设置]]></item>
            ......
        </item>

```
## 其他论坛数据导入
插件安装时可以直接导入一个或多个论坛数据，这些论坛数据包括表情`(smilies)`、风格`(styles)`的数据。在导出的 XML 文件结尾加上需要导入数据的类型和数据文件名即可，多个文件名用逗号(",")分隔。 


```
            <item id="importfile">
                <item id="smilies"><![CDATA[discuz_smilies_test.xml]]></item>
                <item id="styles"><![CDATA[discuz_styles_test.xml]]></item>
            </item>
        </item>
    </root>

```
## 小提示
如果导出的 `XML` 文件名以 `SC_GBK、SC_UTF8、TC_BIG5、TC_UTF8` 结尾，显示的时候将直接显示为“简体”、“繁体”、“UTF8”等字样。 

更新时间：2012-9-13
