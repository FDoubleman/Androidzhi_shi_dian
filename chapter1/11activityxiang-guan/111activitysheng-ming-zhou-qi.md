一、Android 生命周期图

![](/assets/生命周期.png)



二、各种情况生命周期

* 正常生命周期：  onCreat\(\) --&gt; onStart\(\) --&gt; onResume\(\) --&gt; running --&gt; onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击back键   ：  onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击home键  ：  onPause\(\) --&gt; onStop\(\)
* 




