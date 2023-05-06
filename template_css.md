[« 返回](?ac=document&page=dev)## Discuz! 的模板机制
[模板风格创建](?ac=document&page=dev_template)|[Discuz!模板解析语法](?ac=document&page=template_coderule)|[模板缓存与CSS缓存](?ac=document&page=template_css)|[内置常用CSS代码分析 ](?ac=document&page=template_sample)## **模板缓存**
-  模板缓存存放：所有的模板缓存均被解析成php文件存放在 ./data/template 中，以 “**数字**_**模板标示符组合**.tpl.php”形式保存 
-  页面缓存刷新原理：当开发者编辑过模板文件之后，Discuz! 模板解析器会匹配**模板htm文件**与**缓存php文件**的最后修改时间，如过模板html文件较新或无缓存文件，则更新或生成缓存，不新，则不采取任何动作 
-  手动删除此目录的缓存不会影响Discuz!系统的整体运行，Discuz! 模板缓存仍然会进行自动生成 

## **CSS缓存**
-  CSS缓存存放：./data/cache/目录中，以 “style_**风格自增编号**_**应用入口关键字**_**所在页面的mod值**.css”形式保存 
-  自建新套系模板文件可以通过创建 ./template/mytest/common/extend_common.css 或 extend_module.css 进行CSS扩展 
    -  其中这两个文件的CSS样式脚本会通过 Discuz! 模板解析将风格常量统一赋值进去并合将CSS脚本复制出来放入 ./template/default/common/common.css 和 module.css 所对应的缓存中去，方便站点运行时引用 


-  extend_module.css 系统解析与缓存存放： 
    -  其中可以使用下面的书写方法： 



```	
/** forum::index,forum::forumdisplay **/
    .mycss {font: {FONTSIZE} {FONT};}
/** end **/

```
1.  上面的写法含义是：针对 forum 的 **index** 和 **forumdisplay** 追加一个自定义的CSS样式 "**mycss**" ，Discuz! 模板解析将会根据 forum::index 的关键词将 mycss 分别追加在“./data/cache/style_2_forum_index.css”和“./data/cache/style_2_forum_forumdisplay.css”中(里面的数字2，根据新增的风格编号而定) 
1.  这样的写法好处就是，不变更默认模板的情况下有效的扩展CSS，并可以很好的进行多站点移植 

  
## **CSS 继承规范**
-  Discuz! X系列产品中 CSS 文件会在缓存时按照以下顺序进行合并： 

1.  template/default/*.css 文件 
1.  当默认模版是非默认模版时，template/模版目录/extend_*.css 文件 或 template/模版目录/*.css 
1.  当某插件启用时，source/plugin/插件目录/template/extend_*.css 文件 

-  因此非默认模版目录中的 CSS 属性将继承默认模版中的 CSS 属性，插件目录中的 CSS 文件将继承前二者的 CSS 属性 
-  CSS 自身的集成顺序为：当 CSS 属性名称相同是，CSS 文件中，写在后面的替换前面的代码 

更新时间：2012-5-3

