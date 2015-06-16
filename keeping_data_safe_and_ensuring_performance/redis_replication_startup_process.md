# Redis replication startup process

## Table 4.2 What happens when a slave connects to a master

| Step | Master operations | Slave operations |
| ---- | ----------------- | ---------------- |
| 1    | (等待一个命令) | (重)连接到master; 发起``SYNC``命令 |
| 2    | 启动``BGSAVE``操作; 保存一个包含所有写命令的backlog,在``BGSAVE``之后发送 | 提供旧数据(如果有), 或返回错误的命令(视配置而定) |
| 3    | 完成``BGSAVE``; 开始发送快照到slave; 继续维持一个写命令的backlog | 丢弃所有旧数据(如果有); 开始读取接受到的dump |
| 4    | 结束发送快照到slave; 开始发送写命令的backlog到slave | 完成解析dump; 开始再次正常响应命令 |
| 5    | 完成发送backlog; 开始实时写指令，当它们发生时 | 完成执行backlog中的写命令; 继续执行命令,当它们发生时 |

**在SYNC期间，slave将会刷掉所有自己的数据**

**警告: Redis不支持master-master复制集**
