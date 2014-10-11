# Append-only file持久方案

本质上讲，append-only log files保存了每一次写操作时数据的变化过程。任何人可以从append-only log恢复整个数据库。Redis同样提供这样的功能，开启该功能
