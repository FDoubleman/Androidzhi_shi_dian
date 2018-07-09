#### 怎么保证service不被杀死？

1. ##### onStartCommand方法，返回START\_STICKY，当service因内存不足被kill，当内存又有的时候，service又被重新创建。
2. ##### 提升service优先级，在AndroidManifest.xml文件中对于intent-filter可以通过android:priority = "1000"这个属性设置最高优先级，1000是最高值，如果数字越小则优先级越低
3. ##### 提升service进程优先级
4. ##### service +broadcast 方式，就是当service走ondestory的时候，发送一个自定义的广播，当收到广播的时候，重新启动service
5. ##### 两个守护进程



