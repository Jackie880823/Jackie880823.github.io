---
layout: post
title: Android Studio 贴士 - 综述#1
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-1](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-1)*

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;注：文中链接皆为国外链接，可能需要翻墙*

&#160;&#160;&#160;&#160;&#160;&#160;&#160;原来我并不能很好地保持承诺，从上一篇开始的新的一系列章节到这一篇，中间竟间隔了近一年*（作者上一篇 “ Android Studion 贴士 & 技巧：漫游”完成于2013年10月，而这篇是在2014年10月）*。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;所以我想让一切重新开始，把在Google+每日更新的帖子在这里重新整理发布来取代这一系列，就如同[Daniel Lew](http://blog.danlew.net/2014/03/30/android-tips-round-up-part-1/)那段时间做的那样。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;在Google+上开始写这一系列以来，也复述了上一节的一些内容。如果你想获取最新的贴士内容，请关注我的[Google+](https://plus.google.com/+PhilippeBreault/)或订阅[Android Developer Tools Community](https://plus.google.com/communities/114791428968349268860)、Pavlos-Petros Tournaris 也将当前所有的贴士都收集到了[github](https://github.com/pavlospt/Android-Studio-Tips-by-Philippe-Breault/wiki)中。如果你想持续跟进我的博客帖子，那就行动起来吧！

##快捷键映射表（Keymaps）

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;`Android Studio`提供了很多不同的快捷键映射表（快捷键对应行为的映射）。你可以在`Settings > Keymap`中看到它。  
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;实际上你并不需要使用到所有的映射表，所以下面
不同系统所选择表的建议也许对你会有用：

* Windows: Defalut
* Linux: Default
* OSX: Mac OSX 10.5+

###高亮所有相同标识

|        OSX       |        Linu       |      windows      |
|------------------|-------------------|-------------------|
| cmd + shift + F7 | ctrl + shift + F7 | ctrl + shift + F7 |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个会在当前文件中的所有相同标识都高亮显示，比部分匹配要简单得多。这样既能明白其作用域又突出相关性。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;你可以能过`Edit → Find → Find Next/Previous`来导航上下切换定位到不同引用位置。

**额外的贴士**

* 选择高亮函数中声明的一个`return`或`throw`也会高亮所有函数中的这些声明。
* 选择高亮类中定论的`extends`或`implements`也会高亮所覆写/实现的函数。
* 选择高亮一个引入所使用这个引入的位置也会高亮。
* 可以使用`ESC`来取消高亮。

![高亮](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/highlight-all-the-things.gif?raw=true)

###类中函数之间移动

|       OSX      |       Linu    |    windows    |
|----------------|---------------|---------------|
| ctrl + up/down | alt + up/down | alt + up/down |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个将会在当前文件移动光标至上/下一个函数或类的名称前。这在你对定们到的函数进行重构和查找引用是会非常有用。

![类中函数之间的移动](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/move-between-methods-and-inner-classes.gif?raw=true)

###弹出文件结构

|    OSX    |    Linu    |   windows  |
|-----------|------------|------------|
| cmd + F12 | ctrl + F12 | ctrl + F12 |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这种主意来自于需要显示浏览当前类的轮廓。最棒的是你可以输入要找查找的函数名来过滤函数。在你知道函数名的情况下查找函数是非常有效。

**额外贴士**

* 可以使用驼峰标识来过滤匹配。例如：输入“`oCr`”就会匹配出“`onCreate`”
* 可以勾选`show anonymous classes`等复选框。这用于像直接跳到匿名内部类`OnclickListener`的`onClick`函数中的这种方式。

![弹出文件结构](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/the-file-structure-popup.gif?raw=true)

###弹出调用层级

|       OSX      |       Linu    |    windows    |
|----------------|---------------|---------------|
| ctrl + alt + h | alt + alt + h | alt + alt + h |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个是向你显示函数声明与调用之间可能的路径！

![弹出调用层级](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/the-call-hierarchy-popup.gif?raw=true)

###快速查看定义

|     OSX     |       Linu       |      windows     |
|-------------|------------------|------------------|
| alt + space | ctrl + shift + i | ctrl + shift + i |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;有没有想过再实现某个函数或类的同时又不想丢失当前的上下文内容？使用这个快捷键查看其中的内容。

![快速查看定义](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/quick-definition-lookup.gif?raw=true)

###展开/关闭代码块

|     OSX     |         Linu       |       windows      |
|-------------|--------------------|--------------------|
|  cmd + +/-  | ctrl + shift + +/- | ctrl + shift + +/- |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个功能的目的是用于隐藏不需要关注的代码片断。最简单的形式就是，隐藏整个代码块（比如：打开新文件忽略显示的类引入列表）。更有趣的是用它可以隐藏简单匿名内部类的样版部分，全其看起来就像是一个`->`表达式。

**额外贴士**

* 你可以在`Preferences → Editor → Code Folding`中设置缺省的折叠习惯。

![展开/关闭代码块](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/collapse-expand-code-block.gif?raw=true)

###书签！

####标识书签

| OSX | Linu | windows |
|-----|------|---------|
|  F3 |  F11 |   F11   |

###标识书签并添加编号

|    OSX   |    Linu    |   windows  |
|----------|------------|------------|
| alt + F3 | ctrl + F11 | ctrl + F11 |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;如果你给书签设置了编号，你可以使用快捷键：`ctrl + <编号>`快速回到书签的位置

####显示书签

|    OSX   |     Linu    |   windows   |
|----------|-------------|-------------|
| cmd + F3 | shift + F11 | shift + F11 |

![显示书签](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/show-bookmarks.gif?raw=true)

###查找行为

|        OSX      |       Linu       |      windows     |
|-----------------|------------------|------------------|
| cmd + shift + a | ctrl + shift + a | ctrl + shift + a |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;你可以使用所知的`Android Studio`的菜单或行为名称来执行这它！这个在你不知道所用命令的快捷键是什么的时候是非常有用的。

**额外贴士**

* 如果这个行为存在与之对应的快捷键，它会显示在这个行为的左边

![查找行为](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/find-actions.gif?raw=true)

###上下移动行

|           OSX         |         Linu          |        windows        |
|-----------------------|-----------------------|-----------------------|
| alt + shift + up/down | alt + shift + up/down | alt + shift + up/down |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;Yeah.这就是上下移动行，就是这么简单粗暴。Enjoy!

![上下移动行](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/move-lines-up-down.gif?raw=true)

###删除行

|       OSX       |   Linu   | windows  |
|-----------------|----------|----------|
| cmd + backspace | ctrl + y | ctrl + y |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;删除当前所在行。

![上下移动行](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-1/delete-line.gif?raw=true)










