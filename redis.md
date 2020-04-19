# redis

* 数据类型 String ，list，hash，set，sortset
* String 的操作 set key value     ge

```java
set key value 
get key
查看所有的key  keys *
删除key del key
设置过期时间  setex key time(秒) value
设置多个 mset key1 value1 key2 value2
    mget key1 key2
```

* redis 有16个数据库 切换数据库 select  0
* hash 用来存储对象  如果存的值中间有空格，需要用"" 引起来 key不能重复

```
存
hset user name tom
hset user age 10

hmset user name marry age 20
取
hget user name 
hmget user name age
一次取出整个对象 hgetall user
删除 hdel user name

hlen 统计hash有多少个元素  hlen user
hexists user name  查看hash中有没有某一字段
```

* list 本质是链表 元素是有序的    管道一样，取出的顺序刚好和存放的顺序相反  栈的感觉

```
lpush hero aaa bbb ccc
lrange hero 0 -1 (全取)    ccc bbb aaa  取出的顺序
rpush ddd eee 在尾部添加  ccc bbb aaa ddd eee
rpop hero （从右边弹出一个数据）
lpop hero  ccc 原list就只有四个元素了
del hero
llen hero 查看list中存放元素的个数
```

* set 底层是hashtable的数据结构 元素无序 ，元素不能重复

```
sadd email 11.qq.com 22.qq.com
smembers email  取出全部元素
重复数据添加不进去
sismember value  判断set中有没有该元素  有返回1 ，没有返回0
srem email value  删除某一个元素
```

**redis连接池**

