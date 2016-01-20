---
layout: post
title: 在IntentService中执行后台任务
---

*&#160;&#160;&#160;&#160;&#160;&#160;&#160;除非明确地指明其它情况，你在应用中所执行的大部分任务都是在一个叫UI线程的特殊线程。这可能会存在隐患，因为耗时操作会影响用户交互响应。这种交互响应将会惹恼你的用户，甚至会导致出现系统ANR错误。为了避免这种现象，Android框架提供了一些类来帮助你转移这些操作到一个单独的后台线程执行。[IntentSerice](http://developer.android.com/reference/android/app/IntentService.html)就是其中最常用的一个类。
这章将描述如何实现[IntentService](http://developer.android.com/reference/android/app/IntentService.html),向其发送一个工作请并返回馈结果到其它组件。*

##创建后台服务

&#160;&#160;&#160;&#160;&#160;&#160;&#160;[IntentService](http://developer.android.com/reference/android/app/IntentService.html)为执行单一后台线程的任务提供了简单的实现结构。它可以在执行一个耗时的操作而不影响到你的界面响应。另外，它也不受多数用户交互界面生命周期的影响。如此它可以丢弃[AsyncTask](http://developer.android.com/reference/android/os/AsyncTask.html)而一直保持在运行状态。

**[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的几个使用限制**

+ 不能直接与界面进行交互。展示结果到UI，必需把它发送到给Activity。
+ 工作请求按顺序执行。如果一个操作正在[IntentService](http://developer.android.com/reference/android/app/IntentService.html)执行，而你又发送了另一个请求，那么这个请求是等待直到上一个请求执行完毕再执行。
+ 一个操作正在[IntentService](http://developer.android.com/reference/android/app/IntentService.html)中运行时不能被中断。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;尽管如此，大多数情况下，[IntentService](http://developer.android.com/reference/android/app/IntentService.html)执行简单的后台操作还是一种很受欢迎的方式。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;下面小节将向你演示如何创建属于你自己的[IntentService](http://developer.android.com/reference/android/app/IntentService.html)子类。也包括演示如何创建必需实现的回调函数[onHandleIntent()]("http://developer.android.com/reference/android/app/IntentService.html#onHandleIntent(android.content.Intent)").最终，演示如何在manifest文件中定义这个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)。

###创建一个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)
---

&#160;&#160;&#160;&#160;&#160;&#160;&#160;给你的应用创建一个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)，定义一个继承至[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的类，并在这个类中覆写[onHandleIntent()](http://developer.android.com/reference/android/app/IntentService.html#onHandleIntent(android.content.Intent))。如下：

    public class RSSPullService extends IntentService {
        @Override
        protected void onHandleIntent(Intent workIntent) {
            // Gets data from the incoming Intent
            String dataString = workIntent.getDataString();
            ...
            // Do work here, based on the contents of dataString
            ...****
        }
    }

&#160;&#160;&#160;&#160;&#160;&#160;&#160;**注意：**普通[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的其它回调函数，比如[onStartCommand()]("http://developer.android.com/reference/android/app/Service.html#onStartCommand(android.content.Intent, int, int)")会自动被 [IntentService](http://developer.android.com/reference/android/app/IntentService.html)唤起。在[IntentService](http://developer.android.com/reference/android/app/IntentService.html)中，你需要避免覆写这个回调函数。

###在Manifest中定义[IntentService](http://developer.android.com/reference/android/app/IntentService.html)
---

&#160;&#160;&#160;&#160;&#160;&#160;&#160;[IntentService](http://developer.android.com/reference/android/app/IntentService.html)需要添加在你应用的Manifest中，将其作为`<service>`节点插入`<application>`的子节中:

    <application
        android:icon="@drawable/icon"
        android:label="@string/app_name">
        ...
        <!--
            Because android:exported is set to "false",
            the service is only available to this app.
        -->
        <service
            android:name=".RSSPullService"
            android:exported="false"/>
        ...
    <application/>

&#160;&#160;&#160;&#160;&#160;&#160;&#160;属性`android:name`指明了这个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的类名。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;**注意：**这个`<service>`节点不能包含`intent-filter`。 Activity发送工作请求给服务需要使用显示的[Intent](http://developer.android.com/reference/android/content/Intent.html)，所以也不需要`intent-filter`。这就意味着中有在同一应用或有同样`user ID`的模块才能使用这个`service`。

##发送工作请求到后台服务

&#160;&#160;&#160;&#160;&#160;&#160;&#160;本节向你演示如何使用
[IntentService](http://developer.android.com/reference/android/app/IntentService.html)运行通过[Intent](http://developer.android.com/reference/android/content/Intent.html)发送过来的任务，这个[Intent](http://developer.android.com/reference/android/content/Intent.html)可以随意的添加数据来让[IntentService](http://developer.android.com/reference/android/app/IntentService.html)处理。你可以在[Activity](http://developer.android.com/reference/android/app/Activity.html)或[Fragment](http://developer.android.com/reference/android/app/Fragment.html)的任何节点向[IntentService](http://developer.android.com/reference/android/app/IntentService.html)发送[Intent](http://developer.android.com/reference/android/content/Intent.html)。

###创建一个工作请求发送给[IntentService](http://developer.android.com/reference/android/app/IntentService.html)

---

&#160;&#160;&#160;&#160;&#160;&#160;&#160;创建一个工作请求并发送给[IntentService](http://developer.android.com/reference/android/app/IntentService.html)，创建一个显示的[Intent](http://developer.android.com/reference/android/content/Intent.html)，并添加工作请求的数据，通过调用[startService()]("http://developer.android.com/reference/android/content/Context.html#startService(android.content.Intent)")函数将这个[Intent](http://developer.android.com/reference/android/content/Intent.html)传送给[IntentService](http://developer.android.com/reference/android/app/IntentService.html)，创建一个显示的[Intent](http://developer.android.com/reference/android/content/Intent.html)。

操作示范如下：

1.&#160;新建一个显示[Intent](http://developer.android.com/reference/android/content/Intent.html)。

	/*
	 * Creates a new Intent to start the RSSPullService
	 * IntentService. Passes a URI in the
	 * Intent's "data" field.
	 */
	mServiceIntent = new Intent(getActivity(), RSSPullService.class);
	mServiceIntent.setData(Uri.parse(dataUrl));

2.&#160;调用[startService()]("http://developer.android.com/reference/android/content/Context.html#startService(android.content.Intent)")函数。

	// Starts the IntentService
	getActivity().startService(mServiceIntent);

&#160;&#160;&#160;&#160;&#160;&#160;&#160;**注意：**你可以在[Activity](http://developer.android.com/reference/android/app/Activity.html)或[Fragment](http://developer.android.com/reference/android/app/Fragment.html)的任何位置发送这个工作请求。例如，你需要获取用户输入，你可以在点击按钮的回调函数或者其它类似的手势响应回调函数中发送这个工作请求。

&#160;&#160;&#160;&#160;&#160;&#160;&#160;一旦执行了[startService()]("http://developer.android.com/reference/android/content/Context.html#startService(android.content.Intent)"),这个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)就在你覆写的[onHandleIntent()]("http://developer.android.com/reference/android/app/IntentService.html#onHandleIntent(android.content.Intent)")函数就会执行这个任务，并在执行完毕后自动关闭这个[IntentService](http://developer.android.com/reference/android/app/IntentService.html)。

##返馈工作状态

&#160;&#160;&#160;&#160;&#160;&#160;&#160;本节向你演示如何返回后台服务执行请求的运行状态。例如，发送请求的执行状态给[Activity](http://developer.android.com/reference/android/app/Activity.html)的UI。推荐使用[LocalBroadcastManager](http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)来发送和接收状态，它可以限制广播的[Intent](http://developer.android.com/reference/android/content/Intent.html)只在你自己的应用中传递。

###Report Status From an IntentService

---

&#160;&#160;&#160;&#160;&#160;&#160;&#160;发送[IntentService](http://developer.android.com/reference/android/app/IntentService.html)执行工作请求的状态到其它组件，首先创建一个包含状态信息的[Intent](http://developer.android.com/reference/android/content/Intent.html)。还可以给这个[Intent](http://developer.android.com/reference/android/content/Intent.html)添加一个`action`和`data URI`。
&#160;&#160;&#160;&#160;&#160;&#160;&#160;其次，调用[LocalBroadcastManager.sendBroadcast()]("http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html#sendBroadcast(android.content.Intent)")来发送这个[Intent](http://developer.android.com/reference/android/content/Intent.html)。这个[Intent](http://developer.android.com/reference/android/content/Intent.html)被发送到你应用中的任何一个注册了这个广播的组件中。调用[getInstance()]("http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html#getInstance(android.content.Context)")来获取[LocalBroadcastManager](http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)的实例。

代码如下：

	public final class Constants {
	    ...
	    // Defines a custom Intent action
	    public static final String BROADCAST_ACTION =
	        "com.example.android.threadsample.BROADCAST";
	    ...
	    // Defines the key for the status "extra" in an Intent
	    public static final String EXTENDED_DATA_STATUS =
	        "com.example.android.threadsample.STATUS";
	    ...
	}
	public class RSSPullService extends IntentService {
	...
	    /*
	     * Creates a new Intent containing a Uri object
	     * BROADCAST_ACTION is a custom Intent action
	     */
	    Intent localIntent =
	            new Intent(Constants.BROADCAST_ACTION)
	            // Puts the status into the Intent
	            .putExtra(Constants.EXTENDED_DATA_STATUS, status);
	    // Broadcasts the Intent to receivers in this app.
	    LocalBroadcastManager.getInstance(this).sendBroadcast(localIntent);
	...
	}

下一步是在发送工作请求的组件中接收广播发送出来的[Intent](http://developer.android.com/reference/android/content/Intent.html)。

###接收[IntentService](http://developer.android.com/reference/android/app/IntentService.html)的状态广播

用[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)的子类接收广播的[Intent](http://developer.android.com/reference/android/content/Intent.html)。在这个子类中实现回调函数[BroadcastReceiver.onReceive()]("http://developer.android.com/reference/android/content/BroadcastReceiver.html#onReceive(android.content.Context, android.content.Intent)")。这样[LocalBroadcastManager](http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)就把[Intent](http://developer.android.com/reference/android/content/Intent.html)发送出来让[BroadcastReceiver.onReceive()]("http://developer.android.com/reference/android/content/BroadcastReceiver.html#onReceive(android.content.Context, android.content.Intent)")接收了。

代码如下：

	// Broadcast receiver for receiving status updates from the IntentService
	private class ResponseReceiver extends BroadcastReceiver
	{
	    // Prevents instantiation
	    private DownloadStateReceiver() {
	    }
	    // Called when the BroadcastReceiver gets an Intent it's registered to receive
	    @
	    public void onReceive(Context context, Intent intent) {
	...
	        /*
	         * Handle Intents here.
	         */
	...
	    }
	}

&#160;&#160;&#160;&#160;&#160;&#160;&#160;一但定义了[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)，你就能创建有明确`action`、`categories`和`data`的过滤器。创建[IntentFilter](http://developer.android.com/reference/android/content/IntentFilter.html)来承载这它。下面的代码片段向你演示了如何定义这个过滤器。

	// Class that displays photos
	public class DisplayActivity extends FragmentActivity {
	    ...
	    public void onCreate(Bundle stateBundle) {
	        ...
	        super.onCreate(stateBundle);
	        ...
	        // The filter's action is BROADCAST_ACTION
	        IntentFilter mStatusIntentFilter = new IntentFilter(
	                Constants.BROADCAST_ACTION);

	        // Adds a data filter for the HTTP scheme
	        mStatusIntentFilter.addDataScheme("http");
	        ...

&#160;&#160;&#160;&#160;&#160;&#160;&#160;获取系统的[LocalBroadcastManager](http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)实例并调用[registerReceiver()]("http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html#registerReceiver(android.content.BroadcastReceiver, android.content.IntentFilter)")函数来注册[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)和[IntentFilter](http://developer.android.com/reference/android/content/IntentFilter.html)。下面的代码片段向你演示如何注册[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)和[IntentFilter](http://developer.android.com/reference/android/content/IntentFilter.html)：

        // Instantiates a new DownloadStateReceiver
        DownloadStateReceiver mDownloadStateReceiver =
                new DownloadStateReceiver();
        // Registers the DownloadStateReceiver and its intent filters
        LocalBroadcastManager.getInstance(this).registerReceiver(
                mDownloadStateReceiver,
                mStatusIntentFilter);
        ...

&#160;&#160;&#160;&#160;&#160;&#160;&#160;一个[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)可以处理多个类型的广播[Intent](http://developer.android.com/reference/android/content/Intent.html),这些[Intent](http://developer.android.com/reference/android/content/Intent.html)都有自已的`action`。这个功能让你不用定义多个不同的[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)来执行不同的`action`。在同一个[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)定义另一个[IntentFilter](http://developer.android.com/reference/android/content/IntentFilter.html)，创建它并重新调用[registerReceiver()]("http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html#registerReceiver(android.content.BroadcastReceiver, android.content.IntentFilter)")。例如：

        /*
         * Instantiates a new action filter.
         * No data filter is needed.
         */
        statusIntentFilter = new IntentFilter(Constants.ACTION_ZOOM_IMAGE);
        ...
        // Registers the receiver with the new filter
        LocalBroadcastManager.getInstance(getActivity()).registerReceiver(
                mDownloadStateReceiver,
                mIntentFilter);

&#160;&#160;&#160;&#160;&#160;&#160;&#160;发送一个广播[Intent](http://developer.android.com/reference/android/content/Intent.html)不会启动或重启[Activity](http://developer.android.com/reference/android/app/Activity.html)。即使你的应用在后台运行[Activity](http://developer.android.com/reference/android/app/Activity.html)的[BroadcastReceiver](http://developer.android.com/reference/android/content/BroadcastReceiver.html)也能接收和处理这个[Intent](http://developer.android.com/reference/android/content/Intent.html)，这样也不会使你的应用转至前台。如果你的应用在不可见时，又想通知用户后台发生了这个事件，可以用[Notification](http://developer.android.com/reference/android/app/Notification.html)。永远不要在接收到广播[Intent](http://developer.android.com/reference/android/content/Intent.html)请求后去启动[Activity](http://developer.android.com/reference/android/app/Activity.html)。

*Demo 下载: [ThreadSample.zip](http://developer.android.com/shareables/training/ThreadSample.zip)*











ß










