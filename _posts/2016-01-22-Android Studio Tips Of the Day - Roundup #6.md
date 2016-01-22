---
layout: post
title: Android Studio 贴士 - 综述#6
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-6](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-6)*

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;注：文中链接皆为国外链接，可能需要翻墙*

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这篇是我发表在[Google+](https://plus.google.com/+PhilippeBreault/)上有关`Android Studio 贴士`综述的第二部分。你可以点击（[原文](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-6) 或 [译文](http://jackie880823.github.io/2016/01/18/Android%20Studio%20Tips%20Of%20the%20Day%20-%20Roundup%20%236)）查看上一部分的内容。


#**快捷键映射表（Keymaps）**

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;`Android Studio`提供了很多不同的快捷键映射表（快捷键对应行为的映射）。你可以在`Settings > Keymap`中看到它。
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;实际上你并不需要使用到所有的映射表，所以下面
不同系统所选择表的建议也许对你会有用：

* Windows: Defalut
* Linux: Default
* OSX: Mac OSX 10.5+

---

#**重构**

![Refactor this](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/48-refactorthis.png?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这是列出当前选择的上下文中能够重构的快捷键。这个列表可以通过键盘检索也可以产左边的对应的数字进行快速定位。

**快捷方式**

* Mac: Ctrl+T
* windwos/Linux: Ctrl + Alt + Shift + T

---

#**相连文件**

![Related File](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/50-relatedfile.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个帮助你在`layout`和`activity/fragment`之间快速切换。在类名的左边栏和`layout`文件和顶部的左边栏来导航。

**快捷方式**

* Mac: Ctrl + Cmd + Up
* Windows/Linux: Ctrl + Alt + Home

---

#**提取变量**

![Extract Variable](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/51-extractvariable.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;不用通过重构菜单快捷地撮变量。这个在你动态地生成代码时可以输入一个空变量的声明来直接使用它的值。IDE会对生成的声明提供一些建议的名称。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;额外贴士：

* 如果你想将声明修改为更能用的类型（比如：用`List`替换`ArrayList`），你可以使用`Shift + Tab`会给你列出有用的相关类型。

**快捷方式**

* Mac: Cmd + Alt + V
* Windows/Linux: Ctrl + Alt + V

---

#**提取参数**

![Extract Parameter](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/52-extractparam.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;不用通过重构菜单快捷地提取参数。这个方式用在当你意识到一个函数应当提取一部分做为参数时。它会提取你当前选择的值做为函数的参数并把它复制给每一个这个函数的调用者。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;额外贴士：

* 你也可以保留原始的函数，点击`delegate`复选框来将其委托给一个新的函数。

**快捷方式**

* Mac: Cmd + Alt + P
* Windows/Linux: Ctrl + Alt + P

---

#**提取函数**

![Extract Method](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/53-extractmethod.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;跟着我提取重构的思路，这个是提取一段代码块到一个新方法中。这个非常有用，每当你遇到一个函数变量巨大而且复杂时，你可以用这个方式来安全地提取某一块到另一个函数中。我说的安全是因为IDE不会像我们一样犯拷贝粘贴那样的低级错误。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;**额外贴士**

* 一旦进入提取框，你可以修改函数的可见度和参数的名称。

**快捷方式**

* Mac: Cmd + Alt + M
* Windows/Linux: Ctrl + Alt + M

---

#**Inline**

![Inline](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/54-inline.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;提取使用的太过疯狂并且生成了很多冗余的东西？你可以使用返向操作，这就是叫`“inline”`。它可用于函数，作用域，参数和变量上。

**快捷方式**

* Mac: Cmd + Alt + N
* Windows/Linux: Ctrl + Alt + N

---

#**重命名**

![Rename](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/55-rename.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;使用这个，你可以重命名变量、作用域、函数、类、甚至是包。当然，它会确保重命名在你整个应用的上下文中是有意义的，它不会简单地做一个查找然后替换所有文件！

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;**额外贴士**

* 如果你忘记了这个快捷键，你可以一直使用重构的快捷键，在弹出的列表中永远都包含这个重命名的快捷重构。

**快捷方式**：Shift + F6

---

#**上拉/下推**

![Rename](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-6/56-pullupdown.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;当我们谈论上拉成员，我们的意思是我们将会让当前类的一些成员（通常是方法或field）发送它到父类或接口。如果继承于一个类，内容会被移动。如果是实现的一个接口，它将会声明方法作为接口的一部分，在你的类中保持原有的方法并且添加 @Override注解。当我们谈论下推成员，这正好是反向操作，我们会从父类或接口发送一些成员到子类。

**快捷方式**

* Mac: Ctrl+T 然后选择成员 
* Windows/Linux: Ctrl+Alt+Shift+T 然后选择成员


















