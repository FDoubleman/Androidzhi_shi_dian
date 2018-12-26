### 集合框架

> Java的集合类主要由两个接口派生而出：**Collection**和**Map**,Collection和Map是Java集合框架的根接口。

**Collection 结构图:**

![](/assets/collection.webp)Collection是接口 **Set, Queue, List **的父接口

> Map实现类用于**保存具有映射关系的数据**。Map保存的每项数据都是key-value对，也就是由key和value两个值组成。**Map里的key是不可重复**的，key用户标识集合里的每项数据。

Collection用法有：添加元素，删除元素，返回Collection集合的个数以及清空集合等。

![](/assets/collect方法.webp)

**Map 结构图：**

![](/assets/map.webp)**Set集合：**

**Set集合不允许包含相同的元素**，如果试图把两个相同的元素加入同一个Set集合中，则添加操作失败，add\(\)方法返回false，且新元素不会被加入。



**List集合：**

**List集合代表一个元素有序、可重复的集合**，集合中每个元素都有其对应的顺序索引



**Queue集合：**

**Queue模拟队列这种数据结构**，队列通常是指“**先进先出”\(FIFO，first-in-first-out\)的容器**。





**总结：**

