### 集合常见问题

---

#### List，Set,Map三者的区别及总结

* **List：对付顺序的好帮手**

  > List接口存储一组不唯一（可以有多个元素引用相同的对象），有序的对象

* **Set:注重独一无二的性质**

  > 不允许重复的集合。不会有多个元素引用相同的对象。

* **Map:用Key来搜索的专家**

  > 使用键值对存储。Map会维护与Key有关联的值。两个Key可以引用相同的对象，但Key不能重复，典型的Key是String类型，但也可以是任何对象。

#### Arraylist 与 LinkedList 区别

Arraylist底层使用的是数组（存读数据效率高，插入删除特定位置效率低），LinkedList底层使用的是双向循环链表数据结构（插入，删除效率特别高）

#### ArrayList 与 Vector 区别

Vector类的所有方法都是同步的。可以由两个线程安全地访问一个Vector对象、但是一个线程访问Vector ，代码要在同步操作上耗费大量的时间。Arraylist不是同步的，所以在不需要同步时建议使用Arraylist。

#### HashMap 和 Hashtable 的区别

1.HashMap是非线程安全的，HashTable是线程安全的；HashTable内部的方法基本都经过synchronized修饰。

2.因为线程安全的问题，HashMap要比HashTable效率高一点，HashTable基本被淘汰。

3.HashMap允许有null值的存在，而在HashTable中put进的键值只要有一个null，直接抛出NullPointerException。
> Hashtable和HashMap有几个主要的不同：线程安全以及速度。仅在你需要完全的线程安全的时候使用Hashtable，而如果你使用Java5或以上的话，请使用ConcurrentHashMap吧


#### HashSet 和 HashMap 区别
![](/assets/pic.jpg)

#### HashMap 和 ConcurrentHashMap 的区别
1.ConcurrentHashMap对整个桶数组进行了分割分段(Segment)，然后在每一个分段上都用lock锁进行保护，相对于HashTable的synchronized锁的粒度更精细了一些，并发性能更好，而HashMap没有锁机制，不是线程安全的。（JDK1.8之后ConcurrentHashMap启用了一种全新的方式实现,利用CAS算法。）

2.HashMap的键值对允许有null，但是ConCurrentHashMap都不允许。










