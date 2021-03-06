# <<数据结构与算法之美>> 阶段学习记录
**1. 什么是数据结构？什么是算法？**

1. 从广义上将，数据结构就是指一组数据的存储结构。算法就是操作数据的一组方法。
2. 从狭义上讲，是指某些著名的数据结构和算法，比如队列、栈、堆、二分查找、动态规划等。

**2.那数据结构和算法有什么关系呢？**

- 数据结构和算法是相辅相成的，数据结构是为算法服务的，算法要作用在特定的数据结构之上。为什么这么说呢？比如，因为数组具有随机访问的特点，常用的二分查找算法需要用数组来存储数据。但如果我们选择链表这种数据结构，二分查找算法就无法工作了，因为链表并不支持随机访问。

**10 个数据结构：数组、链表、栈、队列、散列表、二叉树、堆、跳表、图、Trie 树；**
**10 个算法：递归、排序、二分查找、搜索、哈希算法、贪心算法、分治算法、回溯算法、动态规划、字符串匹配算法。**



### 第一阶段

#### 1.复杂度分析（M，10分）
  - [复杂度分析（上）：如何分析算法的执行效率和资源消耗](https://time.geekbang.org/column/article/40036)
  - [复杂度分析（下）：浅析最好、最坏、平均、均摊时间复杂度](https://time.geekbang.org/column/article/40447)
- 大 O 复杂度表示法

  - 所有代码的执行时间 T(n) 与每行代码的执行次数 n 成正比。T(n)=O(f(n)),其中，T(n) 我们已经讲过了，它表示代码执行的时间；n 表示数据规模的大小；f(n) 表示每行代码执行的次数总和。大 O 时间复杂度实际上并不具体表示代码真正的执行时间，而是表示代码执行时间随数据规模增长的变化趋势，所以，也叫作渐进时间复杂度（asymptotic time complexity），简称时间复杂度。当n很大时，公式中的低价、常量、系数三部分并不左右增长趋势，所以都可以忽略。我们只需要记录一个最大量级就可以了。有三个比较实用的方法可以分享：
    1. 只关注循环执行次数最多的一段代码
    2. 法法则：总复杂度等于量级最大的那段代码的复杂度
    3. 乘法法则：嵌套代码的复杂度等于嵌套内外代码复杂度的乘积

- 几种常见时间复杂度实例分析

  - 常量阶 O(1)
  - 对数阶O(logn)
  - 线性阶O(n)
  - 线性对数阶O(nlogn)
  - 平方阶O(n^2)、立方阶O(n^3)...k次方阶O(n^k)
  - 指数阶O(2^n)
  - 阶乘阶O(n!)

- 对于以上复杂度量级，我们可以粗略地分为两类，多项式量级和非多项式量级。其中，非多项式量级只有两个：O(2^n) 和 O(n!)。当数据规模 n 越来越大时，非多项式量级算法的执行时间会急剧增加，求解问题的执行时间会无限增长。
  		O(1):一般情况下，只要算法中不存在循环语句、递归语句，即使有成千上万行的代码，其时间复杂度也是Ο(1)。
  		O(logn)、O(nlogn):对于循环来讲，假设以2为底，根据等比数列：2^x = n => x=log2n。
  		如果一段代码的时间复杂度是 O(logn)，我们循环执行 n 遍，时间复杂度就是 O(nlogn) 了。归并排序和快速排序的时间复杂度都是O(nlogn)

- O(m+n)、O(m*n)：
  		时间复杂度的全称是渐进时间复杂度，表示算法的执行时间与数据规模之间的增长关系。类比一下，空间复杂度全称就是渐进空间复杂度，表示算法的存储空间与数据规模之间的增长关系。

- 最好情况时间复杂度（best case time complexity）、最坏情况时间复杂度（worst case time complexity）、平均情况时间复杂度（average case time complexity）、均摊时间复杂度（amortized time complexity）

  - 最好情况时间复杂度就是，在最理想的情况下，执行这段代码的时间复杂度。
    		最坏情况时间复杂度就是，在最糟糕的情况下，执行这段代码的时间复杂度。
    		平均情况时间复杂度，考虑了整个计算过程的加权平均值
    		均摊时间复杂度就是一种特殊的平均时间复杂度
    		对一个数据结构进行一组连续操作中，大部分情况下时间复杂度都很低，只有个别情况下时间复杂度比较高，而且这些操作之间存在前后连贯的时序关系，这个时候，我们就可以将这一组操作放在一块儿分析，看是否能将较高时间复杂度那次操作的耗时，平摊到其他那些时间复杂度比较低的操作上。而且，在能够应用均摊时间复杂度分析的场合，一般均摊时间复杂度就等于最好情况时间复杂度。

  

#### 2.数组、栈、队列（E，8分）
##### 2.1 数组
  - [数组：为什么很多编程语言中数组都从0开始编号？](https://time.geekbang.org/column/article/40961)

  - 数组是最基本的数据类型，我们要透过现象看本质，这4个方面会帮你理解它的精髓

    1. 数组如何实现随机访问
       1. 数组（Array）是一种线性表数据结构。它用一组连续的内存空间，来存储一组具有相同类型的数据。
       2. 第一是线性表（Linear List）。顾名思义，线性表就是数据排成像一条线一样的结构。每个线性表上的数据最多只有前和后两个方向。其实除了数组，链表、队列、栈等也是线性表结构。而与它相对立的概念是非线性表，比如二叉树、堆、图等。之所以叫非线性，是因为，在非线性表中，数据之间并不是简单的前后关系。
       3. 第二个是连续的内存空间和相同类型的数据。正是因为这两个限制，它才有了一个堪称“杀手锏”的特性：“随机访问”。数组支持随机访问，根据下标随机访问的时间复杂度为 O(1)。
    2. 低效的“插入”和“删除”
       1. 为了保证内存空间的连续而变得低效
    3. 数组的访问越界问题
    4. 容器能否完全替代数组
       1. 容器只不过是更高级的数据结构，把常用的算法都封装了。

- 为什么数组要从 0 开始编号，而不是从 1 开始呢？
  从数组存储的内存模型上来看，“下标”最确切的定义应该是“偏移（offset）”。

  
  > 数组和链表的区别：链表适合插入、删除，时间复杂度O(1)，数组支持随机访问，根据下标随机访问的时间复杂度为O(1)；数组为何从0开始编号而不是从1开始编号，从数组存储的内存模型上看，“下标”最确切的定义是“偏移（offset）”，如果从0开始计算公式为 a[k]_address = base_address + k * type_size，如果从1开始计算，内存地址公式变为 a[k]_address = base_address + k * type_size,cpu多了一次减法的指令。
##### 2.2 栈
  - [栈：如何实现浏览器的前进和后退功能？](https://time.geekbang.org/column/article/41222)
  - 
  > 栈是一种操作受限的数据结构，只支持入栈和出栈操作。后进先出是最大特点。栈既可以用数组实现，也可以链表实现，不管基于数组还是链表，入栈、出栈的时间复杂度都为O(1)，可以支持动态扩容的顺序栈，需要重点掌握它的均摊时间复杂度分析方法。
  `为什么函数调用用栈来保存临时变量呢？其他数据结构不行吗？其实，我们不一定非要用栈来保存临时变量，只不过如果这个函数调用符合后进先出的特性，用栈这种数据结构来实现，是最顺理成章的选择。从调用函数进入被调用函数，对于数据来说，变化的是什么呢？是作用域。所以根本上，只要能保证每进入一个新的函数，都是一个新的作用域就可以。而要实现这个，用栈就非常方便。在进入被调用函数的时候，分配一段栈空间给这个函数的变量，在函数结束的时候，将栈顶复位，正好回到调用函数的作用域内。`
##### 2.3 队列
  - [队列：队列在线程池等有限资源池中的应用](https://time.geekbang.org/column/article/41330)
  > 队列（queue）是只允许在一端进行插入操作，而在另一端进行删除操作的线性表。允许插入的一端为队尾，允许删除的一端为堆对头。队列不允许在中间部位进行操作。队列这种数据结构很基础，平时的业务开发不大可能从零开始实现一个队列，甚至都不会直接用到。而一些具有特殊特性的队列应用却比较广泛，比如阻塞队列和并发队列。**阻塞队列**就是在队列基础上增加了阻塞操作。简单来说，就是在队列为空的时候，从队头取数据会被阻塞。因为此时还没有数据可取，直到队列中有了数据才能返回；如果队列满了，那么插入数据的操作会被阻塞，直到队列中有空闲位置后再插入数据，然后再返回。线程安全的队列叫做**并发队列**，最简单直接的实现方式直接在enqueue()、dequeue()方式上加锁，但是锁力度大并发度会比较低，同一时刻仅允许一个存或者取取操作。

#### 3.链表（M，9分）
  - [链表（上）：如何实现LRU缓存淘汰算法?](https://time.geekbang.org/column/article/41013)
  - 如何用链表来实现 LRU 缓存淘汰策略呢？
  > 数组需要一块连续的内存空间来存储，链表通过“指针”将一组零散的内存块串联起来使用。常见的链表结构：单链表、双链表、循环链表。循环链表的优点是从链尾到链头比较方便，当处理的数据具有环型结构特点时，特别适合采用环型链表，比如约瑟夫问题。分析数组与链表的时间复杂度和空间复杂度。数组简单易用，在实现上使用的是连续的内存空间，可以借助CPU的缓存机制，预读数组中的数据，所以访问效率更高。而链表在内存中并不是连续存储，所以对CPU缓存不友好，没办法有效预读。
  - 如何基于链表实现LRU缓存淘汰算法？
    - 我们维护一个有序单链表，越靠近尾部的结点是越早之前访问的，当有一个新的数据被访问时，我们从链表头开始顺序遍历链表
    - 1.如果此数据之前已经被缓存在链表中了，我们遍历得到这个数据对应的结点，并将其从原来的位置删除，然后再插入到链表的头部。
    - 2.如果此数据没有在缓存链表中，又可以分为两种情况：一 如果此时缓存未满，则将此节点直接插入到链表的头部；二 如果此时缓存已满，则链表尾结点删除，将新的数据插入链表的头部。
  - [链表（下）：如何轻松写出正确的链表代码？](https://time.geekbang.org/column/article/41149)
  > 几个写链表代码技巧：一 理解指针或引用的含义 二 警惕指针丢失和内存泄漏 三 利用哨兵简化实现难度 四 重点留意边界条件处理 五 举例画图，辅助思考 六 多写多练，没有捷径
  - 经常用来检查链表代码是否正确的边界条件有这几个：
  - 如果链表为空时，代码是否能正常工作？
  - 如果链表只包含一个节点时，代码是否能正常工作？
  - 如果链表只包含两个节点时，代码是否能正常工作？
  - 代码逻辑在处理头节点和尾结点的时候，是否能正常工作？



#### 4.递归（H，10分）
  - [递归：如何用三行代码找到“最终推荐人”？](https://time.geekbang.org/column/article/41440)
  > 递归需要满足的三个条件：1.一个问题的解可以分解为几个子问题的解 2.这个问题与分解之后的子问题，除了数据规模不同，求解思路完全一样 3.存在递归终止条件。写递归代码最关键的是写出递推公式，找到终止条件。总结：**写递归代码的关键就是找到如何将最大问题分解为小问题的规律，并且基于此写出递推公式，然后再推敲终止条件，最后将递推公式和终止条件翻译成代码。**
  - [递归树：如何借助树来求解递归算法的时间复杂度？](https://time.geekbang.org/column/article/69388)
  > **借助递归树来分析递归算法的时间复杂度。**

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
  - [散列表（上）：Word文档中的单词拼写检查功能是如何实现的？](https://time.geekbang.org/column/article/64233)
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

#### 1.四种算法思想 H 10

#### 2.跳表 M 6

####	3.拓扑排序、Dijkstra算法，A*算法 H 5

#### 4.B+树 M 5

####	5.位图 E6




### 第四阶段

#### 1.BM、KMP、AC自动机 H 3

####	2.红黑树 H 3

####	3.哈希算法 E 3

####	4.高级篇、实践篇的其他内容

