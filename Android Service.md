#### Service的启动方式有几种？都有什么区别？
##### 回答：
###### Service是一个专门在后台处理长时间任务的Android组件，它没有UI。它有两种启动方式，startService和bindService。
###### *startService* 只是启动Service，启动它的组件（如Activity）和Service并没有关联，只有当Service调用stopSelf或者其他组件调用stopService服务才会终止。
###### *bindService* 方法启动Service，其他组件可以通过回调获取Service的代理对象和Service交互，而这两方也进行了绑定，当启动方销毁时，Service也会自动进行unBind操作，当发现所有绑定都进行了unBind时才会销毁Service。

#### Service的onCreate可以执行耗时操作吗？
##### 回答：
###### onCreate是在主线程（ActivityThread）中调用的，耗时操作会阻塞UI。

#### Serivce如果在非主线程启动，onCreate是否还是存在与主线程？

##### 回答：
###### 对于