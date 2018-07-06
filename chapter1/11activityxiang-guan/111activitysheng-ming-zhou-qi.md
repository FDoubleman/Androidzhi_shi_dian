一、Android 生命周期图

![](/assets/生命周期.png)

二、各种情况生命周期

* 正常生命周期：  onCreat\(\) --&gt; onStart\(\) --&gt; onResume\(\) --&gt; running --&gt; onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击back键   ：  onPause\(\) --&gt; onStop\(\) --&gt; onDestroy\(\)
* 点击home键  ：  onPause\(\) --&gt; onStop\(\)
* activity A 开启 activityB : A onPause\(\) --&gt; B onCreat\(\) --&gt; B onStart --&gt; B onResume\(\) --&gt; A onStop\(\)

* 在B 再按返回键到A: B:onPause\(\) -&gt; A:onRestart\(\) -&gt; A:onStart\(\) -&gt; A:onResume\(\) -&gt; B:onStop\(\) -&gt; B:onDestroy\(\)



三、横竖屏切换

```
          onPause() --> onSaveInstanceState() --> onStop() -->onDestroy() --> onCreate()
          
          --> onStart() --> onResume()
```









