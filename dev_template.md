[« 返回](?ac=document&page=dev)## Discuz! 的模板机制
[模板风格创建](?ac=document&page=dev_template)|[Discuz!模板解析语法](?ac=document&page=template_coderule)|[模板缓存与CSS缓存](?ac=document&page=template_css)|[内置常用CSS代码分析 ](?ac=document&page=template_sample)## 目录
- [1开启模板开发者模式](?ac=document&page=dev_template#.E6.A8.A1.E6.9D.BF.E5.A5.97.E7.B3.BB.E4.B8.8E.E9.A3.8E.E6.A0.BC.E5.8C.BA.E5.88.AB.DEV)
- [2模板套系与风格区别](?ac=document&page=dev_template#.E6.A8.A1.E6.9D.BF.E5.A5.97.E7.B3.BB.E4.B8.8E.E9.A3.8E.E6.A0.BC.E5.8C.BA.E5.88.AB)
- [3模板创建（新教程）](?ac=document&page=dev_template#.E6.89.A9.E5.B1.95.E6.A8.A1.E6.9D.BF.E5.88.9B.E5.BB.BA.NEW)
- [4模板创建（旧教程）](?ac=document&page=dev_template#.E6.89.A9.E5.B1.95.E6.A8.A1.E6.9D.BF.E5.88.9B.E5.BB.BA)
    - [4.1创建模板套系](?ac=document&page=dev_template#.E5.88.9B.E5.BB.BA.E6.A8.A1.E6.9D.BF.E5.A5.97.E7.B3.BB)
    - [4.1.1实例](?ac=document&page=dev_template#.E5.AE.9E.E4.BE.8B)



    - [4.2后台风格管理](?ac=document&page=dev_template#.E5.90.8E.E5.8F.B0.E9.A3.8E.E6.A0.BC.E7.AE.A1.E7.90.86)
    - [4.2.1新建风格](?ac=document&page=dev_template#.E6.96.B0.E5.BB.BA.E9.A3.8E.E6.A0.BC)

    - [4.2.2风格管理编辑页面中重点风格常量介绍](?ac=document&page=dev_template#.E9.A3.8E.E6.A0.BC.E7.AE.A1.E7.90.86.E7.BC.96.E8.BE.91.E9.A1.B5.E9.9D.A2.E4.B8.AD.E9.87.8D.E7.82.B9.E9.A3.8E.E6.A0.BC.E5.B8.B8.E9.87.8F.E4.BB.8B.E7.BB.8D)





  
## 开启模板开发者模式
开始设计一个新模板，请首先打开 config/config_global.php 文件，在文件结尾添加以下代码开启模板开发者模式。 

```	$_config['plugindeveloper'] = 1;
```
  


## 模板套系与风格区别
-  模板套系：统一的一类模板，集中放置并打包的系列。 
-  模板风格：使用某个模板套系代码，仅改变其中变量设置的一个方案。 
-  （默认一个模板套系下就一个风格方案，通过“复制”功能，可以复制出不同的风格，进行不同的设置，比如改变logo设置） 

  
## **模板创建（基于最新版的教程）**
-  首先进入**后台 - 模板 - 设计新模板**
-  填写模板名称(name)，例如设置为“我的模板”
-  填写版权信息(copyright)，根据自己的情况填写版权信息
-  填写惟一标识符(identifier)，惟一标识符用于生成模板目录和后续提交模板到应用中心，不可与现有模板重复，命名规则限制与 PHP 变量命名相同，建议一次性将此配置设置好，否则可能涉及到很多代码方面的变更，增加编码的麻烦。请注意：惟一标识符请不要设置的过短，或使用有可能与其他模板重复的命名。会自动创建模板目录：template/标识符/。
-  初始化模板设置，使用已经存在的模板设置初始化本模板，或创建空白设置的模板
-  其他细节参考下边老教程的说明



  
## 模板创建（老版本dz的教程）
### 创建模板套系
-  首先进入**后台 - 界面 - 模板管理**，扩展制作模板时需要创建一个专属套系用来后期修改 
    -  基于“模板套系”可以扩展针对 ./template/default/ 目录中对的模板文件 

    -  创建套系的原则是不破坏原有模板基础上进行全新的扩展模板设计 



#### 实例
1.  在站点根目录 ./template/中创建新的目录如" ./template/*mytest*" 
1.  在 mytest 目录中创建必要子目录与文件如： 

```	
./template/mytest/common/
./template/mytext/common/extend_common.css
./template/mytext/common/extend_module.css

```
-  其中common目录为公共模板目录，其内部新建的**extend_common.css**、**extend_module.css**为扩展型CSS文件，它们可以在./template/default/common/common.css的和module.css的基础上进行CSS代码的覆盖性扩展 
-  如果需要替换论坛首页模板，可以新建 ./template/mytext/forum/discuz，或复制 ./template/default 中的对应文件放在 mytext 对应目录，以在缓存生成时覆盖原有模板缓存，达到修改模板而不破坏原生模板的目的 

### 后台风格管理
-  进入**后台 - 界面 - 风格管理**
    -  “风格管理”可以对已有风格进行风格变量的编辑，也可以基于前面创建的“模板套系”来全新开辟新的风格 



#### 新建风格
-  后台风格管理中，可以通过**新增**和**复制**原有风格进行新建风格的操作 
-  新建风格之后，需要编辑它，调整里面的“匹配模板”为上面创建的新套系即可 

#### 风格管理编辑页面中重点风格常量介绍
-  匹配模板：对应的模板套系 
-  扩展配色：此风格基础上可用于用户切换配色方案的扩展，它对应 ./template/mytest/style/ 目录中的样式文件。全新创建时应在./template/mytest/style/目录中建立如t1/style.css之后方能生效 
-  默认配色：指定站点访问时，用户首先看到的配色方案 
-  默认表情分类：对应**后台 - 界面 - 表情管理**中所启用的表情 
-  界面基础图片目录：可用于更改模板图片目录，在CSS文件中使用**{IMGDIR}**的常量进行输出，**在Discuz! X2版本之后的模板中需要使用$_G['style']['imgdir']**
-  扩展图片目录：用来更改扩展图片目录，在CSS文件中使用**{STYLEIMGDIR}**的常量进行输出，**在Discuz! X2版本之后的模板中需要使用$_G['style']['styleimgdir']**
-  其他风格常量：以上没有提到风格常量，均可以在后台取得以花括号框选的常量用以在CSS文件中使用（X2以后的模板中均需要$_G['style']中对应的数组键值），涉及到CSS样式的动态变更，可以在修改对应设置如：正常字体大小 {FONTSIZE}:12px/1.5，则直接修改程序运行中CSS缓存中的值 
-  自定义模板变量 - 新增：可以根据扩展需求，针对个性化的CSS进行全局的定义 

更新时间：2012-5-3

