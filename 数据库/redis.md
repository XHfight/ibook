# redis与memcached  
redis命令参考:http://doc.redisfans.com/  
- [redis简介](#1)  
- [对比redis与memcached](#2)
- [redis与memcached应用场景](#3)

<h2 id="1">redis简介</h2>
Redis是一个速度非常快的非关系数据库（non-relational database），它可以存储键（key）与5种不同类型的值（value）[5种: String, Hash, List, set, Sorted Set ]之间的映射（mapping），可以将存储在内存的键值对数据持久化到硬盘，可以使用复制特性来扩展读性能，还可以使用客户端分片来扩展写性能，接下来的几节将分别介绍Redis的这几个特性
<h2> 对比redis与memcached </h2>
[__共同点__]:  
两者都属于非关系型数据库,都是基于内存的数据存储系统.  
[<font color=red>__区别__</font>]:
1. __Redis支持服务器端的数据操作__：Redis相比Memcached来说，拥有更多的数据结构和并支持更丰富的数据操作，memcached只能一个key对应一个value,redis可以有5种不同的value.
通常在Memcached里，你需要将数据拿到客户端来进行类似的修改再set回去。这大大增加了网络IO的次数和数据体积。在Redis中，这些复杂的操作通常和一般的GET/SET一样高效。所以，如果需要缓存能够支持更复杂的结构和操作，那么Redis会是不错的选择。  
2. __内存使用效率对比__：使用简单的key-value存储的话，Memcached的内存利用率更高，而如果Redis采用hash结构来做key-value存储，由于其组合式的压缩，其内存利用率会高于Memcached。  
3. __性能对比__：由于Redis只使用单核，而Memcached可以使用多核，所以平均每一个核上Redis在存储小数据时比Memcached性能更高。而在100k以上的数据中，Memcached性能要高于Redis，虽然Redis最近也在存储大数据的性能上进行优化，但是比起Memcached，还是稍有逊色。  
4. __数据备份__:
Redis支持数据的备份，即master-slave模式的数据备,当redis服务器挂掉时,可以进行数据恢复。  
5. __数据持久化支持__:Redis支持数据的持久化，可以将内存中的数据保持在磁盘中，重启的时候可以再次加载进行使用。  

	[深层剖析对比redis与memcached的区别]
https://www.biaodianfu.com/redis-vs-memcached.html  
https://www.cnblogs.com/linuxprobe/p/5922558.html  

<h2 id="3">redis和memcached应用场景:</h2> 
一般用来做缓存,在服务器中常用来存储一些需要频繁调取的数据，这样可以大大节省系统直接读取磁盘来获得数据的I/O开销，更重要的是可以极大提升速度.例如:通过缓存数据库查询结果，减少数据库访问次数，以提高动态Web应用的速度、提高可扩展性。  
如果想要实现数据持久化或者存储的value是别的数据结构,就要选择redis.  
