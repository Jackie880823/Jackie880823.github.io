---
layout: post
title: 在Service中执行后台任务
---

*除非明确地指明其它情况，你在应用中所执行的大部分任务都是在一个叫UI线程的特殊线程。这可能会存在隐患，因为耗时操作会影响用户交互响应。这种交互响应将会惹恼你的用户，甚至会导致出现系统ANR错误。为了避免这种现象，Android框架提供了一些类来帮助你转移这些操作到一个单独的后台线程执行。[IntentSerice](http://developer.android.com/reference/android/app/IntentService.html)就是其中最常用的一个类。
这章将描述如何实现[IntentService](http://developer.android.com/reference/android/app/IntentService.html),向其发送一个工作请并返回馈结果到其它组件。*

#创建IntentService

[IntentService](http://developer.android.com/reference/android/app/IntentService.html)为执行单一后台线程的任务提供了简单的实现结构。它可以在执行一个耗时的操作而不影响到你的界面响应。另外，它也不受多数用户交互界面生命周期的影响。如此它可以丢弃[AsyncTask](http://developer.android.com/reference/android/os/AsyncTask.html)而一直保持在运行状态。

**[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的几个使用限制**