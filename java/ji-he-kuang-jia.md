### 集合框架

> Java的集合类主要由两个接口派生而出：**Collection**和**Map**,Collection和Map是Java集合框架的根接口。

**Collection 结构图:**

![](/assets/collection.webp)Collection是接口 **Set, Queue, List **的父接口

> Map实现类用于**保存具有映射关系的数据**。Map保存的每项数据都是key-value对，也就是由key和value两个值组成。**Map里的key是不可重复**的，key用户标识集合里的每项数据。

Collection用法有：添加元素，删除元素，返回Collection集合的个数以及清空集合等。

![](/assets/collect方法.webp)

---

**Map 结构图：**

![](/assets/map.webp)

---

#### 一、Collection:

**Set集合：**

> **Set集合不允许包含相同的元素**，如果试图把两个相同的元素加入同一个Set集合中，则添加操作失败，add\(\)方法返回false，且新元素不会被加入。

**List集合：**

> **List集合代表一个元素有序、可重复的集合**，集合中每个元素都有其对应的顺序索引

**Queue集合：**

> **Queue模拟队列这种数据结构**，队列通常是指“**先进先出”\(FIFO，first-in-first-out\)的容器**。

---

#### 二、 Map

##### 

##### HashMap：

> **HashMap是基于哈希表的Map接口的非同步实现**，HashMap采用数组+链表实现，即使用链表处理冲突，同一hash值的链表都存储在一个链表里。但是当链表中的元素较多，即hash值相等的元素较多时，通过key值依次查找的效率较低。而**JDK1.8中，HashMap采用数组+链表+红黑树实现**，当链表长度超过阈值（8）时，将链表转换为红黑树，这样大大减少了查找时间。

##### LinkedHashMap：

> HashSet有一个LinkedHashSet子类，HashMap也有一个LinkedHashMap子类；
>
> LinkedHashMap使用双向链表来维护key-value对的次序。
>
> LinkedHashMap需要维护元素的插入顺序，因此性能略低于HashMap的性能。
>
> 迭代输出LinkedHashMap的元素时，将会按照添加key-value对的顺序输出。
>
> **LinkedHashMap=散列表+循环双向链表**

**TreeMap**

> TreeMap是SortedMap接口的实现类。
>
> TreeMap 是一个**有序的key-value集合**，它是通过红黑树实现的，每个key-value对即作为红黑树的一个节点。

**总结：**

**Collection**
**- list**
    - Arraylist：数组（查询快,增删慢 线程不安全,效率高 ）
    - Vector：数组（查询快,增删慢 线程安全,效率低 ）
    - LinkedList：链表（查询慢,增删快 线程不安全,效率高 ）
    
**- set**
    - HashSet（无序，唯一）:哈希表或者叫散列集(hash table)
    - LinkedHashSet：链表和哈希表组成 。 由链表保证元素的排序 ， 由哈希表证元素的唯一性
    - TreeSet（有序，唯一）：红黑树(自平衡的排序二叉树。)
     
**- Map**
    - HashMap：基于哈希表的Map接口实现（哈希表对键进行散列，Map结构即映射表存放键值对）
    - LinkedHashMap:HashMap 的基础上加上了链表数据结构
    - HashTable:哈希表
    - TreeMap:红黑树（自平衡的排序二叉树）





