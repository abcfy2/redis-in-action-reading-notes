# Append-only file持久方案

本质上讲，append-only log files保存了每一次写操作时数据的变化过程。任何人可以从append-only log恢复整个数据库。Redis同样提供这样的功能，开启该功能通过设置配置选项``appendonly yes``，像4.1列表展示的那样。表4.1展示了``appendfsync``选项和他们如何影响文件写同步到硬盘。

## 表4.1 Sync options to use with ``appendfsync``

| 选项 | 发生同步的频率 |
| ---- | -------------- |
| always | 每次写命令都会导致redis将操作写入硬盘。这将导致Redis性能大幅下降 |
| everysec | 每秒一次，明确同步写命令到硬盘 |
| no | 允许操作系统控制同步到磁盘 |


Append-only files很灵活，提供各种选项确保几乎所有级别问题可以处理。但是AOF也有不利的一面，那就是文件容量。
