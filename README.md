# 一、代码规范
### 1、样式表编码
样式文件必须写上 @charset 规则，并且一定要在样式文件的第一行首个字符位置开始写，编码名用 “UTF-8”。
```
@charset "UTF-8";
```
### 2、代码全小写
样式选择器，属性名，属性值关键字全部使用小写字母书写。
### 3、使用类选择器，杜绝使用ID选择器定义样式
ID在一个页面中的唯一性导致了如果以ID为选择器来写CSS，就无法重用。   
团队约定：  
（1）重构只能使用和控制类名来定义样式，不允许增删改id。  
（2）前端不允许增删改class。如果需要添加类名来开发交互效果，则类名规范为”js-xxx“。  
```
<!-- 重构通过go-top定义样式，前端通过js-go-top定义统一的方法 -->
<a href="javascript:;" class="go-top js-go-top"></a>
```
# 二、class命名规范
### 1、以字母开头
必须以字母开头命名选择器，这样可保证在所有浏览器下都能兼容
不允许单个字母的类选择器出现
不允许命名带有广告等英文的单词，例如ad,adv,adver,advertising，已防止该模块被浏览器当成垃圾广告过滤掉
### 2、全小写，并使用 ' - ' 连字符  
下划线 ' _ ' 禁止出现在class命名中，统一使用'-'连字符  
禁止驼峰式命名  
```
/* Bad CSS */
.mod_index{ ... }
.modIndex{ ... }

/* Good CSS */
.mod-index{ ... }
```
### 3、命名应简约而不失语义
避免过度简写，.ico足够表示这是一个图标，而.i不代表任何意思  
使用有意义的名称，使用结构化或者作用目标相关的，而不是抽象的名称  
### 4、统一语义理解和命名
布局：  

