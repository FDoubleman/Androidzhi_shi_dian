#### Service的两种开启方式

![](/assets/1981935-bd709d5989105a12.png)

---

##### 1、Service的startService\(Intent\)启动方式

1、使用这种start方式启动的Service的**生命周期**如下:

onCreate\(\)---&gt;onStartCommand\(\)（onStart\(\)方法已过时） ---&gt; onDestory\(\)

2、如果**服务已经开启，不会重复的执行onCreate\(\)， 而是会调用onStart\(\)和onStartCommand\(\)**

3、服务停止的时候调用 **onDestory\(\)。服务只会被停止一次**。

4、**特点：**一旦服务开启跟调用者\(开启者\)就没有任何关系了。开启者退出了，开启者挂了，服务还在后台长期的运行。 开启者不能调用服务里面的方法。

##### 2、采用bind的方式开启服务

1、使用这种start方式启动的Service的生命周期如下：onCreate\(\) ---&gt;onBind\(\)---&gt;onunbind\(\)---&gt;onDestory\(\)

2、bind的方式开启服务，绑定服务，调用者挂了，服务也会跟着挂掉。 绑定者可以调用服务里面的方法



---



