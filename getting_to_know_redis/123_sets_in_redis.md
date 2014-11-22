# Redis的Sets类型

在Redis中，``SETs``类似于``LISTs``，它们都是一字符串队列，不同点是``SETs``使用一个***hash table***存储所有字符串队列(所以没有关联值)。

![](images/1.2.3-1.png)

因为Redis中``SETs``类型是无序的，所以我们不能像``LISTs``那样从末尾push和pop项。我们加入和删除items的值使用``SADD``和``SREM``命令。我们可以通过``SISMEMBER``命令查找是否一个item在这个SET，也可以使用``SMEMBERS``命令获取整个set(对于大型SETs这个操作很慢，请小心操作)。

## SET类型可使用的命令

| 命令 | 作用 |
| ---- | ---- |
| SADD | 增加item到set |
| SMEMBERS | 返回整个set的items |
| SISMEMBER | 检查一个item是否在set中 |
| SREM | 如果item存在，从set中删除该item |

![](images/1.2.3-2.png)
