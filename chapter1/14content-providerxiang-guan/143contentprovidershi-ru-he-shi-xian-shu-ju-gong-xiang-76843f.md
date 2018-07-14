#### **ContentProvider是如何实现数据共享的?**

#### ![](/assets/Contentprovide.png)

#### 

在创建Contentprovide时，需要首先使用数据库、文件系统或者网络底层存储功能，

然后在继承ContentProvid的类中，实现基本的数据操作的接口函数，包括添加、删除、查找和更新等功能

调用者不能直接调用ContentProvide的接口函数，而需要使用ContentResolver对象。

通过URI间接调用ContentProvider。

