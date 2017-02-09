---
layout: post
title: 探索 Android ConstraintLayout
---

*英文原文：[https://medium.com/exploring-android/exploring-the-new-android-constraintlayout-eed37fe8d8f1#.oup0knb6r]*

![title](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/Exploring%20the%20new%20Android%20ConstraintLayout/1-xKFuNXnDJEh3KzS1DC5xww.jpeg?raw=true)
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;在过去几周的Google I/O大会中我看到了有关Android的新闻介绍。当我在这里讨论相关的一切时，让我们来看看Android最新且令人兴奋的[ConstraintLayout](http://tools.android.com/tech-docs/layout-editor)。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;为了更好地理解**ConstraintLayout**,我把我现在的一个项目（[Bourbon](https://github.com/hitherejoe/Bourbon)）用新的ConstraintLayour来手机转换布局。点击下图从GitHub中获取！
[![github](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/Exploring%20the%20new%20Android%20ConstraintLayout/1-MXKzhZ0gEGqk3DUkmd46jA.png?raw=true)](https://github.com/hitherejoe/Constraints)

##配置

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;如果你想尝试新的ConstraintLayout，在开始之前你还有一些准备工作需要做。

* 你需要从这里下载[Android Sutdio 2.2 预览版](http://tools.android.com/download/studio/builds/android-studio-2-2-preview-1)作为开始。
* 你也需要添加支持ConstraintLayout的依赖库：

		compile 'com.android.support.constraint:constraint-layout:1.0.0-alpha1'

就这样，现在可以开始了！

##那么，怎么是ConstraintLayout?

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;ConstraintLayout是一个强大的新类， RelativeLayout - 对，那就是ConstraintLayout。它允许我们用“constraint”来定义展示在Layout中的两个不同位置基点的子View之间的联系。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;ConstraintLayout的目标是帮助减少View的嵌套，从而优化我们的Layout文件的性能。这个Layout类也比RelativeLayout更容易定义View的侧边和相对View的侧边的位置，而不是留出整片区域来把View放置在其它View的任何一边。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;例如，RelativeLayout允许我们用于定义位置的属性：

* layout_toRightOf
* layout_toLeftOf
* layout_toTopOf
* layout_toBottomOf 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;而ConstraintLayout拥有的功能属性是：

* **layout_constraintTop_toTopOf — **要求View的顶部与另一个View的顶部对齐
* **layout_constraintTop_toBottomOf — **要求View的顶部与另一个View的底部对齐
* **layout_constraintBottom_toTopOf — **要求View的底部与另一个View的顶部对齐
* **layout_constraintBottom_toBottomOf — **要求View的底部与另一个View的底部对齐
* **layout_constraintLeft_toTopOf —**要求View左对齐另一个View的顶部









