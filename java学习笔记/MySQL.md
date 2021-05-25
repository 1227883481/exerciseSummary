## MySQL基础

### 关于group以及having的使用（包括having与where的区别）

参考知乎文章：https://zhuanlan.zhihu.com/p/46925457

## MySQL架构

![查看源图像](https://th.bing.com/th/id/R74c321047ca0bb235d9f3f47de719180?rik=b4KfiDCJFQuv3Q&riu=http%3a%2f%2fwww.mysql.com%2fcommon%2fimages%2fPSEA_diagram.jpg&ehk=ytdXlA%2bVJs6m9hsN5zGwC%2fl%2b4gEHunw8FQZN0bK4iKA%3d&risl=&pid=ImgRaw)

![img](file:///C:\Users\wang\AppData\Roaming\Tencent\Users\1227883481\QQ\WinTemp\RichOle\E3VE}C42MQ{XC[I@O@I%AJX.png)

主要是服务层和引擎层。

## join图

[详细链接可参考](https://blog.csdn.net/weixin_46273997/article/details/112977917)

含义举例的链接可参考：https://blog.csdn.net/lu0422/article/details/78892497

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210122095055633.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjI3Mzk5Nw==,size_16,color_FFFFFF,t_70#pic_center)

## SQL语句执行顺序

```sql
(8) SELECT (9)DISTINCT<Select_list>
(1) FROM <left_table> (3) <join_type>JOIN<right_table>
(2) ON<join_condition>
(4) WHERE<where_condition>
(5) GROUP BY<group_by_list>
(6) WITH {CUBE|ROLLUP}
(7) HAVING<having_condtion>
(10) ORDER BY<order_by_list>
(11) LIMIT<limit_number>
```

**手写顺序**：

![image-20210518100854961](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210518100854961.png)

**机读**：

![image-20210518101947400](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210518101947400.png)

## MySQL Explain 之 type 详解

参考链接 https://learnku.com/articles/44154

## 读锁和写锁

锁是并发控制中最核心的概念之一，在MySQL中的锁分两大类，一种是读锁，一种是写锁，读锁也可以称为共享锁（shared lock），写锁也通常称为排它锁（exclusive lock）。

自己总结：

**读锁**：**当前进程**可以读，不可以写（更新）被锁的表（**只读**），但是不可以操作其他表（必须释放锁之后才能操作其他表，否则容易遗忘释放锁导致事故）。

​			其他进程可以读，写的时候会阻塞，直到进程一中锁被释放，立即执行写操作。可以随意操作其他表。

**写锁**：当前进程可以任意（**读写**）操作该被锁表，但是不可以操作其他表（必须释放锁之后才能操作其他表，否则容易遗忘释放锁导致事故）。

​			其他进程操作（无论读写）被锁表会阻塞，直至进程一锁被释放，立即执行未完成操作。可以随意操作其他表。

![image-20210524151326612](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210524151326612.png)

## 行锁和表锁

如果索引失效（比如查询语句中vachar类型没有加单引号，mySQL会自动优化导致索引失效，此时行锁也会变表锁），表锁
