#
#### 先来看下这官网的Activity生命周期图

![image](http://upload-images.jianshu.io/upload_images/1685558-d3176065dcf72d21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#

### Activity重要要点

##### 1. 如果Activity在需要离开（跳转）时，在哪里保存数据要好点呢？

##### 回答：

    看下Activity的退出周期过程：onPause->onStop ,在生命周期为：onPause时，界面还是可见如Dialog时，
    当保存数据时放在onPause可保证数据的有效性，如果放在onStop，
    在某些情况下Activity走完onPause后有可能还没顺利走到onStop就被系统回收了。

###### == 注意：在onPause中要非常迅速地执行完所需操作，不然会影响到下一个Activity的生命周期函数的调用。 ==

##### 2. onStart和onResume的区别？

##### 回答：

    当执行到onStart时，界面可见，但是界面不可交互，而onResume时，界面可见，亦可交互。

###### 解惑：

##### 1.dialog 弹出时会调用onPause？

    其实不然，调用 dialog形式的activity 才会触发当前activity的生命周期;
    例如：AlertDialog.Builder 就不会调用生命周期
    
##### 2.Android 可见生命周期？

    Activity 的可见生命周期发生在 onStart调用与 onStop调用之间。
    在这段时间，用户可以在屏幕上看到 Activity 并与其交互。
    我们可以在 onStart中注册一个 BroadcastReceiver以监控影响 UI 的变化，并在用户无法再看到您显示的内容时在 onStop中将其取消注册。
