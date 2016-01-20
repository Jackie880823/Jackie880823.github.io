---
layout: post
title: Android Design Support Library
---
[Material Design](http://www.google.com/design/spec/material-design/introduction.html)在Android 5.0中用于提升用户体验的设计语言（或理念），但在5.0以下2.1以上就需要`Android Design Support Library`包来支持，这个包中集合了导航抽屉、浮动编辑、浮动button、snackbar、tabs等。

##NavigationView（导航）

[NavigationView](http://developer.android.com/reference/android/support/design/widget/NavigationView.html?utm_campaign=io15&utm_source=dac&utm_medium=blog)能够很易容的为应用提供抽屉模式的导航框架。

<image src="https://github.com/Jackie880823/AndroidDesignLearn/raw/master/images/navigation-view.png" width="400px"/>

NavigationView需要放在[DrawerLayout](http://developer.android.com/reference/android/support/v4/widget/DrawerLayout.html)布局当中：

	<android.support.v4.widget.DrawerLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:fitsSystemWindows="true">

    	<!-- 这里放主页面的布局 -->

    	<android.support.design.widget.NavigationView
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_gravity="start"
            app:headerLayout="@layout/drawer_header"
            app:menu="@menu/drawer"/>
	</android.support.v4.widget.DrawerLayout>

这里有两个NavigationView属性: `app:headerLayout`(可选)--控制抽屉的头布局，如本介绍的中的`Hello World`显示的布局。`app:menu`是一个导航选择项的菜单资源（可以在程序运行时对导航项更新）。

菜单布局如下：

	<?xml version="1.0" encoding="utf-8"?>
	<menu xmlns:android="http://schemas.android.com/apk/res/android">
    	<group android:checkableBehavior="all">
        	<item android:id="@+id/nv_home"
            	android:icon="@drawable/ic_action_location_found_dark"
            	android:title="@string/text_home"/>
        	<item android:id="@+id/nv_blog"
            	android:icon="@drawable/ic_action_location_found_dark"
	            android:title="@string/text_blog"/>
    	    <item android:id="@+id/nv_about"
        	    android:icon="@drawable/ic_action_location_found_dark"
            	android:title="@string/text_about"/>
	        <item android:id="@+id/nv_contact"
    	        android:icon="@drawable/ic_action_location_found_dark"
        	    android:title="@string/text_contact"/>
    	</group>
	</menu>

点击子项时对应子项会高亮显示，以确保用户能准确知道当前选中的抽屉子项。同时抽屉菜单的每项还可以有子菜单。如下：

	<item
    	android:id="@+id/navigation_subheader"
	    android:title="@string/navigation_subheader">
    	<menu>
        	<item
            	android:id="@+id/navigation_sub_item_1"
	            android:icon="@drawable/ic_android"
    	        android:title="@string/navigation_sub_item_1"/>
        	<item
            	android:id="@+id/navigation_sub_item_2"
	            android:icon="@drawable/ic_android"
    	        android:title="@string/navigation_sub_item_2"/>
	    </menu>
	</item>

**NavigationView**设计setNavigationItemSelectedListener来监听子项被选中的回调：

	navigationView.setNavigationItemSelectedListener(new NavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(MenuItem item) {
				/* 这里编写对应回调的操作 */
           		return false;
            }
	});

##[TextInputLayout](http://developer.android.com/reference/android/support/design/widget/TextInputLayout.html?utm_campaign=io15&utm_source=dac&utm_medium=blog)(浮动提示编辑)

**Material Design**也改善了传统的[EditText](http://developer.android.com/reference/android/widget/EditText.html?utm_campaign=io15&utm_source=dac&utm_medium=blog),EditText在用户输入任意一个文字后，对编辑内容的提示信息随即隐藏，而使用TextInputLayout添加的提示（`android:hint="" 或 setHint()`）会在编辑时一直浮在编辑框的上方，确保用户输入内容的正确性。

![浮动提示框](http://4.bp.blogspot.com/-BUKc5AwzS4A/VWihVlHr9cI/AAAAAAAABvI/rslBAoaHwzA/s1600/textinputlayout.png)

也可以显示错误信息(`setError`)。
