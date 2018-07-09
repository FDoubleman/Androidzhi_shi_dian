**一、Android 生命周期图**

![](/assets/生命周期.png)

**二、各种情况生命周期**

* 正常生命周期：  onCreat\(\) --&gt; onStart\(\) --&gt; onResume\(\) --&gt; running --&gt; onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击back键   ：  onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击home键  ：  onPause\(\) --&gt; onStop\(\)
* activity A 开启 activityB : A onPause\(\) --&gt; B onCreat\(\) --&gt; B onStart --&gt; B onResume\(\) --&gt; A onStop\(\)

* 在B 再按返回键到A: B:onPause\(\) -&gt; A:onRestart\(\) -&gt; A:onStart\(\) -&gt; A:onResume\(\) -&gt; B:onStop\(\) -&gt; B:onDestroy\(\)

**三、横竖屏切换**

1. 在不设置Activity的android:configChanges时，切屏会重新调用各个生命周期，默认先销毁当前activity,之后再重新加载。

2. 设置Activity android:configChanges ="orientation\|keyboradHidden\|screenSize"时，切屏不会调各个生命周期。只会执行 onconfigurationChange 方法。



