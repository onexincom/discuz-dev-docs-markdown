# 文件包说明
## 1、版本及文件包分类
1. **分支版本**:  
 分支版本是指您应用的多个共存版本，如“免费版”、“收费版”、“`**** GBK`”、“`**** UTF8`”、“`**** PHP≤5.2`”、“`**** PHP≥5.3`”。文件包结构请阅读下方的“3、文件包结构”。分支版本的文件包将通过站点的 `Discuz!` 管理中心在线安装。
1. **扩展组件**:  
 扩展组件是指您应用的部分文件，其中不能包含应用的安装脚本(如插件和模板的安装 XML)，通过组件可以让您的应用实现模块化发布，如提供“免费版 + 收费模块”、“试用版 + 正式版模块”。文件包结构请阅读下方的“3、文件包结构”。扩展组件的文件包将通过站点的 `Discuz!` 管理中心在线安装，但只有安装过分支版本的站点才可安装扩展组件。
1. **下载资料**:  
 下载资料是指您可提供给站长直接下载的文件，其中不能包含应用的源码，通过资料可以向站长提供说明书、图片源文件、素材、DIY 配置、分类信息配置等文件。文件包结构不限制。下载资料的文件包站长可直接下载。

## 2、基本要求及安全规范
请详阅 [《`Discuz!` 应用中心应用审核规范》](?ac=document&page=audit)、 [《`Discuz!` 应用中心插件审核规范》](?ac=document&page=audit_plugin)、 [《Discuz! Lite应用审核规范》](?ac=document&page=audit_dzl)

## 3、文件包结构
[以下内容仅限分支版本和扩展组件文件包]

1. 插件类型的应用基准目录为 `/source/plugin/`（插件目录）  
 模板类型的应用基准目录为 `/template/` （模板目录）  
 扩展类型的应用基准目录为 `/` （根目录） 
1. 压缩包中的根文件夹有且只有一个文件夹，文件夹名和插件标识（模板标识、扩展标识）相同，在此文件夹中存放应用的全部文件。简单来说，应用的打包您只需对基准目录下的您的应用目录点击鼠标右键选择压缩即可。
1. 对于上传的插件，平台将提供自动编码转换服务。您只需在上传的压缩包中包含“简体UTF-8”或“简体GBK”版本的 `discuz_plugin_(identifer).xml` 文件，那么在插件审核通过并上线后，平台会自动对下载的安装包中生成以下文件： 
    - `discuz_plugin_(identifer)_SC_GBK.xml` (简体 GBK)

    - `discuz_plugin_(identifer)_SC_UTF8.xml` (简体 UTF8)

    - `discuz_plugin_(identifer)_TC_UTF8.xml` (繁体 UTF8)

    - `discuz_plugin_(identifer)_TC_BIG5.xml` (繁体 BIG5)



如果您不希望平台为您转换编码，请不要在上传的压缩包中包含 `discuz_plugin_(identifer).xml` 文件，直接包含带编码后缀的 `discuz_plugin_(identifer)_SC_GBK.xml` 文件即可。

1. 扩展组件类的文件包和分支版本类的文件包结构相同，唯一区别就是禁止携带插件或风格的安装脚本 xml 文件。
1. 下载资料类的文件包结构不限制，但不允许携带应用源码。

## [4、动态变量](#var)
上传的文件中可通过加入以下动态变量，此变量将在站长安装应用时自动替换成相应的值。 变量标识（系统变量） 含义  
`{ADDONVAR:SN}` 序列号，应用版本和网站绑定的唯一识别码  
`{ADDONVAR:RevisionID}` 应用版本的 ID  
`{ADDONVAR:RevisionDateline}` 应用版本的发布时间  
`{ADDONVAR:SiteUrl}` 站点URL  
`{ADDONVAR:ClientUrl}` 客户端URL  
`{ADDONVAR:SiteID}` 站点 ID  
`{ADDONVAR:QQID}` 站点绑定的 QQID（非QQ号，只有绑定的站点有值）  
`{ADDONVAR:*MyKey*}` 自定义动态变量（添加方法见下面的“应用发布配置文件”）  
`{ADDONVAR:MD5(***)}` 以上值的MD5，自定义组合（\*\*\* 为以上值的名称，用逗号分隔） 

## 5、应用发布配置文件
应用发布配置文件的文件名为 config.xml，位于压缩包中的根目录，此文件非必需。配置文件的格式如下：


```php
                <?xml version="1.0" encoding="ISO-8859-1"?>
                <root>
                    <item id="Title"><![CDATA[Discuz! Addon Config]]></item>
                    <item id="Data">
                        <item id="设置项1">设置项1内容 ...</item>
                        <item id="设置项2">设置项2内容 ...</item>
                        ...
                    </item>
                </root>

```
设置项有如下内容： 

**var**: 自定义动态变量  
 用于扩展自定义动态变量，即 {ADDONVAR: *MyKey*} 的项目，格式如下： 


```php
                <item id="var">
                    <item id="MyKey1"><![CDATA[MyValue1]]></item>
                    <item id="MyKey2"><![CDATA[MyValue2]]></item>
                    ...</item>
```
设置项变量含义  
 MyKey 变量名必须由字母、数字及下划线组成，且不能使用系统变量  
`MyValue` 变量返回值内容不限制。如果返回值为一个网址，表示变量返回值为 `API` 返回的内容，`API` 将在每次应用安装时被调用。调用时，所有系统变量将通过 `POST` 方式提交给 `API`。(返回值为网址的权限需要申请，请与民审联系) 

### [**language**: 附属语言包 `New!`](#lang)
请求开放平台使用自动编码转换服务转换指定的 PHP 脚本，只负责转换一个 PHP 脚本。脚本将在应用审核通过并上线后被删除，并会自动对此生成以下文件： - `language.php` (指定的 PHP 脚本，审核后将被删除)

- `language.SC_GBK.php` (简体 GBK)
- `language.SC_UTF8.php` (简体 UTF8)
- `language.TC_UTF8.php` (繁体 UTF8)
- `language.TC_BIG5.php` (繁体 BIG5)

格式如下： 


```php
<item id="language"><![CDATA[附属语言包 PHP 脚本文件名]]></item>
```
友情提示：`Discuz! X2.5` 开始可用 `currentlang()` 函数获取网站 `Discuz!` 的语言编码，如下： 


```php
$language = 'language.'.currentlang().'.php';
```
## 6、范例
如有不明白的开发者可以 [下载范例文件包](https://addon.dismall.com/resource/vartest.zip)或者 [安装“应用配置文件演示”应用](https://addon.dismall.com/?@vartest.plugin)，以了解您需要上传给开放平台的文件包结构。 

