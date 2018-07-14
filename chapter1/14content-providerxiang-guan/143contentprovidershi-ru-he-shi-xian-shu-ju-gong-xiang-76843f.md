#### **ContentProvider是如何实现数据共享的?**

#### 流程：

#### ![](/assets/Contentprovide.png)

#### 

在创建Contentprovide时，需要首先使用数据库、文件系统或者网络底层存储功能，

然后在继承ContentProvid的类中，实现基本的数据操作的接口函数，包括添加、删除、查找和更新等功能

调用者不能直接调用ContentProvide的接口函数，而需要使用ContentResolver对象。

通过URI间接调用ContentProvider。



---

1、在Android中为了把自己程序的数据（一般是指数据库）提供给其他应用程序，就通过ContentProvider提供的方法

2、内容提供者可认为是不同应用之间共享数据的接口，新建一个集成ContentProvider

3、按要求重新insert、delete、update、query方法（用于数据库的操作）

4、要记得进行清单文件注册：

     // 注册要加上作者标记authorities\(自定义的\)

```
    <provider
    android:authorities="this.bank.authority"
    android:name=".MyContentProvider"/>

```



