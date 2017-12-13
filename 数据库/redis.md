# redis  
redis命令参考:http://doc.redisfans.com/  
- [redis简介](#1)  
- [对比redis与memcached](#2)

<h2 id="1">redis简介</h2>
Redis是一个速度非常快的非关系数据库（non-relational database），它可以存储键（key）与5种不同类型的值（value）之间的映射（mapping），可以将存储在内存的键值对数据持久化到硬盘，可以使用复制特性来扩展读性能，还可以使用客户端分片1来扩展写性能，接下来的几节将分别介绍Redis的这几个特性
<h2> 对比redis与memcached </h2>
共同点:  
两者都属于非关系型数据库.
都用  
深层剖析对比redis与memcached的区别:https://www.biaodianfu.com/redis-vs-memcached.html