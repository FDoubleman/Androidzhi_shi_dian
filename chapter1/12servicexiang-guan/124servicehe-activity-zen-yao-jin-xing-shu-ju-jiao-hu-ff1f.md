#### service和activity怎么进行数据交互？

> 一种是使用broadcast，另一种是使用bindService。

1. #### 通过广播：在service中发送广播，在activity中创建一个BroadcastReceive\(\)接收
2. #### BindService：activity通过Intent传值给service,并创建ServiceConnection\(\)对象，获得BindService.MyBind。



