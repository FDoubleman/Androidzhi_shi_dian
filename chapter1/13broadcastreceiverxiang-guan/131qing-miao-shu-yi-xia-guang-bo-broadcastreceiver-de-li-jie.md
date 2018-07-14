#### 请描述一下广播BroadcastReceiver的理解

**广播（Broadcast）**是在不同进程间通信的一种组件，**起到通知和传递数据的作用**。

**广播接受者（BroadcastReceiver）**是android中的四大组件之一，一旦被启动之后就可以在后台监听广播事件，当然对于已经用不到的广播事件我们也可以调用**unregisterReceiver\(receiver\)方法来注销广播**，被注销的广播就不能在重新注册了