语义 | 命名
---|---
头部 | header
尾部 | footer
主栏 | main
侧栏 | side
盒容器 | wrap/box
模块：  
语义 | 命名
---|---
导航 | nav
子导航 | subnav
面包屑 | crumb
菜单 | menu
选项卡 | tab
标题区 | title
内容区 | body
列表 | list
表格 | table
表单 | form
热点 | hot
排行 | top
登录 | login
标志 | logo
搜索 | search
幻灯 | slide
提示 | tips
帮助 | help
新闻 | news
下载 | download
注册 | regist
版权 | copyright
结果 | result
按钮 | button
输入 | input
状态：  
语义 | 命名
---|---
选中 | selected
当前 | current
打开 | open
关闭 | close
出错 | error
不可用 | disable
### 5、可复用公共模块命名
全局公共模块以 mod-xxx 命名，定义在全局公共样式文件中  
栏目级公共模块以 栏目名-mod-xxx 命名，定义在栏目公共样式文件中  
页面级模块以 栏目名-页面名-xxx 命名，定义在页面私有样式文件中  
```
/* 全局头部定义 */
.mod-header{
    ...
}

/* 注册流程表单定义 */
.reg-mod-form{
    ...
}

/* 注册结果页广告位定义 */
.reg-result-broad{
    ...
}
```
# 三、代码格式
### 1、使用4个空格做为缩进
保证在各种环境下显示一致。在sublime中的设置：
```
/* The number of spaces a tab is considered equal to */
    "tab_size": 4,

/* Set to true to insert spaces when tab is pressed */
    "translate_tabs_to_spaces": true,
```
###2、每条声明应该只占用一行来保证错误报告更加准确  
在一个声明块中只包含一条声明的情况下，为了易读性和快速编辑可以考虑移除其中的换行。所有包含多条声明的声明块应该分为多行。
```
/* Bad CSS */
.selector{padding: 15px; margin: 0px 0px 15px; }

/* Good CSS */
.selector{
    padding: 15px;
    margin: 0px 0px 15px;
}
```
### 3、使用组合选择器时，保持每个独立的选择器占用一行  
在一个声明块中只包含一条声明的情况下，为了易读性和快速编辑可以考虑移除其中的换行。所有包含多条声明的声明块应该分为多行。
```
/* Bad CSS */
.selector,.selector-a,.selector-b{padding: 15px; margin: 0px 0px 15px; }

/* Good CSS */
.selector,
.selector-a,
.selector-b{
    padding: 15px;
    margin: 0px 0px 15px;
}
```
### 4、所有声明应该以分号结尾  
通常在大括号结束前的值可以省略分号，但是这样做会对修改、添加和维护工作带来不必要的失误和麻烦。   
左括号与类名之间一个空格，冒号与属性值之间一个空格。
```
/* Bad CSS */
.fql{
    width:100%;
}

/* Good CSS */
.fql {
    width: 100%;
}
```
### 5、逗号分隔的取值，都应该在逗号之后增加一个空格
比如说box-shadow
```
/* Bad CSS */
box-shadow: 0 1px 2px #ccc,inset 0 1px 0 #fff;

/* Good CSS  */
box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
```
### 6、颜色值 rgb() rgba() hsl() hsla() rect() 中不需有空格，且取值不要带有不必要的 0
```
/* Bad CSS */
.fql {
    color: rgba( 255, 255, 255, 0.5 );
}

/* Good CSS  */
.fql {
    color: rgba(255,255,255,.5);
}
```
### 7、不要为 0 指明单位
比如使用 margin: 0; 而不是 margin: 0px;。
### 8、使用单引号
省略url引用中的引号，其他需要引号的地方使用单引号。
```
.m-box {
     background: url (bg.png);
     font-family: 'Hiragino Sans GB';
}
.m-box:after {
     content: '.' ;
}
```
### 9、使用16进制表示颜色值,并使用小写字母以及尽量缩写
省略url引用中的引号，其他需要引号的地方使用单引号。
```
.m-box {
    color: #f00 ;
    background: rgba(0,0,0,.5);
}
```
### 10、不要以没有语义的标签作为选择器
这会造成大面积污染，除非你可以断定现在或将来你的这个选择器不会污染其他同类
```
/* Good CSS */
.fql {}
.fql li {}
.fql li p {}

/* Bad CSS */
.fql div { ... }
```
### 11、不要将选择器写的过于冗长
这会额外增加文件大小并且限制了太小范围的选择器，使树形结构过于严格应用范围过于局限，建议3-4个长度之内写完。
```
/* Bad CSS */
.m-xxx .class .class .class .class{}
```
### 12、统一Hack方法
统一使用 “ * ” 和 “ _ ” 分别对IE7和6进行Hack。如下代码所示：
```
.m-list{
    color: #000;
    *color: #888;
    _color: #fff ;
}
```
### 13、建议属性声明以下面的顺序分组处理
布局定位属性：display / position / float / clear / visibility / overflow  
自身属性：width / height / margin / padding / border / background  
文本属性：color / font / text-decoration / text-align / vertical-align / white- space / break-word  
其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …  
```
.fql {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    -o-border-radius: 10px;
    -ms-border-radius: 10px;
    border-radius: 10px;
}
```
### 14、坚持限制属性取值简写的使用，属性简写需要你必须显式设置所有取值
缩写值可以减少CSS文件大小，并增加可读性和可维护性。  
但大多数情况下，我们并不需要设置属性简写中包含的所有值。例如，HTML 头部只设置上下的 margin，所以如果需要，只设置这两个值。过度使用属性简写往往会导致更混乱的代码，其中包含不必要的重写和意想不到的副作用。  
```
/* 比如我们用下面这个样式来让某个定宽的容器水平居中，我们要的只是left和right，
 * 而top和bottom不是这个样式要关心的（如果设置了反倒会影响其他样式在这个容器上的使用），
 * 所以这时我们就不需要缩写
 */
.f-mgha {
    margin-left: auto ;
    margin-right: auto ;
}

/* 比如下面这个模块的样式设置，我们确实需要设置padding的所有项，于是我们就可以采用缩写 */
.m-link {padding: 6px 12px ;}
```
### 15、私有在前，标准在后
先写带有浏览器私有标志的，后写W3C标准的。
```
.m-box {
    -webkit-box-shadow: 0 0 0 #000 ;
    -moz-box-shadow: 0 0 0 #000 ;
    box-shadow: 0 0 0 #000 ;
}
```
### 16、涉及公共模块的样式修改，不能简单地使用原类名重定义
如果是栏目级的重定义，可以使用扩展类的方式重定义在栏目级公共样式中  
如果是页面私有的重定义，可以通过父级类名来控制，重定义在页面私有样式中  
如.mod-header是全局的头部，你需要重定义一下背景颜色：  
```
/* 所有注册栏目页面 */
.reg-mod-header {
    background-color: #000;
}

/* 当前页面 */
.reg-index .mod-header {
    background-color: #f00;
}
```
# 四、注释规范
注释以字符 /* 开始，以字符 */ 结束  
注释不能嵌套
### 1、单行注释
注释方法：注释内容第一个字符和最后一个字符都是一个空格字符，单独占一行，行与行之间相隔一行。  
使用场景：  
（1）对某个选择器的解释，写在被注释对象的上一行。  
（2）对属性及值的注释，特别需要开发人员关注的，写于分号后。  
```
/* 商品列表通用样式 */
.m-list li {
    height: 20px;
    line-height: 20px;  /* 需要设置行高来保证各个浏览器展现一致 */
}

/* 商品列表通用样式-角标 */
.m-list li em {color: #666;}
```
### 2、模块注释
注释方法：注释内容第一个字符和最后一个字符都是一个空格字符，/* 与 模块信息描述占一行，多个横线分隔符-与*/占一行，行与行之间相隔两行   
使用场景：  
（1）css注释应该对应到html结构上的各个模块。  
（2）可复用的公共代码块一定要注释。
```
/* PC页面公共头部
---------------------------------------------------------------- */
.mod-header {}

/* PC页面公共底部
---------------------------------------------------------------- */
.mod-footer {}
```
### 3、文件信息注释
注释方法：在样式文件编码声明 @charset 语句下面注明页面名称、作者、创建日期等信息。 
使用场景： 
（1）每个css文件均可添加。
此注释可选。
```
@charset "UTF-8";
/**
 * @desc File Info
 * @author Author Name
 * @date 2015-10-10
 */
 ```