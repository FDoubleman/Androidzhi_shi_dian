#### Synchronized

> Java中的一个关键字，保证**同一时刻最多只有1个**线程**执行**被Synchrnized 修饰的方法/代码。其他线程必须等待当前线程执行完该方法/代码块后才能执行该方法/代码块

#### 1、应用场景：

保证线程安全，解决多线程中的并发同步问题（阻塞型并发）

#### 2、原理

* 依赖JVM同步实现
* 底层通过一个监视器对象（monitor）完成，wait\(\)、notify\(\)等方法也依赖于monitor对象
* 监视器锁（monitor）的本质依赖底层操作系统的互斥锁（Mutex Lock）实现

#### 3、锁的类型&等级

> 由于Synchronized会修饰 代码块、类的实例方法 &静态方法，故分为不同锁的类型

* 对象锁：含Synchronized方法/代码块的类的实例对象
* 方法锁（也属于对象锁）：使用Synchronized修饰的方法
* 类锁：使用Synchronized修饰 静态方法/代码块

4、使用方法

```
/**
 * 对象锁
 */
    public class Test{ 
    // 对象锁：形式1(方法锁) 
    public synchronized void Method1(){ 
        System.out.println("我是对象锁也是方法锁"); 
        try{ 
            Thread.sleep(500); 
        } catch (InterruptedException e){ 
            e.printStackTrace(); 
        } 
 
    } 
 
    // 对象锁：形式2（代码块形式） 
    public void Method2(){ 
        synchronized (this){ 
            System.out.println("我是对象锁"); 
            try{ 
                Thread.sleep(500); 
            } catch (InterruptedException e){ 
                e.printStackTrace(); 
            } 
        } 
 
    } 
 ｝

/**
 * 方法锁（即对象锁中的形式1）
 */
    public synchronized void Method1(){ 
        System.out.println("我是对象锁也是方法锁"); 
        try{ 
            Thread.sleep(500); 
        } catch (InterruptedException e){ 
            e.printStackTrace(); 
        } 
 
    } 

/**
 * 类锁
 */
public class Test{ 
　　 // 类锁：形式1 ：锁静态方法
    public static synchronized void Method1(){ 
        System.out.println("我是类锁一号"); 
        try{ 
            Thread.sleep(500); 
        } catch (InterruptedException e){ 
            e.printStackTrace(); 
        } 
 
    } 
 
    // 类锁：形式2 ：锁静态代码块
    public void Method2(){ 
        synchronized (Test.class){ 
            System.out.println("我是类锁二号"); 
            try{ 
                Thread.sleep(500); 
            } catch (InterruptedException e){ 
                e.printStackTrace(); 
            } 
 
        } 
 
    } 
｝
```

5、类锁和对象锁区别

![](/assets/944365-73825030c7a118fd.png)

