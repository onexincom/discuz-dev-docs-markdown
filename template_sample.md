
# 内置常用CSS代码分析
## **CSS IE多版本下兼容`HACK`写法**

```css
所有 IE浏览器适用： .ie_all .foo { ... }
IE6 专用：     .ie6 .foo { ... }
IE7 专用：     .ie7 .foo { ... }
IE8 专用：     .ie8 .foo { ... }

```
## **CSS书写规范**
\* 属性写在一行内，属性之间、属性名和值之间以及属性与 `{}` 之间须有空格，例如：`.class { width: 400px; height: 300px; }`

\* 属性的书写顺序：

2.1. 针对特殊浏览器的属性，应写在标准属性之前，例如：`-webkit-box-shadow:; -moz-box-shadow:; box-shaow:;`

2.2. 按照元素模型由外及内，由整体到细节书写，大致分为五组：

2.2.1. 位置：`position,left,right,float`

2.2.2. 盒模型属性：`display,margin,padding,width,height`

2.2.3. 边框与背景：`border,background`

2.2.4. 段落与文本：`line-height,text-indent,font,color,text-decoration,...`

2.2.5. 其他属性：`overflow,cursor,visibility,...`

\* 谨慎添加新的选择符规则，尤其不可滥用 `id` ，尽可能继承和复用已有样式 

\* 选择符、属性、值均用小写（格式的颜色值除外），缩写的选择符名称须说明缩写前的全称，例如 `.cl -> Clearfix`

\* 勿使用冗余低效的 `CSS` 写法，例如：`ul li a span { ... }`

\* 慎用 `!important`

\* 建议使用在 `class/id` 名称中的词语

7.1. 表示状态：`a->active`

7.2. 表示结构：`h->header,c->content,f->footer`

7.3. 表示区域：`mn->main,sd->side,nv-navigation,mu->menu`

7.4. 表示样式：`l-list,tab,p_pop`

## **常用CSS**
- 左浮动、右浮动 


```css
.z { float: left; }
.y { float: right; }
```
- 因为左右浮动造成的父级浮动溢出，及使用方法 


```html
.cl:after { content: "."; display: block; height: 0; clear: both; visibility: hidden; } .cl { zoom: 1; }

<div class="cl">
    <div class="z"></div>
</div>

```
- 大标题字体 


```css
.wx, .ph { font-family: "Microsoft YaHei", "Hiragino Sans GB", STHeiti, Tahoma, SimHei, sans-serif; font-weight: 100; }
```
- 行内分割竖线 


```css
.pipe { margin: 0 5px; color: #CCC; }
```
- 文字字体大小 


```css
.xs0 { font-family: {SMFONT}; font-size: {SMFONTSIZE}; -webkit-text-size-adjust: none; }
.xs1 { font-size: 12px !important; }
.xs2 { font-size: 14px !important; }
.xs3 { font-size: 16px !important; }

```
- 灰色文字 


```css
.xg1, .xg1 a { color: {LIGHTTEXT} !important; }
.xg1 .xi2 { color: {HIGHLIGHTLINK} !important; }
.xg2 { color: {MIDTEXT}; }
```
- 高亮文字，1为橙色，2为蓝色 


```css
.xi1, .onerror { color: {NOTICETEXT}; }
.xi2, .xi2 a, .xi3 a { color: {HIGHLIGHTLINK} ; }

```
- 文字粗体 


```css
.xw0 { font-weight: 400; }
.xw1 { font-weight: 700; }
```
- 层下边线 


```css
.bbda { border-bottom: 1px dashed {COMMONBORDER}; }
.bbs { border-bottom: 1px solid {COMMONBORDER} !important; }
```
- 去除边框 


```css
.bw0 { border: none !important; }
.bw0_all, .bw0_all th, .bw0_all td { border: none !important; }

```
- 去除背景 


```css
.bg0_c { background-color: transparent !important; }
.bg0_i { background-image: none !important; }
.bg0_all { background: none !important; }

```
- 外边距样式 


```css
.mtn { margin-top: 5px !important; }
.mbn { margin-bottom: 5px !important; }
.mtm { margin-top: 10px !important; }
.mbm { margin-bottom: 10px !important; }
.mtw { margin-top: 20px !important; }
.mbw { margin-bottom: 20px !important; }

```
- 内边距样式 


```css
.ptn { padding-top: 5px !important; }
.pbn { padding-bottom: 5px !important; }
.ptm { padding-top: 10px !important; }
.pbm { padding-bottom: 10px !important; }
.ptw { padding-top: 20px !important; }
.pbw { padding-bottom: 20px !important; }

```
更新时间：2012-5-3

