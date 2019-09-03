# <<数据结构与算法之美>> 阶段学习记录
### 第一阶段
#### 1.复杂度分析（M，10分）
  - [复杂度分析（上）：如何分析算法的执行效率和资源消耗](https://time.geekbang.org/column/article/40036)
  - [复杂度分析（下）：浅析最好、最坏、平均、均摊时间复杂度](https://time.geekbang.org/column/article/40447)
  > `大O时间复杂度表示法：表示代码执行时间随着数据规模增长的变化趋势，一般情况下，只要算法中不存在循环语句、递归语句，即使有成千上万行的代码，其时间复杂度也是O(1)`;空间复杂度表示算法的存储空间与数据规模之间的增长关系，常见的有O(1)、O(n)、O(n2 );最好时间复杂度、最坏时间复杂度、平均时间复杂度(考虑概率论的知识)、均摊时间复杂度

#### 2.数组、栈、队列（E，8分）
##### 2.1 数组
  - [数组：为什么很多编程语言中数组都从0开始编号？](https://time.geekbang.org/column/article/40961)
  > 数组和链表的区别：链表适合插入、删除，时间复杂度O(1)，数组支持随机访问，根据下标随机访问的时间复杂度为O(1)；数组为何从0开始编号而不是从1开始编号，从数组存储的内存模型上看，“下标”最确切的定义是“偏移（offset）”，如果从0开始计算公式为 a[k]_address = base_address + k * type_size，如果从1开始计算，内存地址公式变为 a[k]_address = base_address + k * type_size,cpu多了一次减法的指令。
##### 2.2 栈
  - [栈：如何实现浏览器的前进和后退功能？](https://time.geekbang.org/column/article/41222)
##### 2.3 队列
  - [队列：队列在线程池等有限资源池中的应用](https://time.geekbang.org/column/article/41330)
  
#### 3.链表（M，9分）
  - [链表（上）：如何实现LRU缓存淘汰算法?](https://time.geekbang.org/column/article/41013)
  - [链表（下）：如何轻松写出正确的链表代码？](https://time.geekbang.org/column/article/41149)

#### 4.递归（H，10分）
  - [递归：如何用三行代码找到“最终推荐人”？](https://time.geekbang.org/column/article/41440)
  - [递归树：如何借助树来求解递归算法的时间复杂度？](https://time.geekbang.org/column/article/69388)

#### 5.排序、二分查找（E，7分）
##### 5.1 冒泡排序、插入排序、选择排序
  - [排序（上）：为什么插入排序比冒泡排序更受欢迎？](https://time.geekbang.org/column/article/41802)
##### 5.2 归并排序、快速排序
  - [排序（下）：如何用快排思想在O(n)内查找第K大元素？](https://time.geekbang.org/column/article/41913)
##### 5.3 桶排序、计数排序、基数排序
  - [线性排序：如何根据年龄给100万用户数据排序？](https://time.geekbang.org/column/article/42038)
##### 5.4 排序优化
  - [排序优化：如何实现一个通用的、高性能的排序函数？](https://time.geekbang.org/column/article/42359)
##### 5.5 二分查找
  - [二分查找（上）：如何用最省内存的方式实现快速查找功能？](https://time.geekbang.org/column/article/42520)

### 第二阶段
#### 1.散列表（M，8分）
  - [散列表（上）：Word文档中的单词拼写检查功能是如何实现的？](https://github.com/iostalks/Algorithms/blob/master/64233)
  - [散列表（中）：如何打造一个工业级水平的散列表？](https://time.geekbang.org/column/article/64586)
  - [散列表（下）：为什么散列表和链表经常会一起使用？](https://time.geekbang.org/column/article/64858)
#### 2.二叉树（M，9分）
##### 2.1 二叉树基础
  - [二叉树基础（上）：什么样的二叉树适合用数组来存储？](https://time.geekbang.org/column/article/67856)
  - [二叉树基础（下）：有了如此高效的散列表，为什么还需要二叉树？](https://time.geekbang.org/column/article/68334)
##### 2.2 平衡二叉树
  - [红黑树（上）：为什么工程中都用红黑树这种二叉树？](https://time.geekbang.org/column/article/68638)
  - [红黑树（下）：掌握这些技巧，你也可以实现一个红黑树](https://time.geekbang.org/column/article/68976)
  - 
#### 3.堆和堆排序（M，9分）
  - [堆和堆排序：为什么说堆排序没有快速排序快？](https://time.geekbang.org/column/article/69913)
  - [堆的应用：如何快速获取到Top 10最热门的搜索关键词？](https://time.geekbang.org/column/article/70187)
#### 4.BF/RK字符串匹配算法（E，7分）
  - [字符串匹配基础（上）：如何借助哈希算法实现高效字符串匹配？](https://time.geekbang.org/column/article/71187)
#### 5.Trie树（M，7分）
  - [Trie树：如何实现搜索引擎的搜索关键词提示功能？](https://time.geekbang.org/column/article/72414)
#### 6.图的表示（E，8分）
##### 6.1 无向图、有向图、带权图
  - [图的表示：如何存储微博、微信等社交网络中的好友关系？](https://time.geekbang.org/column/article/70537)
#### 7.深度、广度优先搜索（H，8分）
  - [深度和广度优先搜索：如何找出社交网络中的三度好友关系？](https://time.geekbang.org/column/article/70891)

### 第三阶段


### 第四阶段
