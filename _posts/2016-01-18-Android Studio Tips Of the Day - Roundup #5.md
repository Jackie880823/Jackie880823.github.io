---
layout: post
title: Android Studio 贴士 - 综述#5
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-5](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-5)*

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

#**Enter vs Tab补全代码的方式**

![Enter vs Tab for Code Completion](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/45-codecompletionentertab.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;使用`tab`或`enter`键在补全代码时存在着一个有趣的差异。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;使用`Enter`会补全你想要的声明；使用`Tab`来补全声明则会删除点、括号、分号或空隔之前的所有内容。

**快捷方式**： `Enter`或`Tab`

---

#**跳到父类**

![Navigage to Parent](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/39-navigatetoparent.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;如果在覆盖了一个父类函数上（比如：Activity#onCreate()）,会跳到父类对这个函数的实现的位置。如果在这个类名上，则会跳到父类上。

**快捷方式**

|   OSX   |    Linu  |  windows |
|---------|----------|----------|
| Cmd + U | Ctrl + U | Ctrl + U |

---

#**回到编辑**

![Return to Editor](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/40-returntoeditor.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;一些快捷键会捆绑光标一起脱离编辑界面（调用层级、查找引用等等）。如果你想要回到编辑，你可以用以下选择：

* Escape: 简单地使光标回到编辑界面；
* Shift + Escape: 这回关闭当前的面板并把光标返回到编辑界面。

**快捷方式**

* 返回并保持面板打开：Escape
* 关闭面板和返回：Shift + Escape

---

#**跳到最近使用的工具窗口**

![Jump to Last Tool Window](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/41-lasttoolwindow.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;有时候，你回到的编辑界面但你发现你还需要返回到这个面析。比如：浏览查找的引用，这时你不需要使用鼠标就能返回到这个面板。

**快捷方式**：F12 (也许会和系统的快捷键有冲突)

---

#**隐藏所有面板**

![Hide All Panels](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/42-hideallwindows.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;将编辑框切入全屏模式。第二次使用这个快捷键所有的面板回到上一次的状态。

**快捷方式**

|   OSX   |    Linu  |  windows |
|---------|----------|----------|
| Cmd + Shift + F12 | Ctrl + Shift + F12 | Ctrl + Shift + F12 |

---

#**根据编号打开面板**

![Open a Panel by Its Number](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/43-openpanelbynumber.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;你可能注意到一些面板名字左边有一个数字。这是打开它们的快捷键。 如果你看不到面板的名字，可以点击IDE的左下角的盒子似的东西。

|      OSX     |      Linu    |    windows   |
|--------------|--------------|--------------|
| Cmd + Number | Alt + Number | Alt + Number |

#**参数信息**

![Parameter Info](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/44-parameterinfo.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;当你编写函数调用时会出现一引起相同参数名的列表。这在你需要查看函数存在的参数时会有用。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;光标所在对应的参数会变黄色，如果没有变成黄色，这意味着你调用了一个无效函数，也许是你输入了错误的参数类型（比如：用float类型替代了int类型的参数）。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;当你正在写一个方法调用参数信息意外地消失了，就像我经常做的，你也可以输入一个逗号（,）用来触发参数信息的显示。

|      OSX     |      Linu    |    windows   |
|--------------|--------------|--------------|
| Cmd + P | Ctrl + P | Ctrl + P |

---

#**切换器**

![The Switcher](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/46-switcher.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个功能和IDE的alt+tab/cmd+tab差不多。它允许你导航到一个tab或一个panel。一旦它被打开，只要你按住ctrl键，你可以使用数字或字母快捷键快速导航。你也可以关闭一个已选择的tab或panel通过按下backspace。

|      OSX     |      Linu    |    windows   |
|--------------|--------------|--------------|
| Ctrl + Tab | Ctrl + Tab | Ctrl + Tab |

---
#**上下文信息**

![The Switcher](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-5/47-contextinfo.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;当你定义的区域超出了滚动区域这个会向你显示当前的位置。通常是显示当前类和内部类的类名。也有可能是当前的函数名。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;在我看来，最有效的是用在快速查看当前类的继承和实现了那些类。这个在xml文件中也可以工作。

|      OSX     |      Linu    |    windows   |
|--------------|--------------|--------------|
| Ctrl+Shift+Q | Ctrl+Shift+Q | Ctrl+Shift+Q |










