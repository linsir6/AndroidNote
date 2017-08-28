# HashTable和HashMap的异同

- HashTable

    1. Hashtable继承于Dictionary字典，实现Map接口  

    2. 键、值都不能是空对象 
 
    3. 多次访问，映射元素的顺序相同  
 
    4. 线程安全 
 

    5. hash算法 ，Hashtable则直接利用key本身的hash码来做验证 

    6. 数据遍历的方式 Iterator （支持fast-fail）和 Enumeration （不支持fast-fail） 
 
    7. 缺省初始长度为11，内部都为抽象方法，需要 它的实现类一一作自己的实现 

备注：程序在对 collection 进行迭代时，某个线程对该 collection 在结构上对其做了修改，这时迭代器就会抛出 ConcurrentModificationException 异常信息，从而产生 fail-fast。

----

 - HashMap

    1. HashMap继承于AbstractMap抽象类 
 
    2. 键和值都可以是空对象  
 
    3. 多次访问，映射元素的顺序可能不同  
 
    4. 非线程安全 
 HashMap可以通过下面的语句进行同步：
``Map m = Collections.synchronizeMap(hashMap);``
 
    5. 检测是否含有key时，HashMap内部需要将key的hash码重新计算一边再检测数据遍历的方式 Iterator （支持fast-fail）
 
    6. 缺省初始长度为16，其内部已经实现了Map所需 要做的大部分工作， 它的子类只需要实现它的少量方法

