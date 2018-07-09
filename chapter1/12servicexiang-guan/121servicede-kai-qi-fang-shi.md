#### Service的两种开启方式

![](/assets/1981935-bd709d5989105a12.png)

---

##### 1、Service的startService\(Intent\)启动方式

1、使用这种start方式启动的Service的**生命周期**如下:

onCreate\(\)---&gt;onStartCommand\(\)（onStart\(\)方法已过时） ---&gt; onDestory\(\)

2、如果**服务已经开启，不会重复的执行onCreate\(\)， 而是会调用onStart\(\)和onStartCommand\(\)**

3、服务停止的时候调用 **onDestory\(\)。服务只会被停止一次**。

4、**特点：**一旦服务开启跟调用者\(开启者\)就没有任何关系了。开启者退出了，开启者挂了，服务还在后台长期的运行。 开启者不能调用服务里面的方法。

```

```

##### 2、采用bind的方式开启服务

1、使用这种start方式启动的Service的生命周期如下：onCreate\(\) ---&gt;onBind\(\)---&gt;onunbind\(\)---&gt;onDestory\(\)

2、bind的方式开启服务，绑定服务，调用者挂了，服务也会跟着挂掉。 绑定者可以调用服务里面的方法

---

相关代码：

方式一、

```java
    //启动Service
    Intent intentOne= new Intent(this, TestOneService.class);

    startService(intentOne);
    
    //停止Service
    Intent intentFour = new Intent(this, TestOneService.class);
    stopService(intentFour);
    
    
```

方式二、

```java
public class TestTwoService extends Service{

    //client 可以通过Binder获取Service实例
    public class MyBinder extends Binder {
        public TestTwoService getService() {
            return TestTwoService.this;
        }
    }

    //通过binder实现调用者client与Service之间的通信
    private MyBinder binder = new MyBinder();

    private final Random generator = new Random();

    @Override
    public void onCreate() {
        Log.i("Kathy","TestTwoService - onCreate - Thread = " + Thread.currentThread().getName());
        super.onCreate();
    }

    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        Log.i("Kathy", "TestTwoService - onStartCommand - startId = " + startId + ", Thread = " + Thread.currentThread().getName());
        return START_NOT_STICKY;
    }

    @Nullable
    @Override
    public IBinder onBind(Intent intent) {
        Log.i("Kathy", "TestTwoService - onBind - Thread = " + Thread.currentThread().getName());
        return binder;
    }

    @Override
    public boolean onUnbind(Intent intent) {
        Log.i("Kathy", "TestTwoService - onUnbind - from = " + intent.getStringExtra("from"));
        return false;
    }

    @Override
    public void onDestroy() {
        Log.i("Kathy", "TestTwoService - onDestroy - Thread = " + Thread.currentThread().getName());
        super.onDestroy();
    }

    //getRandomNumber是Service暴露出去供client调用的公共方法
    public int getRandomNumber() {
        return generator.nextInt();
    }
}

```

```java
public class ActivityA extends Activity implements Button.OnClickListener {
    private TestTwoService service = null;
    private boolean isBind = false;

    private ServiceConnection conn = new ServiceConnection() {
        @Override
        public void onServiceConnected(ComponentName name, IBinder binder) {
            isBind = true;
            TestTwoService.MyBinder myBinder = (TestTwoService.MyBinder) binder;
            service = myBinder.getService();
            Log.i("Kathy", "ActivityA - onServiceConnected");
            int num = service.getRandomNumber();
            Log.i("Kathy", "ActivityA - getRandomNumber = " + num);
        }

        @Override
        public void onServiceDisconnected(ComponentName name) {
            isBind = false;
            Log.i("Kathy", "ActivityA - onServiceDisconnected");
        }
    };

    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_a);
        Log.i("Kathy", "ActivityA - onCreate - Thread = " + Thread.currentThread().getName());

        findViewById(R.id.btnBindService).setOnClickListener(this);
        findViewById(R.id.btnUnbindService).setOnClickListener(this);
        findViewById(R.id.btnStartActivityB).setOnClickListener(this);
        findViewById(R.id.btnFinish).setOnClickListener(this);
    }

    @Override
    public void onClick(View v) {
        if (v.getId() == R.id.btnBindService) {
            //单击了“bindService”按钮
            Intent intent = new Intent(this, TestTwoService.class);
            intent.putExtra("from", "ActivityA");
            Log.i("Kathy", "----------------------------------------------------------------------");
            Log.i("Kathy", "ActivityA 执行 bindService");
            bindService(intent, conn, BIND_AUTO_CREATE);
        } else if (v.getId() == R.id.btnUnbindService) {
            //单击了“unbindService”按钮
            if (isBind) {
                Log.i("Kathy",
                        "----------------------------------------------------------------------");
                Log.i("Kathy", "ActivityA 执行 unbindService");
                unbindService(conn);
            }
        } else if (v.getId() == R.id.btnStartActivityB) {
            //单击了“start ActivityB”按钮
            Intent intent = new Intent(this, ActivityB.class);
            Log.i("Kathy",
                    "----------------------------------------------------------------------");
            Log.i("Kathy", "ActivityA 启动 ActivityB");
            startActivity(intent);
        } else if (v.getId() == R.id.btnFinish) {
            //单击了“Finish”按钮
            Log.i("Kathy",
                    "----------------------------------------------------------------------");
            Log.i("Kathy", "ActivityA 执行 finish");
            this.finish();
        }
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.i("Kathy", "ActivityA - onDestroy");
    }
}

```







