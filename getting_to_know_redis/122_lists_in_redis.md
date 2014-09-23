# Redis的Lists类型

在键值对存储的类型中，Redis独特支持一种链表结构。``LISTs``就是Redis中存储一个有序字符串队列的类型。

![](images/1.2.2-1.png)

``LISTs``支持的操作类型和绝大多数编程语言的同等数据结构类似。我们可以压入项到队列头或尾使用``LPUSH/RPUSH``. 我们可以从头或尾弹出项使用``LPOP/RPOP``,我们可以获取给定坐标的项使用``LINDEX``，我们可以获取一个范围的项使用``LRANGE``。

## LIST类型可使用的命令

| 命令 | 作用 |
| -- | -- |
| RPUSH | 从list右边压入数据 |
| LRANGE | 获取list中一个范围的值 |
| LINDEX | 获取list中一个给定坐标的值 |
| LPOP | 弹出list最左边的值并返回该值 |

![](images/1.2.2-2.png)


