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

#### HashSet如何检查重复
> 当你把对象加入HashSet时，HashSet会先计算对象的hashcode值来判断对象加入的位置，同时也会与其他加入的对象的hashcode值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同hashcode值的对象，这时会调用equals（）方法来检查hashcode相等的对象是否真的相同。如果两者相同，HashSet就不会让加入操作成功。（摘自我的Java启蒙书《Head fist java》第二版）

####  hashCode（）与equals（）的相关规定：

- 如果两个对象相等，则hashcode一定也是相同的

- 两个对象相等,对两个equals方法返回true

- 两个对象有相同的hashcode值，它们也不一定是相等的

- equals方法被覆盖过，则hashCode方法也必须被覆盖

- hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写hashCode()，则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）。

####  ==与equals的区别

- 1.==是判断两个变量或实例是不是指向同一个内存空间 equals是判断两个变量或实例所指向的内存空间的值是不是相同

- 2.==是指对内存地址进行比较 equals()是对字符串的内容进行比较- 
- 3.==指引用是否相同 equals()指的是值是否相同













