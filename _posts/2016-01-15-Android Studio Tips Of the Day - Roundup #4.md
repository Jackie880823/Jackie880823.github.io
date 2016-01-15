---
layout: post
title: Android Studio 贴士 - 综述#4
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-4](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-4)*

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;注：文中链接皆为国外链接，可能需要翻墙*

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这篇是我发表在[Google+](https://plus.google.com/+PhilippeBreault/)上有关`Android Studio 贴士`综述的第二部分。你可以点击（[原文](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-1/) 或 [译文](http://jackie880823.github.io/2015/12/26/Android%20Studio%20Tips%20Of%20the%20Day%20-%20Roundup%20%231/)）查看上一部分的内容。


#**快捷键映射表（Keymaps）**

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;`Android Studio`提供了很多不同的快捷键映射表（快捷键对应行为的映射）。你可以在`Settings > Keymap`中看到它。  
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;实际上你并不需要使用到所有的映射表，所以下面
不同系统所选择表的建议也许对你会有用：

* Windows: Defalut
* Linux: Default
* OSX: Mac OSX 10.5+

---

#**分析数据来源**

![Analyze](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/31-analyzedataflow.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这会向你显示选中的变量、参数或作用域的获取路径。这在你进入到一断陌生的代码并想弄清楚参数的来源时会非常有用。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;也有一个与之相反的操作叫`“Analyze Data Flow from Here”`,这会向你显示你选中的变量、参数、作用域、或返回值的最终去向。

**快捷方式：** 这个没有快捷键

* 菜单： Analyze → Analyze Data Flow to Here
* 查找行为：Analyze Data Flow to Here

---

#**高超的多文本选择**

![Sublime Text Multi Selection](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/32-multiselection.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这条装逼专用！
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这会在你当前选择和下一个选择的文本中添加都添加游标。这意味着你可以在一个文件有多个编辑游标！并同时在这些游标上编辑。

**快捷方式**

|    OSX   |   Linu  | windows |
|----------|---------|---------|
| Ctrl + G | Alt + J | Alt + J |

---

#**选择列**

![Sublime Text Multi Selection](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/33-columnselection.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;列选择，别名也叫块选择。确切的说就是，当你向下选择时它不会包裹行尾。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这也会在你选择的块中有的每一行有一个游标用来编辑。

**快捷方式**
* 鼠标： Alt + 拖拽鼠标

|    OSX   |   Linu  | windows |
|----------|---------|---------|
| Ctrl + Shift + 8 | Shift + Alt + Insert | Shift + Alt + Insert |

---

#**缀词实现**

![Postfix Completion](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/33-postfixcompletion.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这条的词义不是很明确但用途强大。这节省大量的代码敲写就可以包裹你的当前声明。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;比如：遍历列表，你敲写“myList.for”后敲击`Tab`键就会给你生成一个for循环。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;在你的声明后面添加一个点会得到一个列表来显示你可以对空上声明做到的所有功能选项。

**个人爱用的一些选项**

* .for(遍历)
* .format(包裹字符在String.format()中)
* .cast（包裹声明到cast中）

---

#**与粘贴板比较**

![Compare With Clipboard](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/34-comparewithclipboard.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;将当前选中的内容与粘贴板中的内容进行比较。

**快捷方式**

* 鼠标： 右击选中的的内容然后选择`Compare With Clipboard`
* 查找行为：compare with clipboard

---

#**停止进程**

![Stop Process](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/35-stoprocess.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;停止当前正在执行的任务，如果有多个任务的话用列表显示当前可以停止的任务。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;可完美地使用在停止调试或中止编译上。

**快捷方式**

|    OSX   |    Linu   |  windows  |
|----------|-----------|-----------|
| Cmd + F2 | Ctrl + F2 | Ctrl + F2 |

---

#**显示执行点**

![Show Execution Point](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/36-executionpoint.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这会将光标返回到你正在调度的位置。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;使用在以下情况：

* 中断的位置
* 开始查找然后进入了其它文件中
* 调用这个快捷键可以返回到你正在一步一步的调试会话的地方

**快捷方式** （适用在调试阶段）

|     OSX   |    Linu   |  windows  |
|-----------|-----------|-----------|
| Alt + F10 | Alt + F10 | Alt + F10 |

---

#**弹出版本控制（VCS）操作选项**

![VCS Operations Popup](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/37-vcspopup.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个会显示最常用的版本控制操作项。如果你的项目没有在git或其它管理系统中，它了至少会显示一个Android Studio维护本地历史记录。

**快捷方式**

|    OSX   |   Linu  | windows |
|----------|---------|---------|
| Ctrl + V | Alt + ' | Alt + ' |

---

#**分支（git）比较**

![Compare With Branch](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-4/38-comparewithbranch.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;假设你的项目用git管理，你可以将当前的文件和目录与其它分支进行比较。这在查看你的分支与主分有多少不同时非常有用。

**快捷方式**

* 菜单（for git）：VCS → Git → Compare With Branch
* 查找行为：Compare With Branch





























































