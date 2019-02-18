#### HashMap的内部实现原理

1. HashMap可以接受null键值和值，而HashTable则不能，HashMap是非synchronized的；存储的是键值对。

2. HashMap是基于hashing原理,使用put\(key,value\)存储对象到HashMap中，使用get\(key\)从HashMap中获取对象，当我们给put方法传递键和值时，我们先对键调用hashCode\(\)方法，返回的hashCode用于找到bucket位置来存储键对象和值对象，作为Map.Entry.

3. 如果两个对象hashCode相同：① 存储时：他们会找到相同的bucket位置，发生碰撞，因为HashMap使用链表存储对象（每个Map.Entry都有一个next指针），这个Entry会存储在链表中。② 获取时:会用hashCode找到bucket位置，然后调用key.equals\(\)方法找到链表中正确的节点.最终找到要找的值对象.

   减少碰撞：使用final修饰的对象、或不可变的对象作为键，使用\(Integer、String\)（是不可变、final的,而且已经重写了equals和hashCode方法）这样的wrapper类作为键是非常好的，（我们可以使用自定义的对象作为键吗？答：当然可以，只要它遵守了equals和hashCode方法定义规则，并且当对象插入到Map中之后将不会再改变。）

4. HashMap负载因子默认是0.75，可设置，当map填满了75%的bucket时候，将会创建原来HashMap大小两倍的bucket数组，来重新调整map的大小，并将原来的对象放入新的bucket数组中,这个过程叫做rehashing，因为它调用hash方法找到新的bucket位置。

5. 重新调整map大小可能会发生竞争问题：如果两个线程都发现HashMap需要调整大小了，它们都会尝试进行调整，在调整中，存储在链表中的元素的次序会反过来，因为移动bucket位置的时候，HashMap并不会将元素放在链表的尾部，而是放在头部，这是为了避免尾部遍历，如果条件竞争发生了，就死循环了。



HashMap源码解析（JDK8）

https://blog.csdn.net/zxt0601/article/details/77413921



