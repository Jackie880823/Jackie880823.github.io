---
layout: post
title: 代码混淆参数选项
---
*作者：Jackie Zhu, 时间：2016年8月11日*

<p align="center"> ![传说中的B2B](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/ProGuardUsage/0.gif?raw=true)

<p align="center"> **传说中的B2B**


&#160;&#160;&#160;&#160;&#160;&#160;&#160;本章只是对`Android Code ProGuard`各参数选项的一个说明，至于使用用例现在在网上随便一都能找来一大把。也许以后会加上一些用例，也会在以后再写有关`ProGuard`的文章推荐一些个人觉得比较好的用例。敬请期待吧！

&#160;&#160;&#160;&#160;&#160;&#160;&#160;若想获取比本文更全面的资料可以登陆[ProGuard Usage](http://proguard.sourceforge.net/manual/usage.html)官方网站或都`SDK`目录下的`tools/proguard/docs/manual/usage.html`中查看。`可以所有与ProGuard有关资料都出自其中`。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;在配置文件中你可以任意组合参数选项，而不受参数的顺序影响。以下就是参数选项的详细说明：

1. Input/Output Options
2. Keep Options
3. ShrinKing Options
4. Optimization Options
5. Obfuscation Options
6. Preverification Options
7. General Options
8. Class Paths
9. File Names
10. File Filters
11. Filters
12. Overview of Keep Options
13. Keep Option Modifiers
14. Class Specifications 

## Input/Output 输入/输出选项

	@<filename>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;`-include <fileName>`的简写。

	-include <fileName>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;递归读取`fileName`中的配置选项。

	-basedirectory <directoryName>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定所有配置参数文件和配置文件的相对目录的基本目录。

	-injars <class_path>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定被程序处理的输入的`jar（war, ear, zip, apk 或 目录）`文件。这些jar中的`.class`文件将会被处理（混淆）并写入到输入的`jar`中。默认情况下，任何非`.class`文件都将被原封不动的复制。请特别注意你直接导入的任何临时文件（例如：IDE创建的）。想要某个`class_path`被过滤掉，请参考`filters`的说明。为了更好的可读性，可在`-injars`选项中添加多个指定的`class_path`。

	-outjars <class_path>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定输出的`jar（war, ear, zip, apk 或 目录）`文件的名称。在先前`-injars`输入的文件将会被重写到指定的`jar`文件中，这将允许你选择输入的`jar`到指定输出的`jar`。另外，输出条目可以按filters的规则过滤掉，每一个被处理过的class文件和资源文件会被写入到第一个匹配过滤规则的输入文件中。你必须避免让输出文件重写任何的输入文件中。为了更好的可读性，可在`-outjars`选项中添加多个指定的`class_path`，如果没有任何的`-outjars`选项，`jar`文件不会被重写。

	-libraryjars <class_path>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定被程序引用的`jar（war, ear, zip, apk 或 目录）`文件。这些`jar`包含在输出的`jar`文件中。指定的`library jars`至少包含`application`的子类。`Library class files`只被调用而不必呈现，虽然它们的存在可以提升优化的结果，这些`class`路径会`filter`的要求来过滤。为了更好的可读性，可`-libraryjars`选项中添加多个指定的`class_path`。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;请注意当寻找`library class`时，引导路径和`ProGurad`的运行路径是不会被考虑在内的，这就意味着你要明确地指出你的代码会用到的`run-time jar`。尽管这样看起来会显得笨拙，但可以使你的程序运行在的不的运行环境中。比例，只需要确定适当的`run-time jar`你就可以运行在[J2SE application](http://proguard.sourceforge.net/manual/examples.html#application)以及[JME midlets](http://proguard.sourceforge.net/manual/examples.html#midlet)或[Android apps](http://proguard.sourceforge.net/manual/examples.html#androidapplication)中。

	-skipnonpubliclibraryclasses

&#160;&#160;&#160;&#160;&#160;&#160;&#160;为了提升运行速度和减少`ProGuard`的使用内存，当读取`library jars`时跳过`non-public classe`。默认情况下，读取library中的`non-public`和`public`类是一样的。然而，如果没影响引入的`jar`中实际的程序代码，通常情况下`non-public`类都是不相干的。在没有影响输出的情况下，可以忽略它们来加速`ProGuard`。不幸的是，一些库，包括最近的`JSE run-time`库，包含一些`non-public class`继承自`public library classes`，那在这种情况下你不能使用这个选项。此时使用这个选项`ProGuard`将打印出找不到类的警告。

	-dontskipnonpubliclibrarclasses

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定不去忽略`non-public library class`,这个在4.5以上的版本默认设置了。

	-dontskipnonpubliclibraryclassmembers

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定不忽略包可见的类成员(变量和函数)。默认情况下，解析库类的时候`ProGuard`会跳过这些类成员，程序类也一般不会去引用它们。然后有时候，程序中的类会使用`library jar`中的包可见的类成员，而使用与`library jar`的包名相同。在这种情况下要能实际有效的读取类中的成员，就需要保证代码的一致性而使用这个选项。

	-keepdirectories [directory_filter]

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定保存输出`jar（war, ear, zip, apk 或 目录）`的目录。输出目录默认是会被移除

	-target <version>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定Java的编译版本。版本号可以是1.0,1.1,1.2,1.3,1.4,1.5(或者就是5),1.6(或者就是6),1.7(或者就是7),1.8(或者就是8)。默认情况下class文件的版本号是保持不变的。比如，你想更新class file到Java 6。可以通过改变他们的版本让他们预编译。不应该降级的类文件的版本号，因为代码可能包含未在旧版本支持的构造。

	-forceprocessing

&#160;&#160;&#160;&#160;&#160;&#160;&#160;指定输入的过程



<p align="center">**未完待续……**

<p align="center">![迷之尴尬](https://github.com/Jackie880823/Jackie880823.github.io/blob/master/img/ProGuardUsage/1.gif?raw=true)













