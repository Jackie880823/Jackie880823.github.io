---
layout: post
title: Android Studio 贴士 - 综述#3
---
*作者：Philippe Breault  英文原文：[http://www.developerphil.com/android-studio-tips-of-the-day-roundup-3](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-3)*

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;注：文中链接皆为国外链接，可能需要翻墙*

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这篇是我发表在[Google+](https://plus.google.com/+PhilippeBreault/)上有关`Android Studio 贴士`综述的第二部分。你可以点击（[原文](http://www.developerphil.com/android-studio-tips-of-the-day-roundup-1/) 或 [译文](http://jackie880823.github.io/2015/12/26/Android%20Studio%20Tips%20Of%20the%20Day%20-%20Roundup%20%231/)）查看上一部分的内容。


##**快捷键映射表（Keymaps）**

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;`Android Studio`提供了很多不同的快捷键映射表（快捷键对应行为的映射）。你可以在`Settings > Keymap`中看到它。  
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;实际上你并不需要使用到所有的映射表，所以下面
不同系统所选择表的建议也许对你会有用：

* Windows: Defalut
* Linux: Default
* OSX: Mac OSX 10.5+

---

## **标识断点**

![标识断点](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/21-togglebreakpoints.gif?raw=true) 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;接下来的几个贴士都和调度有关。所以让我们从最基础的开始：添加断点！我可以确认你现在知道如何用鼠标在左边栏添加一个断点。而这里是不用鼠标的情况下正确添加这个断点。

|    OSX   |    Linu   |  windows  |
|----------|-----------|-----------|
| cmd + F8 | ctrl + F8 | ctrl + F8 |

---

## **附带条件的断点**

![标识断点](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/22-conditionalbreakpoint.gif?raw=true) 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;简单的说，就是只是确定的条件下程序才会中断，你可以输入任何表达工返回boolean值来满足这个作用域的条件。在弱了的输入框中输入支持的条件代码来完成。

**快捷方式**

* 右击断点标识然后输入条件。

---

## **断点日志**

![标识断点](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/23-loggingbreakpoints.gif?raw=true) 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这是一个记录的断点而不是在这里中断。这个在当你需要记录某些东西时会有用，但他不能重新部署和添加记录代码。

**快捷方式**

* 右击断点标识，不选择 `Suspend`并在`Log evaluated Expression`中输入信息。

---

## **临时断点**

![标识断点](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/24-temporarybreakpoints.gif?raw=true) 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个方式会添加一个在首次点击会自动删除的断点。

**快捷方式**

* **鼠标：**在左边栏：Alt + 左击

|           OSX          |           Linu          |         windows         |
|------------------------|-------------------------|-------------------------|
| cmd + alt + shift + F8 | ctrl + alt + shift + F8 | ctrl + alt + shift + F8 |

## **失效断点**

![标识断点](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/25-disablebreakpoint.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个会使断点失效。

**快捷方式**

* `Alt + 左击`左边栏中存在的断点标识
* 没有快捷键，如果你经常使用这个功能的话可以在`Keymaps`中创建一个。

---

## **附加调试**

![附加调试](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/26-attachdebugger.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;即使不启动调试模式也能启动调试。这个在你必需在不重新部署应用启动调试期间是非常有用的。这个也能漂亮地用在某些人给你出现错误的设备时进入调度。

**快捷方式**

* **鼠标：** 点击如图图标或选择菜单栏的`Run → Attach debugger to Android Process`
* 没有快捷键，如果你经常使用这个功能的话可以在`Keymaps`中创建一个。

---

## **评估表达式**

![评估表达式](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/27-evaluateexpression.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个用于检查变量的内容和任何有效的表达式。

**快捷方式**

|    OSX   |    Linu   |  windows  |
|----------|-----------|-----------|
| cmd + F8 | ctrl + F8 | ctrl + F8 |

---

## **审查变量**

![评估表达式](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/28-mouse_evaluate_expression.gif?raw=true)

&#160;&#160;&#160;&#160;&#160;&#160;&#160;这个不用在打开`Evaluate Expression`对放话框来评估表达式。

**快捷方式**

* `Alt + 左击` 表达式。

---

## **标识项目**

![标识项目](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/29-markobject.gif?raw=true)

在调试会话期间,这将让你添加一个标签到一个特定的对象。

**快捷方式**

* 鼠标：右击并选择“`Mark Object`”
* 
| OSX | Linu|windows|
|-----|-----|-------|
|  F3 | F11 |  F11  |

---

## **分析堆栈**

![项目](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/android-studio-tips-of-the-day-roundup-3/30-analyzestacktrace.gif?raw=true)

**快捷方式：** 这个没有快捷键

* 鼠标：菜单 》Analyze Stacktrace
* 摸查行为：analyze stacktrace




















 










