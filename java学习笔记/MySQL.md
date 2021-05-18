## MySQL架构

![查看源图像](https://th.bing.com/th/id/R74c321047ca0bb235d9f3f47de719180?rik=b4KfiDCJFQuv3Q&riu=http%3a%2f%2fwww.mysql.com%2fcommon%2fimages%2fPSEA_diagram.jpg&ehk=ytdXlA%2bVJs6m9hsN5zGwC%2fl%2b4gEHunw8FQZN0bK4iKA%3d&risl=&pid=ImgRaw)

![img](file:///C:\Users\wang\AppData\Roaming\Tencent\Users\1227883481\QQ\WinTemp\RichOle\E3VE}C42MQ{XC[I@O@I%AJX.png)

主要是服务层和引擎层。

## join图

[详细链接可参考](https://blog.csdn.net/weixin_46273997/article/details/112977917)

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

手写顺序

![image-20210518100854961](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210518100854961.png)

机读

![image-20210518101947400](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210518101947400.png)
