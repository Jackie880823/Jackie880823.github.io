---
layout: post
title: Android Studio 贴士 - 综述#2
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-2](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-2)*

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;注：文中链接皆为国外链接，可能需要翻墙*

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这篇是我发表在[Google+](https://plus.google.com/+PhilippeBreault/)上有关`Android Studio 贴士`综述的第二部分。你可以点击（[原文](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-1/) 或 [译文](http://jackie880823.github.io/2015/12/26/Android%20Studio%20Tips%20Of%20the%20Day%20-%20Roundup%20%231/)）查看上一部分的内容。


##快捷键映射表（Keymaps）

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;`Android Studio`提供了很多不同的快捷键映射表（快捷键对应行为的映射）。你可以在`Settings > Keymap`中看到它。
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;实际上你并不需要使用到所有的映射表，所以下面
不同系统所选择表的建议也许对你会有用：

* Windows: Defalut
* Linux: Default
* OSX: Mac OSX 10.5+

###行复制

|   OSX   |   Linu   | windows  |
|---------|----------|----------|
| cmd + d | ctrl + d | ctrl + d |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;顾名思义：这个快捷键会将当前行复制、粘贴至下一行并且不干扰剪贴板的内容。这个当你快速地在行中移动时会非常有用。

![行复制](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/11-duplicate_lines.gif?raw=true)

###扩展/缩小选择

|      OSX      |         Linu         |       windows        |
|---------------|----------------------|----------------------|
| alt + up/down | ctrl + w/(shift + w) | ctrl + w/(shift + w) |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个会扩展当前位置的上下文区域。例如：选择当前的变量、声明、函数等。

![扩展/缩小选择](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/12-expand_shrink_selection.gif?raw=true)

###包围代码

|      OSX      |      Linu      |    windows     |
|---------------|----------------|----------------|
| cmd + alt + t | ctrl + alt + t | ctrl + alt + t |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;常用于包裹代码块到其它作用域中。通常是：`if、loop、try-catch或runnable`等组件.

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;如果没有选择代码，会包裹光标所在行。

![包围代码](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/13-surround_with.gif?raw=true)

###近期文档

|   OSX   |   Linu   | windows  |
|---------|----------|----------|
| cmd + e | ctrl + e | ctrl + e |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;用这个快捷键，你可能得到可检索的近期打开过的文档列表。

![近期文档](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/14-recents.gif?raw=ture)

###现场样板

|   OSX   |   Linu   | windows  |
|---------|----------|----------|
| cmd + j | ctrl + j | ctrl + j |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;现场样板是一种快速插入代码块的方式，有趣的是现场样板可以智能地实现参数并引导你以参数形式插入代码。

**额外贴士**

* 如果你知道它的缩写就可以不用这个快捷键，只需要输入正确的缩写再用`Tab`键确认即可。

![现场样板](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/15-live_templates.gif?raw=true)

###移动函数

|         OSX         |          Linu          |         windows        |
|---------------------|------------------------|------------------------|
| cmd + alt + up/down | ctrl + shift + up/down | ctrl + shift + up/down |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个快捷键类似`移动行`，但这是个是用在移动函数上，你可以上下移动函数不需要使用复制-粘贴。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这里的`移动函数`的实际意义是移动任何类型的组件。比如：移动代码块到内部类。

![现场样板](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/15-movemethods.gif?raw=true)


###补全组件

|         OSX         |        Linu          |       windows        |
|---------------------|----------------------|----------------------|
| cmd + shift + enter | ctrl + shift + enter | ctrl + shift + enter |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;用于补全组件缺失的代码，通常用于以下几种情况：

*  如果你没有在行尾添加分号，在行尾添加分号；
*  在`if、while或for`圆括号后添加花括号；
*  在函数声明后添加花括号。

**额外贴士**

* 如果组件是已编定完整，就会跳入下一行，即使光标不在当前行的最后一个字符的位置。

![补全组件](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/16-completestatement.gif?raw=true)

###最后编辑的位置

|           OSX           |          Linu            |         windows          |
|-------------------------|--------------------------|--------------------------|
| cmd + shift + backspace | ctrl + shift + backspace | ctrl + shift + backspace |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个会引导你跳至你最后一次编辑的位置。这个区别于导航栏中的箭头工具，在这个工具包含了你编辑和打开浏览的历史。

![最后编辑的位置](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/17-navigate-previous-changes.gif?raw=true)

###合并行

|        OSX       |      Linu        |      windows     |
|------------------|------------------|------------------|
| ctrl + shift + j | ctrl + shift + j | ctrl + shift + j |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个不仅仅是在模仿删除！它同时还保留了以下规则：

* 合并两个行注释删除无效的`//`；
* 合并多个字符串会删除之间的`+`号和双引号；
* 连接作用域和作业

**额外贴士**

* 如果你选择了多行字符，将会把这些字符合并成一行。

![合并行](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/18-joinlines.gif?raw=true)

###选择进入

|    OSX   |  Linu    |  windows |
|----------|----------|----------|
| alt + f1 | alt + f1 | alt + f1 |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;选择当前位置所在的位置，依本人遇见在打开项目结构和和浏览文件中是最有用的快捷键了。提示 每个行为的前缀的编号和文字都能使用你快速地执行这个操作。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;通常，在Mac电脑上时我都会使用`Alt + F1`打开项目视图和用`Alt + F1 + 8`在文件夹中显示这个文件。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;你可以从文件或者项目视图中直接调用这个快捷键。

![选择进入](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/19-select-in.gif?raw=true)

###展开/移除包围

|          OSX         |        Linu           |         windows       |
|----------------------|-----------------------|-----------------------|
| cmd + shift + delete | ctrl + shift + delete | ctrl + shift + delete |

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个可以用于移除一个`if、while、try/catch甚至runnable`等组件。直接与**包围代码**这个快捷键相对。

![展开移除包围](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-2/20-unwrap.gif?raw=true)














