#### 抽象类与接口的区别

> 抽象：将一类对象的共同特征 总结出来  & 构造成一类事物的过程。作用：隐藏具体实现方式 & 拓展模块的功能。
>
> 抽象类 & 接口  是抽象的具体实现。

#### 一、抽象类

#### ![](/assets/944365-c1cc6cae5128be59.png)二、接口

![](/assets/944365-67662bed92c3133c.png)

#### 区别：

![](/assets/944365-0ff5d61b5b2eeaf0.png)

> **实例代码：**
>
> * **需求1：有1类门，其本质功能 = 开门 & 关门**
> * **需求2：为上述这类门增加1个报警器，可进行报警**

```
// 方案1：只使用抽象类
  abstract class Door{  
      abstract void open();  
      abstract void close();  
      abstract void alarm();  
  }  

  // 具体使用时
  class AlarmDoor extends Door {  
      void open(){}  
      void close(){}  
      void alarm(){}  
  } 

// 方案2：只使用接口
  interface Door{  
      void open();  
      void close();  
      void alarm();  
  }  

  // 具体使用时
  class AlarmDoor implements  Door {  
      void open(){}  
      void close(){}  
      void alarm(){}  
  } 


// 方案3：同时使用抽象类 & 接口
  // 对于需求1 = 抽象1类事物，即 使用抽象类
  abstract class Door{  
      abstract void open();  
      abstract void close();  
  }  

  // 对于需求2 = 抽象事物中的某个行为， 即 使用 接口
  interface Alarm{  
      void alarm();  
  }  
  
  // 具体使用时
  class AlarmDoor extends Door implements Alarm{  
      void open(){}  
      void close(){}  
      void alarm(){}  
  } 
```

```

```





