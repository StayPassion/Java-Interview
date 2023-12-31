# Redis

## 缓存

### 缓存穿透

**缓存穿透**：查询一个**不存在**的数据，mysql查询不到数据也不会直接写入缓存，就会导致每次请求都查数据库

**解决方案**：

1. 缓存空数据，查询返回的数据为空，仍把这个空结果进行缓存。`{key:1,value:null}`

   <img src="https://raw.githubusercontent.com/StayPassion/Java-Interview/master/docs/redis-picture/1.png" alt="3" style="zoom:60%;" />

   **优点：**简单

   **缺点：**消耗内存，可能会发生不一致的问题

2. 布隆过滤器。

   <img src="https://raw.githubusercontent.com/StayPassion/Java-Interview/master/docs/redis-picture/2.png" alt="3" style="zoom:60%;" />

   **优点：**内存占用较少，没有多余key

   **缺点：**实现复杂，存在误判

   

**布隆过滤器**

**bitmap（位图）**：相当于是一个以（bit）位为单位的数组，数组中每个单元只能存储二进制数0或1

**布隆过滤器作用：**布隆过滤器可以用于检索一个元素是否在一个集合中。

<img src="https://raw.githubusercontent.com/StayPassion/Java-Interview/master/docs/redis-picture/3.png" alt="3" style="zoom:60%;" />



<img src="https://raw.githubusercontent.com/StayPassion/Java-Interview/master/docs/redis-picture/4.png" alt="3" style="zoom:60%;" />

**误判率**：数组越小误判率就越大，数组越大误判率就越小，但是同时带来了更多的内存消耗。

**布隆过滤器实现方案**：Redisson，Guava



### 缓存击透

