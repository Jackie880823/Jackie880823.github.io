---
layout: post
title: Android 命令编译篇
---
使用Gradle编译你的安卓项目的，以debug版本为例：会在项目的`build/`目录中生成带签名的`app-debug.apk`和不带签名的`app-debug-unaligned.apk`两个apk文件。

Windows平台命令如下：

	> gradlew.bat assembleDebug

Mac或Linux平台命令如下：

	$ chmod +x gradlew
	$ ./gradlew assembleDebug

编译完成后，APK文件会输出在你的app模块（有些项目可能叫sample）下的 `build/outputs/apk/`目录中

	注：Mac或Linux平台使用的第一行代码是给gradlew这个文件添加可执权限，只在第一次编译时运行这条命令即可。
	
确定系统已经安装好了[Android SDK](http://		developer.android.com/sdk/installing/index.html)并已经将其中的`platform-tools/`添加到了PATH环境变量中，执行下面命令安装编译好的APK:

	adb install app/build/outputs/MyFirstApp-debug.apk
