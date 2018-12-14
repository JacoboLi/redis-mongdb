作业一、Redis和	Memcached的区别 
1.	Redis不仅仅支持简单的k/v类型的数据，同时提供了list、set、hash等数据结构的存储；Memcached所有的值均是简单的字符串
2.	Redis支持数据的备份，即master-slave模式的数据备份
3.	Redis支持数据的持久化，可以将内存中的数据保持在磁盘中，重启的时候可以再次加载进行使用
4.	Redis和Memcache都是将数据存放在内存中，都是内存数据库。不过memcache还可用于缓存其他东西，例如图片、视频等等
5.	虚拟内存--Redis当物理内存用完时，可以将一些很久没用到的value 交换到磁盘
6.	过期策略--memcache在set时就指定，例如set key1 0 0 8,即永不过期。Redis可以通过例如expire 设定，例如expire name 10
7.	分布式--设定memcache集群，利用magent做一主多从;redis可以做一主多从。都可以一主一从
8.	存储数据安全--memcache挂掉后，数据没了；redis可以定期保存到磁盘（持久化）
9.	灾难恢复--memcache挂掉后，数据不可恢复; redis数据丢失后可以通过aof恢复
10.	应用场景不一样：Redis出来作为NoSQL数据库使用外，还能用做消息队列、数据堆栈和数据缓存等；Memcached适合于缓存SQL语句、数据集、用户临时性数据、延迟查询数据和session等
11.	memcached是多线程，非阻塞IO复用的网络模型；redis使用单线程的IO复用模型
12.	Memcached提供了cas命令，可以保证多个并发访问操作同一份数据的一致性问题。 Redis没有提供cas 命令，并不能保证这点，不过Redis提供了事务的功能，可以保证一串 命令的原子性，中间不会被任何操作打断
13.	Memcached本身并不支持分布式, 只能采用客户端实现分布式存储; Redis更偏向于在服务器端构建分布式存储

作业二、redis五个类型的运用场景
1.	String字符串：
String数据结构是简单的key-value类型，value其实不仅可以是String，也可以是数字。 
常规key-value缓存应用； 
常规计数：微博数，粉丝数等。
2.	Hash
Redis hash是一个string类型的field和value的映射表，hash特别适合用于存储对象。 
存储部分变更的数据，如用户信息等。
3.	List 
list就是链表，略有数据结构知识的人都应该能理解其结构。
使用list可以实现最新消息排行等功能；list的另一个应用就是消息队列
4.	Set
set就是一个集合，集合的概念就是一堆不重复值的组合。利用Redis提供的set数据结构，可以存储一些集合性的数据。set中的元素是没有顺序的。
应用场景：在微博应用中，可以将一个用户所有的关注人存在一个集合中，将其所有粉丝存在一个集合。
Redis还为集合提供了求交集、并集、差集等操作。
5.	Sorted Set
和Set相比，sorted set 增加了一个权重参数score，使得集合中的元素能够按score进行有序排列。
应用场景：排行榜应用，取TOPN操作 ：比如在线游戏的排行榜

