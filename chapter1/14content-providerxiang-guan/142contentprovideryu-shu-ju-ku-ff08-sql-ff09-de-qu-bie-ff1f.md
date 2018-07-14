#### **为什么要使用ContentProvider?它和sql在实现上有什么区别?**

1. **ContentProvider** 屏蔽了**数据存储的细节**,**内部实现透明化**,**用户只需关心uri即可**\(是否匹配\)
2. **ContentProvider**能实现**不同app的数据共享**,sql **只能是自己程序才能访问**
3. **Contentprovider**还能增删本地的文件,xml等信息



