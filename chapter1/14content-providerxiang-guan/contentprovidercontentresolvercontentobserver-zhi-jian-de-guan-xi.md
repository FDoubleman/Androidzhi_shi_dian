#### ContentProvider、ContentResolver、ContentObserver 之间的关系

1、ContentProvider 内容提供者，用于对外提供数据

2、ContentResolver 内容解析者，用于获取内容提供者提供的数据

3、ContentObserver 内容监听器，可以监听数据的改变状态

4、ContentResolver.notifyChange\(uri\)发出消息

5、ContentResolver.registerContentObserver\(\)监听消息。

